---
title: "2024 年 10 月から 2025 年 10 月までの Mozc に対する主な変更"
emoji: "🟠"
type: "tech"
topics:
  - "linux"
  - "windows"
  - "keyboard"
  - "ime"
  - "mozc"
published: true
published_at: "2025-10-10 23:00"
---

初稿: 2025-10-10

小松弘幸 ([@komatsuh:bsky](https://bsky.app/profile/komatsuh.bsky.social), [@komatsuh:twitter](https://twitter.com/komatsuh))

2024 年 10 月以降の Mozc に対する主な変更をまとめました。ドキュメントやコミットログ、 Issues に書かれているものをまとめただけで新しい情報はありません。抜けているものがあれば後で追記します。

Mozc の問題の報告や機能の要望等は、GitHub の [Issues](https://github.com/google/mozc/issues) や [Discussions](https://github.com/google/mozc/discussions) へお願いします。

## 関連記事

* [2023 年 10 月以降の Mozc に対する主な変更](https://zenn.dev/komatsuh/articles/komatsuh_mozc_updates_from_2023_10) 
* [2022 年 10 月以降の Mozc に対する主な変更](https://zenn.dev/komatsuh/articles/9b88d84c0590f6) 
* [2021 年 10 月以降の Mozc に対する主な変更](https://zenn.dev/komatsuh/articles/9821ea8be015f0)
* [2020 年以降の Mozc に対する主な変更](https://zenn.dev/komatsuh/articles/d6844edd398402)

## 現在のバージョン

* 2.32.5981
* 3 つめの数字 (5981) はバージョン番号をつけ始めてからの経過日数
* 参考: Google 日本語入力は 2.31.5840.0 (Windows / macOS)
* バージョンを確認する方法: 「ばーじょん」または「Version」で変換する

## 統計情報

### 2024-10-11 - 2025-10-10

* コミット数: 920 (前回: 825)
* クローズした issue の数: 112 ([Issues · google/mozc](https://github.com/google/mozc/issues?q=is%3Aissue+is%3Aclosed++closed%3A2024-10-11..2025-10-10)) (前回: 232)
* マージしたプルリクエスト数: 144 ([Pull requests · google/mozc](https://github.com/google/mozc/pulls?q=is%3Apr+is%3Amerged+updated%3A2024-10-11..2025-10-10+)) (前回: 16)

クローズした数の減少は、変換内容に関する報告を別フォームに移行したことが影響しています。

マージしたプルリクエスト数の大幅な増加は、プルリクエストの受け入れ範囲を全体に拡大したことと、定期的にプルリクエストを送ってくださる方々のおかげです。

### 累計

* コミット数: 5,093 (前回: 4,173)
* クローズした issue の数: 977 (前回: 865)
* マージしたプルリクエスト数: 210 (前回: 67)



## 主要な変更点

* バージョンを 2.32 に更新
* 変換用データと手法の更新
* ARM 用ビルドへの対応 (macOS, Windows)
* macOS の対応バージョンを 12 以降へ変更
* すべての環境でビルドシステムを Bazel へ移行
* NSFW な表現等の報告フォームの追加


## 変換・機能の変更点

### 変換関連

* 変換用データの更新 ([11a5dc3](https://github.com/google/mozc/commit/11a5dc3), etc.)
* 郵便番号データを 2025-08-30 時点のものに更新 ([53e6db7](https://github.com/google/mozc/commit/53e6db7))
* 絵文字データを CLDR 46 (Emoji 16.0) に更新 ([12f8892](https://github.com/google/mozc/commit/12f8892))
* 入力用データの更新 ([#1074](https://github.com/google/mozc/issues/1074), [#1100](https://github.com/google/mozc/issues/1100), [#1165](https://github.com/google/mozc/issues/1165), [#1331](https://github.com/google/mozc/issues/1331), [#1351](https://github.com/google/mozc/issues/1351), [#1360](https://github.com/google/mozc/issues/1360), [#1374](https://github.com/google/mozc/issues/1374), etc.)
* 予測入力の手法の改善 ([9d7332c](https://github.com/google/mozc/commit/9d7332c), [22adec5](https://github.com/google/mozc/commit/22adec5))
* 誤変換報告フォームでの内容に対応 ([#1056](https://github.com/google/mozc/issues/1056))
  + 家系(いえけい), 一意(いちい), 舵輪(だりん), ヒエログリフ(ひえろぐりふ) などを追加しました
* 数字変換での候補の改善 ([#1274](https://github.com/google/mozc/issues/1274))
  + "ゆり" で "百合" にくわえて "100合" が候補になる問題を改善しました
* 同じ読みでより長い候補がある場合に、短い候補が除外される問題の修正 ([1dfd91b](https://github.com/google/mozc/commit/1dfd91b))
  + "さかい" で "堺井" だけが候補となり "堺" が除外される問題を修正しました
* ローマ字入力ルールに "tch" → "っch" を追加
  + "itchou" で "いっちょう" になります
* 予測入力候補に句読点をつけないように変更 ([cb0b430](https://github.com/google/mozc/commit/cb0b430))
  + "お疲れ様です" + "。" と入力したあと、"お疲れ様です。" が予測入力の候補にならないようになります

### 機能関連

* 入力学習用のデータを 62 日間後の削除から、10,000 件以降の削除へ変更 ([12f6d98](https://github.com/google/mozc/commit/12f6d98))
  + 3ヶ月ぶりに入力したい単語を覚えていてくれていない、という問題が改善されます
* 辞書ツールのファイル読込で、 .tsv ファイルをデフォルトで選択可能に

#### Windows 用機能関連

* バージョン更新時に既存の変換エンジン等のプロセスを終了するように変更 ([#1093](https://github.com/google/mozc/issues/1093))
* 入力場所周辺の文字列を変換に活用できる機能に対応するアプリケーションの拡充 ([#1289](https://github.com/google/mozc/issues/1289), [#1293](https://github.com/google/mozc/issues/1293))
  + Chromium 系のアプリケーションや Sakura Editor などのアプリケーションに対応しました
* インストール時に OS のビルド番号のチェックに対応 ([#1329](https://github.com/google/mozc/issues/1329))

### バグ修正

* F10 等での英数字への変換で文字種が循環しない問題の修正 ([#1280](https://github.com/google/mozc/issues/1280))
  + "pya" と入力後の F10 で、"pya" → "PYA" → "Pya" → "pya" と循環しない問題を修正しました
* Linux: 特定の Linux 環境でクラッシュする問題の修正 ([#1318](https://github.com/google/mozc/issues/1318))
  + _SC_GETPW_R_SIZE_MAX に未対応の環境での問題に対応しました
* Linux: 削除した文字が再入力されてしまうアプリケーションがある問題の修正 ([#1174](https://github.com/google/mozc/issues/1174))
  + Anki などでのアプリケーション上の問題に対応しました
* Linux: ibus_config.textproto の設定例の誤りを修正 ([#1237](https://github.com/google/mozc/issues/1237))
* macOS: macOS 26 (Tahoe) でインストール時にクラッシュする問題の修正 ([018d8d9](https://github.com/google/mozc/commit/018d8d9))
* Windows: 特定のアプリケーション (searchhost.exe 等) でフリーズする問題の修正 ([#1077](https://github.com/google/mozc/issues/1077), [#856](https://github.com/google/mozc/issues/856))
  + スタートメニューの検索窓などのアプリケーションに対応しました
* Windows: GUI ツールで表示言語の優先順位が反映されない問題の修正 ([#1110](https://github.com/google/mozc/issues/1110))
  + 日本語にくわえて英語も使用言語に選択している場合の問題に対応しました

#### 2024年10月以降に発生したバグの修正

* 無変換キーによるひらがな・カタカナ変換が動作しない問題の修正 ([#1188](https://github.com/google/mozc/issues/1188))
  + 2.30.5618 で発生
* Linux: テキストを選択すると文字が消去されてしまう問題の修正 ([#1278](https://github.com/google/mozc/issues/1278))
  + 2.31.5851 で発生
* Windows: 候補ウインドウがマウスで選択できない問題の修正 ([#1372](https://github.com/google/mozc/issues/1372))
  + 2.31.5851 で発生


### 開発用機能関連

Mozc をライブラリとして使用する場合に関する変更点です

* Android: 109A キーボード用の KCM ファイルの削除 ([5d3ce6f](https://github.com/google/mozc/commit/5d3ce6f))
* Android: `libmozc.so` を 16KB ページサイズに対応 ([#1364](https://github.com/google/mozc/issues/1364))
* `is_incognito_mode` フィールドを `Request` protocol buffer メッセージに追加
* Protocol Buffer の `Candidates` を `CandidateWindow` に変更


## ビルドの変更点

* Docker でのビルドを終了 (deprecated)
* Bazelisk によるビルドを推奨方法に ([#1272](https://github.com/google/mozc/issues/1272))
  + Bazelisk は Bazel の設定を制御するためのラッパーです
* Python 3.14 でのビルドに対応 ([#1084](https://github.com/google/mozc/issues/1084))
  + Python 3.9 以降でビルド可能です

### Bazel 関連

Bazel はビルドツールのひとつで、Make, CMake 等に相当するツールです。Mozc では Bazel を採用しています。

* Bazel のバージョンを 7 から 8.4.1 へ更新 ([#1118](https://github.com/google/mozc/issues/1118))
* バージョン番号を指定するコマンドラインオプションに対応 ([4f48688](https://github.com/google/mozc/commit/4f48688))
  + 例: `bazel build package --action_env=MOZC_VERSION="2.32.5981.102"`
* WORKSPACE の削除 ([#1115](https://github.com/google/mozc/issues/1115))
  + bzlmod へ移行しました

### GYP 関連

GYP はビルドツールのひとつで、現在は Bazel に変更されています。GYP は今後非対応、関連ファイルの削除を予定しています。

* Windows と macOS でメンテナンスモードへ
  + Linux では既に対応を終了 (deprecated)

### Linux 用ビルド関連

* gcc-14.1.1 でのビルドに対応 ([#927](https://github.com/google/mozc/issues/927))


### macOS 用ビルド関連

* 署名付き .dmg ファイルの作成に対応
  + GitHub Actions での生成物に署名はされていません
* 対応バージョンを macOS 12 以降へ変更
  + これまでは macOS 11 以降での対応でした
* Xcode の必要バージョンを 16.0 (macOS SDK 15.0) 以降に変更


### Windows 用ビルド関連

* ARM64 ビルドへの対応 ([#1130](https://github.com/google/mozc/issues/1130))
* Bazel をデフォルトビルド環境に
* Bazel でのユニットテストに対応
* Bazel で使用するコンパイラーを clang-cl に変更


### 依存ライブラリの更新

* Abseil: 20240722.0 → 20250814.0
* Protocol Buffers: v27.3 → v32.0
* Google Test: v1.15.2 → v1.17.0
* Qt:  6.7.3 → 6.9.1


### GitHub 関連

* GitHub Actions の macOS 環境を macos-14 から macos-15 に更新
* GitHub Actions の Windows 環境を windows-2022 から windows-2025 に更新


## コードの変更点

* C++20 へ対応
* コーディングスタイルの更新 (例 `string &s` → `string& s`)
* Bazel 用のスタイルチェッカーを導入 ([#1089](https://github.com/google/mozc/issues/1089))


### デバッグ関連

* `session_handler_main` ツールに `--test` オプションの追加 ([e1c2bec](https://github.com/google/mozc/commit/e1c2bec))
* 変換処理の内部構造可視化ツール (Lattice Viewer) の追加 ([3c62c59](https://github.com/google/mozc/commit/3c62c59))


### リファクタリング関連

コミットの多くの割合がリファクタリング関連です

* `ConversionRequest` を immutable なオブジェクトに
* `Converter` の実装のリファクタリング
* `SessionConverter` を `EngineConverter` に変更
* `Engine` と `EngineConverter` を pluggable に
* `Converter` と `Rewriter` 間の循環参照を解消
* `Predictor` から `Segment` への依存を削減
* `FRIEND_TEST` から `TestPeer` へ変更
* 不要なコードとデータの削除


## そのほか

### コミット数

コミット数が 5,000 を超えました。以前は上流での変更を一定期間内でまとめて 1 コミットとしていましたので、数週間から数カ月の変更が 1 コミットになっていました。現在は 1:1 の対応になったのでコミット数が大幅に増加した、という背景もあります。

### ビルド番号

バージョン番号の 3 番目の数字はビルド番号で、バージョンをつけ始めてからの経過日数です。この番号が 5000 なら 2023 年 1 月ごろのバージョンだと分かります。現在は 5981 で、そろそろ 6000 番台です。

### 日付のカスタマイズ

日付の表示形式は、ユーザー辞書への登録でカスタマイズできます。次のように登録すると「きょう」などの変換で "2025.01.31" といった形式になります。

| よみ         | 変換                  | 品詞   |
| ----------- | --------------------- | ----- |
| DATE_FORMAT | {YEAR}.{MONTH}.{DATE} | 名詞   |

この機能は 2021 年に実験的機能として実装されました。実験的機能ですので、今後や変更・削除がされることもあります。

* https://github.com/google/mozc/blob/master/docs/configurations.md


### 報告の方法

内容に応じて、報告先を選択してください。使い方の質問に関してはユーザー間での相互的にやり取りをしていただけるととてもうれしいです。

新しく、公共の場では控えたい表現等を報告するためのフォームを作成しました。一般の誤変換レポートと違い、報告内容等は公開されません。

* 使い方の質問: Discussions > [Q&A](https://github.com/google/mozc/discussions/categories/q-a)
* 機能追加の要望: Discussions > [Ideas](https://github.com/google/mozc/discussions/categories/ideas)
* 誤変換や語彙の要望: [Typing issue for Mozc](https://forms.gle/oXgwbqzvSyVHNBSc7)
* 公共の場では控えたい表現の報告: [NSFW issue for Mozc](https://forms.gle/4wwwhkqsXtiDgPcYA)
* 不具合報告: [Issues](https://github.com/google/mozc/issues)


## さいごに

コミットや誤変換の報告等、数多くの方々からのご協力に感謝しています。どうもありがとうございます。前回からの繰り返しですが、Mozc にかぎらず IME に関心を持っていたり、実際に開発に取り組んでいる方がいらっしゃることもとてもうれしく思っています。また、プロジェクトの現在を多くの方々が認識してくださるのはとても心強いことです。これからも応援をよろしくお願いいたします。
