---
title: "GitHub Pages を独自ドメインで運用するための Squarespace での設定方法"
emoji: "📄"
type: "idea"
topics:
  - "GitHub Pages"
  - "Squarespace"
published: true
published_at: "2025-12-28 03:00"
---

初稿: 2025-12-28
小松弘幸 ([@komatsuh:bsky](https://bsky.app/profile/komatsuh.bsky.social), [@komatsuh:twitter](https://twitter.com/komatsuh))

[charcode.dev](http://charcode.dev) というサイトを作りました。

文字列がどのような文字コードで構成されているかの確認や操作をするためのツールです。ソースコードは GitHub で公開しています。

https://github.com/hiroyuki-komatsu/charcode

せっかくなので、GitHub Pages 上で公開しているウェブアプリ用に charcode.dev のドメインを取得して、GitHub Pages を独自ドメインとして運用することにしました。

この記事は、その時に必要だった設定方法のメモです。

## 作業の手順

1. GitHub Pages 上で公開する
2. 独自ドメインを取得する
3. DNS サーバー側の設定をする
4. GitHub Pages 側の設定をする

## 1. GitHub Pages 上で公開する

GitHub レポジトリのルートディレクトリ上にある index.html を公開することにします。シンプルなウェブアプリなので、シンプルな構成にします。

1. Settings > Pages に移動
2. Build and deployment > Source で "Deploy from a branch" を選択
3. Build and deployment > Branch で "master, / (root)" を選択

新規に作成したレポジトリでは master ではなく、main を選択します。

![GitHub Pages の Build and deployment のスクリーンショット](https://github.com/hiroyuki-komatsu/zenn/blob/main/articles/komatsuh_dns_for_github_pages/github_build_and_deployment.png?raw=true)

これで `https:// <ユーザー名> .github.io/ <レポジトリ名> / index.html` という URL で公開されます。

今回の場合は、 https://hiroyuki-komatsu.github.io/charcode/index.html という URL です。


## 2. 独自ドメインを取得する

Squarespace で独自ドメインを取得しました。

https://domains.squarespace.com/ja/


## 3. DNS サーバー側の設定をする

Squarespace の設定を変更して、取得したドメインが GitHub Pages 上のページを指し示すようにします。

1. ドメイン > DNS > カスタムレコードに下記を追加

ホスト | タイプ | データ
----- | ----- | ----
@     | ALIAS | <ユーザー名>.github.io
www   | CNAME | <ユーザー名>.github.io


![Squarespace の DNS 設定のスクリーンショット](https://github.com/hiroyuki-komatsu/zenn/blob/main/articles/komatsuh_dns_for_github_pages/squarespace_dns.png?raw=true)


Web サイトにドメイン転送という設定項目もありますが、今回の目的では必要ありませんでした。

![Squarespace の ドメイン設定のスクリーンショット](https://github.com/hiroyuki-komatsu/zenn/blob/main/articles/komatsuh_dns_for_github_pages/squarespace_domain.png?raw=true)


## 4. GitHub Pages 側の設定をする

1. Settings > Pages に移動
2. Custom domain に独自ドメインを設定 (今回は charcode.dev)
3. Enforce HTTPS にチェックを入れる

![GitHub Pages の Custom domain のスクリーンショット](https://github.com/hiroyuki-komatsu/zenn/blob/main/articles/komatsuh_dns_for_github_pages/github_custom_domain.png?raw=true)

正しく設定できていれば "DNS check successful" というラベルが表示されます。


## まとめ

GitHub Pages を使えば手軽にウェブアプリを公開できます。独自ドメインを使うことで利便性もさらに向上しました。

[charcode.dev](https://charcode.dev) は文字コードの確認や編集に便利ですので、ぜひ使ってみてください。

https://www.youtube.com/watch?v=s3TsS1SaHjQ
