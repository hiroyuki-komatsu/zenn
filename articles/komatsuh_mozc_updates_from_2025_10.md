---
title: "2025 年 10 月から 2026 年 10 月までの Mozc に対する主な変更"
emoji: "🟠"
type: "tech"
topics:
  - "linux"
  - "windows"
  - "keyboard"
  - "ime"
  - "mozc"
published: true
published_at: "2026-10-10 23:30"
---

初稿: 2026-10-10

小松弘幸 ([@komatsuh:bsky](https://bsky.app/profile/komatsuh.bsky.social), [@komatsuh:twitter](https://twitter.com/komatsuh))

2025 年 10 月以降の Mozc に対する主な変更をまとめました。ドキュメントやコミットログ、 Issues に書かれているものをまとめました。

Mozc の問題の報告や機能の要望等は、GitHub の [Issues](https://github.com/google/mozc/issues) や [Discussions](https://github.com/google/mozc/discussions) へお願いしま
す。

## 関連記事

* [2024 年 10 月から 2025 年 10 月までの Mozc に対する主な変更](https://zenn.dev/komatsuh/articles/komatsuh_mozc_updates_from_2024_10) 
* [2023 年 10 月以降の Mozc に対する主な変更](https://zenn.dev/komatsuh/articles/komatsuh_mozc_updates_from_2023_10) 
* [2022 年 10 月以降の Mozc に対する主な変更](https://zenn.dev/komatsuh/articles/9b88d84c0590f6) 
* [2021 年 10 月以降の Mozc に対する主な変更](https://zenn.dev/komatsuh/articles/9821ea8be015f0)
* [2020 年以降の Mozc に対する主な変更](https://zenn.dev/komatsuh/articles/d6844edd398402)

## 現在のバージョン

* 3.34.6345
* 3 つめの数字 (6345) はバージョン番号をつけ始めてからの経過日数
* 参考: Google 日本語入力は 3.34.6260.0 (Windows / macOS)
* バージョンを確認する方法: 「ばーじょん」または「Version」で変換する

## 統計情報

### 2025-10-11 - 2026-10-10

* コミット数: 620 (前回: 920)
* クローズした issue の数: 58 ([Issues · google/mozc](https://github.com/google/mozc/issues?q=is%3Aissue+is%3Aclosed++closed%3A2025-10-11..2026-10-10)) (前回: 112)
* マージしたプルリクエスト数: 105 ([Pull requests · google/mozc](https://github.com/google/mozc/pulls?q=is%3Apr+is%3Amerged+updated%3A2025-10-11..2026-10-10+)) (前回: 144)

クローズした数の減少は、明確なバグ以外の内容は Discussions を積極的に活用するようにしたことも影響しています。

### 累計

* コミット数: 5,715  (前回: 5,093)
* クローズした issue の数: 1,035 (前回: 977)
* マージしたプルリクエスト数: 315 (前回: 210)

## 主な変更点

* メジャーバージョンを 2 から 3 に更新
* 辞書データの更新
* 変換精度の改善
* ユーザー辞書のコスト計算を登録数に応じるように変更
* Linux: 候補ウインドウをダークテーマに対応
* macOS: インストール時にログアウトするように変更
* Windows: DPIが異なる複数ディスプレイ上で、候補ウインドウの大きさや位置が異なる問題の改善
* 「語彙集合および変換結果に関する方針」の策定
* コード: コーディングスタイルの変更
* コード: バージョン表記ファイルの移動
* ビルド: GYP ビルドの完全削除
* ビルド: Google Benchmark への対応
* ビルド: Python test への対応

### メジャーバージョンを 2 から 3 に更新

Windows / macOS での ARM 対応、ビルドシステムの GYP から Bazel への完全移行、コードベースの改修等を踏まえて、メジャーバージョンを 2 から 3 へ更新しました。

前回のメジャーバージョンの 2 への更新は [2014-11-09](https://github.com/google/mozc/commit/b729086960878ccca5f2229a4fc9701e84093583) ですので、12 年ぶりの更新です。

### 辞書データの更新

定期的な辞書データの更新のほか、郵便番号データ、絵文字データ、報告フォームなどに寄せられた新語や未登録語の追加などを行いました。

### 変換精度の改善

記号類などの優先順位調整、全角半角の学習方法の調整などを行いました。

### ユーザー辞書のコスト計算を登録数に応じるように変更

ユーザー辞書に登録した単語の優先順位を、登録した単語数に応じて変化するように調整しました。10 程度の単語登録の場合は、これまでよりもより優先順位が高く提示されます。150 登録ぐらいでこれまでとほぼ同様の優先順位になります。

### Linux: 候補ウインドウをダークテーマに対応

システムのテーマ設定に応じて、候補ウインドウがダークテーマで表示されます。 ([#1582](https://github.com/google/mozc/issues/1582))

### macOS: インストール時にログアウトするように変更

インストーラーの終了時にログアウトするように変更しました。現在の macOS ではインプットメソッドを有効にするためにはログアウト以外に安定した方法がないため、インストール直後の分かりにくさを防ぐためです。

### Windows: DPIが異なる複数ディスプレイ上で、候補ウインドウの大きさや位置が異なる問題の改善

Windows 環境で、複数ディスプレイを異なる DPI 設定で使用すると、候補ウインドウの大きさがウインドウによって異なる問題がありました。これを改善しました。

### 「語彙集合および変換結果に関する方針」の策定

Mozc プロジェクトにおいての「[登録単語や変換精度に関する方針](https://github.com/google/mozc/blob/master/VOCABULARY_POLICY.md)」を策定しました。持続可能なプロジェクト運営のためです。

### コード: コーディングスタイルの変更

Google の C++ コーディングスタイルの変更に合わせて、コーディングスタイルを変更しました。大きな変更としては、ポインタ `*` やリファレンス `&` の記号と空白の位置が変わりました。

新: `std::string& value`

旧: `std::string &value`

### コード: バージョン表記ファイルの移動

現在のバージョンを記載しているファイルの場所の名前を変更しました。

新: `src/version.bzl`

旧: `src/data/version/mozc_version_template.bzl` 

### ビルド: GYP ビルドの完全削除

Windows / macOS ビルド用に残していた GYP ビルド用のファイル群を完全に削除しました。([#1438](https://github.com/google/mozc/issues/1438))

GYP は現在はほぼ更新されておらず、最新のビルド環境で使用するには工夫が必要になるビルドツールでした。今後は Bazel ビルドのみの対応になるため、リファクタリングやコードの簡略化などがより積極的に行われます。

### ビルド: Google Benchmark への対応

Google Benchmark の OSS 化に対応しました。速度が重視されるコンポーネントに対して計測に基づいた改善ができるようになります。

### ビルド: Python test への対応

Python のユニットテストの OSS 化に対応しました。ビルドツールなどの Python コードに対してもテストが実施されます。

## 変換・機能の変更点

### データ更新関連

* 辞書データの更新
* 報告フォームなどからのフィードバックに基づく更新
* 郵便番号データの更新
* 記号データの追加
* 絵文字データの更新 (Emoji 17.0  へ対応)

### 変換精度関連

* 記号候補の優先順位を引き下げ
* 絵文字候補を顔文字候補よりも優先して表示
* ユーザー辞書の優先順位を登録数に応じて変更
* 助詞を省略した文での変換精度を改善 (さかなくう → 魚食う) (デフォルトでは無効)
* 入力履歴の保存方法を 62 日間から、データサイズに応じた保存に変更 ([12f6d98](https://github.com/google/mozc/commit/12f6d98493d63c0992c2d179b3a433df565e283e))
* 数字入力の後は助数詞 (「個」「本」など) を優先 ([6621478](https://github.com/google/mozc/commit/662147864d8a902f49bee7aa7a02d377c0bbd58d))
 
### 変換機能

* 日時変換のカスタマイズで `{HOUR}` と `{MINUTE}` フォーマットに対応 ([56e9a20](https://github.com/google/mozc/commit/56e9a20), [5614529](https://github.com/google/mozc/commit/5614529))
* 日時変換のカスタマイズで複数項目に対応 ([396972c](https://github.com/google/mozc/commit/396972ca8f221b6bc5e587e9689f030a70826c97))
* 計算機能で `Sin` `Log` などに対応 (`Log(100)=` → `2`)  ([27710f2](https://github.com/google/mozc/commit/27710f2))

### UI 関連

* 変換履歴と予測履歴の削除操作の統合 ([14882c3](https://github.com/google/mozc/commit/14882c3))
* Linux: 候補ウインドウがダークテーマに対応
* Linux: 候補ウインドウが候補数と候補位置を示すインジケーターに対応 ([#1565](https://github.com/google/mozc/issues/1565))
* Linux: 候補ウインドウがフッターラベルに対応 ([#1580](https://github.com/google/mozc/issues/1580))
* Linux: 候補ウインドウのスタイルやレイアウトの見た目を macOS / Windows と統一 ([#1549](https://github.com/google/mozc/issues/1549), [#1551](https://github.com/google/mozc/issues/1551), [#1586](https://github.com/google/mozc/issues/1586))
* Windows: DPIが異なる複数ディスプレイ上で、候補ウインドウの大きさや位置が異なる問題の改善 ([#1481](https://github.com/google/mozc/issues/1481))

 ### インストール関連

 * macOS: インストール時にログアウトするように変更 ([e8c987a](https://github.com/google/mozc/commit/e8c987a))
 * Windows: 同一バージョンや CPU 不整合時のインストールエラー時のメッセージを改善 ([#1410](https://github.com/google/mozc/issues/1410), [#1585](https://github.com/google/mozc/issues/1585))

## バグ修正

* ATOK 形式のユーザー辞書の読み込みに失敗する問題を修正 ([9cf9ede](https://github.com/google/mozc/commit/9cf9ede))
* Android: 先頭に空白を含む候補の入力履歴を削除できない問題を修正 ([a8f245e](https://github.com/google/mozc/commit/a8f245e))
* Emacs: tab-line 有効時に候補オーバーレイが崩れる問題を修正 ([#1507](https://github.com/google/mozc/issues/1507), [0c8acf4](https://github.com/google/mozc/commit/0c8acf4))
* Emacs: mozc.el における候補ウィンドウ表示の後方互換性を修正 ([#1427](https://github.com/google/mozc/issues/1427), [891e324](https://github.com/google/mozc/commit/891e324))
* Linux: _SC_GETPW_R_SIZE_MAX に未対応の Linux 環境でクラッシュする問題を修正 ([#1318](https://github.com/google/mozc/issues/1318))
* macOS: macOS 26 (Tahoe) でインストーラーが落ちる問題を修正 ([018d8d9](https://github.com/google/mozc/commit/018d8d9ff95019569d9496ec5ab9d1f0b3107c72))
* macOS: 辞書ツールで動作が停止する問題を修正 ([#1545](https://github.com/google/mozc/issues/1545))
* macOS: アプリケーションの起動に失敗する問題を修正 [34c3187](https://github.com/google/mozc/commit/34c3187)
* macOS: フッター境界線の色を赤から灰色に修正 [0b71173](https://github.com/google/mozc/commit/0b71173)
* macOS: GUI ツールが起動できない問題の修正 ([#1412](https://github.com/google/mozc/issues/1412))
* Windows: Excel 上で再変換できない問題を修正 ([#1385](https://github.com/google/mozc/issues/1385))
* Windows: 特定のアプリケーションで入力中文字列がちらつく問題を修正 ([#1389](https://github.com/google/mozc/issues/1389))
* Windows: 修飾キー単体押しイベントが取得できなくなっていた問題を修正 ([#1415](https://github.com/google/mozc/issues/1415))
* Windows: 候補ウィンドウ上でマウスクリックできない問題を修正 ([#1372](https://github.com/google/mozc/issues/1372))

## コード関連

* コーディングスタイルの変更 (`string &s` → `string& s`)
* バージョン表記ファイルの移動 (`src/mozc/version.bzl`)
* 全角半角の入力履歴の保存先を cform.db から UserHistoryStorage へ移行 [b7277bb](https://github.com/google/mozc/commit/b7277bb)
* Android: ユーザー辞書の保存方法をサーバーを介さない方法に変更 [[2fc02b0](https://github.com/google/mozc/commit/2fc02b0), [7262b53](https://github.com/google/mozc/commit/7262b53), [ff99671](https://github.com/google/mozc/commit/ff99671), [f91f569](https://github.com/google/mozc/commit/f91f569), [1ab7fc8](https://github.com/google/mozc/commit/1ab7fc8), [80eadd0](https://github.com/google/mozc/commit/80eadd0), [c60e7d4](https://github.com/google/mozc/commit/c60e7d4)]
* 品詞名と品詞IDの紐づけをランタイムに行う PosPatternMatcher を実装 [[cb11f9c](https://github.com/google/mozc/commit/cb11f9c), [b5ac73a](https://github.com/google/mozc/commit/b5ac73a), [88da9b4](https://github.com/google/mozc/commit/88da9b4)]
* SuggestionFilter / ResultFilter で <NWP> 接頭辞エントリをサポート [d3f6b7c](https://github.com/google/mozc/commit/d3f6b7c)
* ビット演算による高速化 ([#1568](https://github.com/google/mozc/issues/1568), [#1569](https://github.com/google/mozc/issues/1569), [13fd62b](https://github.com/google/mozc/commit/13fd62b))
* Singleton クラスの削除 ([#1461](https://github.com/google/mozc/issues/1461), [#1463](https://github.com/google/mozc/issues/1463), [#1464](https://github.com/google/mozc/issues/1464), [#1465](https://github.com/google/mozc/issues/1465), [#1475](https://github.com/google/mozc/issues/1475), [#1477](https://github.com/google/mozc/issues/1477), [#1478](https://github.com/google/mozc/issues/1478), [#1479](https://github.com/google/mozc/issues/1479), [#1480](https://github.com/google/mozc/issues/1480), [#1490](https://github.com/google/mozc/issues/1490), [#1491](https://github.com/google/mozc/issues/1491), [#1497](https://github.com/google/mozc/issues/1497), [#1498](https://github.com/google/mozc/issues/1498), [#1499](https://github.com/google/mozc/issues/1499), [#1502](https://github.com/google/mozc/issues/1502), [#1509](https://github.com/google/mozc/issues/1509), [#1510](https://github.com/google/mozc/issues/1510), [#1513](https://github.com/google/mozc/issues/1513), [#1514](https://github.com/google/mozc/issues/1514), [#1515](https://github.com/google/mozc/issues/1515), [#1523](https://github.com/google/mozc/issues/1523))
* 候補ウインドウの描画スタイルの `renderer_style.textproto` による管理 [[751df90](https://github.com/google/mozc/commit/751df90), [be6dd36](https://github.com/google/mozc/commit/be6dd36), [67cede2](https://github.com/google/mozc/commit/67cede2), [afbf1d0](https://github.com/google/mozc/commit/afbf1d0)]
* ConfigDialog のレイアウトのリファクタリング [[4638ce6](https://github.com/google/mozc/commit/4638ce6), [c79a760](https://github.com/google/mozc/commit/c79a760), [895652c](https://github.com/google/mozc/commit/895652c), [3c327d8](https://github.com/google/mozc/commit/3c327d8)]
* ImmutableConverter および DictionaryInterface の ConversionRequest への依存の削除 [[2ee4da3](https://github.com/google/mozc/commit/2ee4da3), [6ba80c7](https://github.com/google/mozc/commit/6ba80c7), [b30921c](https://github.com/google/mozc/commit/b30921c)]
* CalculatorRewriter から Lemon パーサーの削除 [[cb95326](https://github.com/google/mozc/commit/cb95326), [e96c1ba](https://github.com/google/mozc/commit/e96c1ba)]
* Breakpad 関連のコードの削除 ([1078e63](https://github.com/google/mozc/commit/1078e63))
* zstring_view の削除 ([61068fe](https://github.com/google/mozc/commit/61068fe))
* RealtimeDecoder の所有権を predictor 側に移動 ([b465e89](https://github.com/google/mozc/commit/b465e89))
* FreeList を Arena として再実装 ([730ad5a](https://github.com/google/mozc/commit/730ad5a))
* RequestNWP コマンドを追加 ([8f1f0eb](https://github.com/google/mozc/commit/8f1f0ebbbc2899def9420e15edbde44b729b7d75))
* INPUT_MODE_* を COMPOSITION_MODE_* に変更 (例: `INPUT_MODE_HIRAGANA` → `COMPOSITION_MODE_HIRAGANA`)
* Enum ラベルの `KUTEN` および `TOUTEN` の入れ替わりの修正 ([0429d96](https://github.com/google/mozc/commit/0429d9659f6c36abc40a1ca82bc6e5c01f938503))

 ## ビルド関連

* 必要なデフォルトビルドオプションの簡素化 (`bazelisk build package`)
* Bazel 9.0.2 へ更新
* GYP ビルドの完全削除
* Git サブモジュールの削除
* Google Benchmark への対応
* Python test への対応
* Android: `android_util` を独立したビルドターゲットに分離 ([060b96e](https://github.com/google/mozc/commit/060b96e))
* Android: `libmozc.so` を 16KB ページサイズに対応 ([#1364](https://github.com/google/mozc/issues/1364))
* macOS: コード署名付きの .dmg ファイル生成に対応
* macOS: 対応バージョンを macOS 11 から macOS 12 へ変更
* Windows: Visual Studio 2026 によるビルドに対応 ([#1495](https://github.com/google/mozc/issues/1495))
* Windows: ユニバーサル MSI インストーラービルドのサポート ([#1430](https://github.com/google/mozc/issues/1430))

 ## そのほか

### スター数

GitHub のスターの数が 3,000 を超えました。ありがとうございます。

### 報告の方法

内容に応じて報告先を選択してください。使い方の質問に関してはユーザー間での相互的にやり取りをしていただけるととてもうれしいです。

* 使い方の質問: Discussions > [Q&A](https://github.com/google/mozc/discussions/categories/q-a)
* 機能追加の要望: Discussions > [Ideas](https://github.com/google/mozc/discussions/categories/ideas)
* 誤変換や語彙の要望: [Typing issue for Mozc](https://forms.gle/oXgwbqzvSyVHNBSc7)
* 公共の場では控えたい表現の報告: [NSFW issue for Mozc](https://forms.gle/4wwwhkqsXtiDgPcYA)
* 不具合報告: [Issues](https://github.com/google/mozc/issues)

また「[登録単語や変換精度に関する方針](https://github.com/google/mozc/blob/master/VOCABULARY_POLICY.md)」も参照してください。

### さいごに

LLM (生成AI) の発展と普及によって、IME (日本語入力ソフトウェア) の作成も非常に手軽になったと実感しています。個人的な機能や変換傾向の実現は LLM を使えば数日中に動くものができてしまいます。多くの方が IME の開発に興味を持って乗り出してくれていることは、個人的にも大変うれしいことです。

このような現在の環境においての Mozc の役割は、Mozc をそのまま使うだけではなく、Mozc を自作実装の基盤にしたり日本語入力ソフトウェアの参考実装としての側面もあるのではと考えています。その場合においても、Mozc の変換精度の向上や、使いやすさの改善などは、今後も引き続き重要であると考えています。

プロジェクトの健全な発展と継続には、みなさまからの応援に支えられています。これからもどうぞよろしくお願いいたします。
