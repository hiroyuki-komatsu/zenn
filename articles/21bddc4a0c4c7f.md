---
title: "GitHub Actions で Bazel の Android NDK ビルド環境を設定する"
emoji: "📗"
type: "tech"
topics:
  - "android"
  - "githubactions"
  - "ndk"
  - "bazel"
published: true
published_at: "2022-08-21 21:19"
---

初稿： 2022-08-21
小松弘幸 ([@komatsuh](https://twitter.com/komatsuh))

# 記事の内容

GitHub Actions で、Bazel による Android NDK ビルド用の環境を設定する方法を紹介します。

Bazel での Android NDK ビルドの設定はすでにできている前提で、GitHub Actions でも同様のビルドをする方法がこの記事の主題です。

:::message
この記事は、2022 年 8 月時点での内容です。バージョン番号等に依存する内容ですので、情報が古くなることが予想されます。
:::

# 結論

* Android NDK r21 を明示的にインストールする
* ANDROID_NDK_HOME を Android NDK r21 へ設定する
* 実例: [mozc/blob/master/.github/workflows/android.yaml](https://github.com/google/mozc/blob/master/.github/workflows/android.yaml)

```yaml
      - name: setup
        run: |
          # Android NDK
          # Bazel has not yet supported Android NDK 22 or later.
          # https://github.com/bazelbuild/bazel/issues/12889
          # Install Android NDK 21.
          # https://github.com/actions/runner-images/issues/5930
          ANDROID_SDK_ROOT=/usr/local/lib/android/sdk
          SDKMANAGER=${ANDROID_SDK_ROOT}/cmdline-tools/latest/bin/sdkmanager
          echo "y" | $SDKMANAGER "ndk;21.4.7075529"
          echo "ANDROID_NDK_HOME=$ANDROID_SDK_ROOT/ndk/21.4.7075529" >> $GITHUB_ENV
```

# 説明

GitHub Actions での Android NDK のデフォルトバージョンが r21 から r25 に更新されました。

* [[all OSs] Android NDK 21 will be replaced in favor of 25 on August, 1st · Issue #5930 · actions/runner-images](https://github.com/actions/runner-images/issues/5930)

しかし残念ながら Bazel の Android NDK ビルドは、NDK r22 以降をまだ対応していません。

* [Support for Android NDK r22, r23, r24, r25 · Issue #12889 · bazelbuild/bazel](https://github.com/bazelbuild/bazel/issues/12889)

そこで、GitHub Actions の実行環境に NDK r21 を入れる必要があります。

また GitHub Actions の実行環境では、ANDROID_NDK_HOME のデフォルト値は NDK バージョンの固有のディレクトリが設定されています。具体的には `/usr/local/lib/android/sdk/ndk/25.0.8775105` です。この値もあわせて r21 に対応した `21.4.7075529` にします。

ディレクトリ名に使っているバージョン番号は、GitHub Actions のランタイム情報や Android NDK のダウンロードサイトから確認できます。

* [runner-images/Ubuntu2004-Readme.md at main · actions/runner-images](https://github.com/actions/runner-images/blob/main/images/linux/Ubuntu2004-Readme.md)
* [Unsupported Downloads · android/ndk Wiki](https://github.com/android/ndk/wiki/Unsupported-Downloads)

# さいごに

この記事は Bazel が Android NDK r25 に対応したら必要なくなります。
早く必要なくなるといいなあと願っています。
* [Support for Android NDK r22, r23, r24, r25 · Issue #12889 · bazelbuild/bazel](https://github.com/bazelbuild/bazel/issues/12889)

それまではニッチな内容ですがどなたかのお役に立てばうれしいです。