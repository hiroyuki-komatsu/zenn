---
title: "Bazel 7 での jni.h: No such file というエラーへの対応 (bazelisk --bisect)"
emoji: "💚"
type: "tech"
topics:
  - "Bazel"
  - "Android"
  - "C++"
published: true
published_at: "2023-12-24 13:00"
---

初稿: 2023-12-24
小松弘幸 ([@komatsuh:twitter](https://twitter.com/komatsuh), [@komatsuh:bsky](https://bsky.app/profile/komatsuh.bsky.social))

## 概要

Bazel のバージョンが 7 にあがったら、「jni.h が存在しない」というエラーがでました。結論としては Bazel 7 以降では `--fat_apk_cpu` オプションを使うには `--incompatible_enable_android_toolchain_resolution=false` の追加が必要でした。

原因の発見と解決に至るまでを記事にしました。Bazel をすでに利用している人向けの内容です。

## Bazel 7 で jni.h: No such file or directory というエラーになる

GitHub Actions での CI で、Bazel による Android ビルドに失敗するようになりました。次のようなエラーが起きていました。

```
java/com/app/jni.cc:15:10: fatal error: jni.h: No such file or directory
   15 | #include <jni.h>
      |          ^~~~~~~
compilation terminated.
```

コミットをロールバックしてもエラーになるため、GitHub Actions の環境が更新されたことが原因だと考え確認しました。

経験上 Bazel のバージョンが更新されるとこのようなエラーが起きることが多いので、Bazel 関連の変更を確認します。

[GitHub Actions の環境](https://github.com/actions/runner-images/blob/main/images/ubuntu/Ubuntu2204-Readme.md)の更新履歴を確認して、Bazel のバージョンが 7.0.0 へ更新されていることを確認しました。

https://github.com/actions/runner-images/commit/28be760bba37289f8f7361bbb84c3d0527e804c3

![GitHub Actions 環境の diff](https://github.com/hiroyuki-komatsu/zenn/blob/main/articles/komatsuh_bazel7_jni_error_gadiff.png?raw=true)


## Bazelisk による Bazel のバージョン指定

Bazelisk は複数のバージョンの Bazel を使い分けるためのツールです。

https://github.com/bazelbuild/bazelisk

Bazel のバージョン 7.0.0 を指定してビルドする場合は次のようにします。

```shell
USE_BAZEL_VERSION=7.0.0 bazelisk build (target_name)
```

手元の環境でも Bazel 7.0.0 では同様のエラーになり、Bazel 6.0.0 ではビルドに成功することが確認できました。

## Bazelisk --bisect による原因の特定

Bazel のバージョンによる問題であることは分かりましたので、実際の原因や解決方法を探ります。Bazel へのどの変更で問題が起きたのかを `Bazel --bisect` によって調べます。

バイセクト (bisect) とは変更履歴の中から実際に問題が起きた変更を調べるための手法で、二分探索によって確認していきます。git にも同様の手法があります。

https://git-scm.com/docs/git-bisect

Bazelisk でのバイセクトは次のようにします。バージョン 6.0.0 から 7.0.0 の間でビルドの成否が変わる場所を見つけられます。

```shell
bazelisk --bisect=6.0.0..7.0.0 build (target_name)
```

あとは結果を確認すれば完了のはずでしたが、バイセクトが途中で止まってしまいました。

```
--- Succeeded at 78db9ae9a545a9586dbb02d7831f5302594e01cb
--- Testing with Bazel built at 05bea52ed3159aa5d15d967f5f56fc084a2b6c73, 6 commits remaining...

...

--- Testing with Bazel built at f7946d0107dd75b2f45bcc79b91c016d075a756d, 3 commits remaining...

2023/12/20 11:23:45 Using unreleased version at commit f7946d0107dd75b2f45bcc79b91c016d075a756d
2023/12/20 11:23:45 Downloading https://storage.googleapis.com/bazel-builds/artifacts/centos7/f7946d0107dd75b2f45bcc79b91c016d075a756d/bazel...
2023/12/20 11:23:45 could not run Bazel: could not download Bazel: failed to download bazel: failed to download bazel: HTTP GET https://storage.googleapis.com/bazel-builds/artifacts/centos7/f7946d0107dd75b2f45bcc79b91c016d075a756d/bazel failed with error 404
```

理由は調べていませんが、途中のコミットが取得できないようです。それでも 6 コミットまでは絞り込めました。ここからは、判明しているコミットを指定してみます。

```shell
bazelisk --bisect=78db9ae9a545a9586dbb02d7831f5302594e01cb..05bea52ed3159aa5d15d967f5f56fc084a2b6c73 build (target_name)
```

今回は期待通り、原因の変更を確認できました。もし同じエラーが起きたとしても、6 コミットであれば全部確認すればよいでしょう。

```
--- Failed at 05bea52ed3159aa5d15d967f5f56fc084a2b6c73

--- Bisect Result
first bad commit is https://github.com/bazelbuild/bazel/commit/05bea52ed3159aa5d15d967f5f56fc084a2b6c73
```

## 原因と解決方法

ビルドエラーの原因は次の変更であることが判明しました。

https://github.com/bazelbuild/bazel/commit/05bea52ed3159aa5d15d967f5f56fc084a2b6c73

> RELNOTES: Enable Platforms and Toolchains for Android. Android projects will need to stop passing the legacy flag `--fat_apk_cpu`, and instead use `--android_platforms` using platforms defined with the `@platforms//os:android` constraint. The https://github.com/bazelbuild/rules_android repository defines four standard Android platforms for projects that use those rules, `@rules_android//:armeabi-v7a`, `@rules_android//:arm64-v8a`, `@rules_android//:x86`, `@rules_android//:x86_64`.

![diff of 05bea5](https://github.com/hiroyuki-komatsu/zenn/blob/main/articles/komatsuh_bazel7_jni_error_commitdiff.png?raw=true)

変更内容にある通り `incompatible_enable_android_toolchain_resolution` オプションのデフォルト値が `true` に変更されたようです。そのために `--fat_apk_cpu` オプションを指定しているビルドではエラーになるようです。

とりあえずの解決方法としては、`incompatible_enable_android_toolchain_resolution` を `false` に戻せばよいようです。

```shell
USE_BAZEL_VERSION=7.0.0 bazelisk build (target_name) --incompatible_enable_android_toolchain_resolution=false
```

上記コマンドでは期待通りビルドできることが確認できました。(自分の環境では `--fat_apk_cpu` オプションは `.bazelrc` にデフォルトオプションとして記載されています)

なおコミットメッセージにもあるとおり、将来的には `--fat_apk_cpu` の代わりに `--android_platforms` の使用が推奨されています。

## まとめ

* GitHub Actions で `jni.h: No such file or directory` というエラーが起きました。
* GitHub Actions のビルド環境が Bazel が更新されたことを確認しました。
* Bazelisk --bisect によって、原因となる変更を特定しました。
* 変更履歴から Bazel 7 で `--fat_apk_cpu` を使うには `--incompatible_enable_android_toolchain_resolution=false` が必要だと分かりました。

### 具体例

エラー時の GitHub Actions
https://github.com/google/mozc/actions/runs/7243136493

修正後の GitHub Actions
https://github.com/google/mozc/actions/runs/7279025829

修正コミット
https://github.com/google/mozc/commit/68fea8a05c189a7ff166b36b07eac434569f4cd2
