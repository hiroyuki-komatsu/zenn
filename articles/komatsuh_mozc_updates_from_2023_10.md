---
title: "2023 年10月以降の Mozc に対する主な変更"
emoji: "🟠"
type: "tech"
topics:
  - "linux"
  - "windows"
  - "keyboard"
  - "ime"
  - "mozc"
published: true
published_at: "2024-10-10 23:00"
---

初稿: 2024-10-10

小松弘幸 ([@komatsuh:bsky](https://bsky.app/profile/komatsuh.bsky.social), [@komatsuh:twitter](https://twitter.com/komatsuh))

2023 年 10 月以降の Mozc に対する主な変更をまとめました。ドキュメントやコミットログ、 Issues に書かれているものをまとめただけで新しい情報はありません。抜けているものがあれば後で追記します。

Mozc の問題の報告や機能の要望等は、GitHub の [Issues](https://github.com/google/mozc/issues) や [Discussions](https://github.com/google/mozc/discussions) へお願いします。

## 関連記事

* [2025 年 10 月から 2026 年 10 月までの Mozc に対する主な変更](https://zenn.dev/komatsuh/articles/komatsuh_mozc_updates_from_2025_10) 
* [2024 年 10 月から 2025 年 10 月までの Mozc に対する主な変更](https://zenn.dev/komatsuh/articles/komatsuh_mozc_updates_from_2024_10) 
* [2023 年 10 月以降の Mozc に対する主な変更](https://zenn.dev/komatsuh/articles/komatsuh_mozc_updates_from_2023_10) : この記事
* [2022 年 10 月以降の Mozc に対する主な変更](https://zenn.dev/komatsuh/articles/9b88d84c0590f6) 
* [2021 年 10 月以降の Mozc に対する主な変更](https://zenn.dev/komatsuh/articles/9821ea8be015f0)
* [2020 年以降の Mozc に対する主な変更](https://zenn.dev/komatsuh/articles/d6844edd398402)


## 現在のバージョン

* 2.30.5618
* 3 つめの数字 (5618) はバージョン番号をつけ始めてからの経過日数
* 参考: Google 日本語入力は 2.29.5370 (Windows), 2.30.5590 (macOS)
* バージョンを確認する方法: 「ばーじょん」または「Version」で変換する


## 統計情報

### 2023-10-11 - 2024-10-10

* コミット数: 825
* クローズした issue の数: 232 ([Issues · google/mozc](https://github.com/google/mozc/issues?q=is%3Aissue+is%3Aclosed++closed%3A2023-10-11..2024-10-10))
* マージしたプルリクエスト数: 16 ([Pull requests · google/mozc](https://github.com/google/mozc/pulls?q=is%3Apr+is%3Amerged+updated%3A2023-10-11..2024-10-10+))

### 累計

* コミット数: 4,173
* クローズした issue の数: 865
* マージしたプルリクエスト数: 67


## 主要な変更点

* バージョンを 2.30 に更新
* プルリクエストの受け入れ範囲を全体に拡大
* 誤変換の報告方法を簡略化
* 変換用データの更新と変換機能の調整
* Windows の Bazel でのビルドへの対応 ([#948](https://github.com/google/mozc/issues/948))
* WORKSPACE から Bzlmod への移行 ([#1002](https://github.com/google/mozc/issues/1002))
* GYP によるビルドを非推奨に

## プルリクエストの受け入れ範囲を全体に拡大

これまではプルリクエストを受け付けは特定のディレクトリに対してのみでしたが、その制限を撤廃しました。


## 誤変換の報告方法を簡略化

誤変換のレポート方法を GitHub Issues から Google Form へ移行しました。送る側も受ける側もお互いに便利になることを期待しています。

* [報告フォーム](https://docs.google.com/forms/d/e/1FAIpQLSfQ7UVkk9HxVQOQ1F2O_E3L5psvkkk-zPKJxJCbyAg9dZk8Yw/viewform)
* [報告一覧](https://docs.google.com/spreadsheets/d/1AAK8wiTfIhj339Rb98lIRwgGfHndVz-jFXFNXZNQyeo/pubhtml?gid=649291758&single=true)
* [Please use the Google form for reporting typing issues · Issue #1056 · google/mozc](https://github.com/google/mozc/issues/1056)


これまでの誤変換のレポートに基づいた改善の例

* [b0b37db](https://github.com/google/mozc/commit/b0b37db046cb8a2f075a463d0c71926f744cfcb6) / [9c53503](https://github.com/google/mozc/commit/9c53503e501a045e9f7a8566d59481f593f7dde8) / [ad8a2be](https://github.com/google/mozc/commit/ad8a2be763376675df256fef3cb68d41ede2e566) / [456284e](https://github.com/google/mozc/commit/456284ec02696ed6444a8b09610f4746a2714100) / [f518d3d](https://github.com/google/mozc/commit/f518d3d6be4ebc938a1db0df914d54c34ba86213) / [d0d1bc8](https://github.com/google/mozc/commit/d0d1bc86aaaa2eae14ea9113b2f8261ec40ca24a) / [2ea9504](https://github.com/google/mozc/commit/2ea95041d8ac33ceb6523a008b9c57be56819415) / [d6a55d2](https://github.com/google/mozc/commit/d6a55d2b35440dae4c26baf420bb02cedaf2ab37)


## 変換用データの更新と変換機能の調整

* 郵便番号データの更新 ([#1063](https://github.com/google/mozc/issues/1063))
* 辞書データの更新 ([#1068](https://github.com/google/mozc/issues/1068), [#1069](https://github.com/google/mozc/issues/1069), [#928](https://github.com/google/mozc/issues/928), [6af6a25](https://github.com/google/mozc/commit/6af6a25e580ec46c438677e50303d137db230bd1), [4f03239](https://github.com/google/mozc/commit/4f03239c829c2a986f077b0d21b0a7702aabc508))
* 「もしかして」データの更新 ([3a665b1](https://github.com/google/mozc/commit/3a665b1efdc975bc6d6316b80497bb411b6508fb))
* 記号データの更新 ([#933](https://github.com/google/mozc/issues/933), [#860](https://github.com/google/mozc/issues/860))
* 絵文字データを 15.1 へ更新 ([68c3985](https://github.com/google/mozc/commit/68c3985583aa341673e85ee4ea8267590a665f57))
* 変換手法の調整 (例: 後に vs あと2).


## 機能関連の変更

* 元号と西暦の変換機能の改善 (れいわ６ねん→2024年, 2024ねん → 令和6年) ([6ceada3](https://github.com/google/mozc/commit/6ceada3f2d95eccc96b731d0ae2dc59b73323b8a))
* 「なう」から日時への変換を追加 ("なう" → "2024/12/31 23:59")
* Gboard から保存したユーザー辞書の読み込みに対応
* 「Mozc について」のダイアログ GUI をダークモードに対応 ([#897](https://github.com/google/mozc/issues/897))


## バグ修正

* ユーザー辞書の保存時にクラッシュする問題を修正 ([42cbb3f](https://github.com/google/mozc/commit/42cbb3f93378f2ca25ac99371abb22404f129250))
* デバッグビルド時に、負の数字を変換するとクラッシュする問題を修正 ([#878](https://github.com/google/mozc/issues/878))
* 「ゑ」のカタカナ変換の訂正 (ヸ → ヹ)


## Linux 関連の変更

* Ibus でメニューから直接入力の選択に対応 ([#1061](https://github.com/google/mozc/issues/1061))
* Wayland 上の Ibus で Super + Space からの入力モードの変更に対応 ([#853](https://github.com/google/mozc/issues/853), [#1059](https://github.com/google/mozc/issues/1059))
* 候補ウインドウの HiDPI ディスプレイへの対応を改善 ([#823](https://github.com/google/mozc/issues/823))
* 候補ウインドウがモニター外に移動したときクラッシュする問題を修正 ([#820](https://github.com/google/mozc/issues/820))
* 候補ウインドウのプロセスが複数同時に起動する問題を修正 ([#912](https://github.com/google/mozc/issues/912))


## Windows 関連の変更

* インストール直後に変換できない問題の修正 ([#845](https://github.com/google/mozc/issues/845))
* Windows 11 22H2 で、標準 IME との互換性の向上 (InputScope の値の調整) ([#818](https://github.com/google/mozc/issues/818), [#826](https://github.com/google/mozc/issues/826))
* MS-Word で入力できなくなる問題の修正 ([#819](https://github.com/google/mozc/issues/819))
* 候補ウインドウを縦書き入力に考慮した表示位置に調整 ([#362](https://github.com/google/mozc/issues/362))
* 候補ウインドウのモニター単位での DPI 設定に対応 ([#832](https://github.com/google/mozc/issues/832))


## macOS 関連の変更

* GUI アイコンを高解像度化 ([#964](https://github.com/google/mozc/issues/964))
* UI メニューで  "Google Japanese Input" と表示されていた部分を Mozc に変更 ([caeb9ce](https://github.com/google/mozc/commit/caeb9ceea5e2c5eec73a6b10e0d8304606ff1436))
* mozc_emacs_helper がクラッシュする問題を修正 ([#900](https://github.com/google/mozc/issues/900))
* Apple Silicon 版で GUI ツールがクラッシュする問題を修正 ([#791](https://github.com/google/mozc/issues/791))


## ビルド関連の変更

* C++20 への対応 ([#783](https://github.com/google/mozc/issues/783))
* 変換データの追加方法を簡略化。dictionary_manual/words.tsv を導入 ([8d3a297](https://github.com/google/mozc/commit/8d3a2970014f03cdddf7291b71d632999563f0b6))
* Qt6 のバイナリサイズを削減 ([#822](https://github.com/google/mozc/issues/822))
* Bazel ビルドで dictionary_manual/ 以下のデータを利用するように変更 ([47eb877](https://github.com/google/mozc/commit/47eb87752c1d8e2e0730a44df022f6bc18c8da16))
* Linux 用の Docker 環境を Ubuntu 24.04 へ更新 ([#924](https://github.com/google/mozc/issues/924))
* Android 用の Docker 環境を更新
* Android ライブラリが動作しない問題を解決 ([#840](https://github.com/google/mozc/issues/840))
* Windows でビルド手順の簡略化 (vcvars への依存を解消) ([#923](https://github.com/google/mozc/issues/923))


### GitHub 関連

* GitHub Actions の生成物をリリースビルドに変更 ([07c5f89](https://github.com/google/mozc/commit/07c5f89f716e520c98a796ee7ed1204581686192))
* GitHub Actions の Linux 環境を Ubuntu 24.04 へ更新 ([#924](https://github.com/google/mozc/issues/924))
* Issues で 2020-01-01 以前から更新のない 33 件を `obsolete` としてクローズ ([#800](https://github.com/google/mozc/issues/800))
* Issues のテンプレートを Markdown から YAML のフォーム形式に変更 ([efc4337](https://github.com/google/mozc/commit/efc4337c018fd9e62c429f569d78499abb2a5889))


### Bazel 関連

* Bazel 7 に対応
* Windows への対応
* macOS で .dmg ファイルの作成に対応
* WORKSPACE から Bzlmod へ移行
* `--config=release_build` オプションの追加 ([9fd8739](https://github.com/google/mozc/commit/9fd87395671693e1670f63e61ac1320fd803dc19))
* ビルドの安定性の向上 ([#843](https://github.com/google/mozc/issues/843), [#844](https://github.com/google/mozc/issues/844))


### GYP 関連

* Linux での対応を終了 (deprecated)
* Windows で 64 コア以上でのビルドに対応


### Windows 関連

* Bazel でのビルドへの対応 ([#948](https://github.com/google/mozc/issues/948))
* /BASE オプションの指定をはずす ([#834](https://github.com/google/mozc/issues/834))
* Hardware Enforced Stack Protection の有効化 (/CETCOMPAT) ([#835](https://github.com/google/mozc/issues/835))
* DependedtLoadFlags の有効化 (/DEPENDENTLOADFLAG) ([#836](https://github.com/google/mozc/issues/836))
* TIP DLL の ComCreateInstance への依存を削除 ([#837](https://github.com/google/mozc/issues/837))


### 依存ライブラリの更新

* Abseil: 20230125.3 → 20240722.0
* Google Test: release-1.12.1 → v1.15.2
* Protocol Buffers: v24.2 → v27.3
* Qt:  6.5.2 → 6.7.3
* WiX: v3.14 → v5.0.2


### 依存ライブラリの削除

* ipa_font ([#842](https://github.com/google/mozc/issues/842))
* WTL ([#861](https://github.com/google/mozc/issues/861))


## リファクタリング関連

* Clang のビルドクリーナーを適用
* Abseil 等を活用したコードの最適化 (例: `const vector<T>&` → `absl::Span<const T>`)
* ログを独自実装から Abseil のログへ移行 ([c77285e](https://github.com/google/mozc/commit/c77285efa096e6e400cacffbcded980d24c5b17f))
* macOS: GitHub からApplied suggestions from code scanning alerts ([b955086](https://github.com/google/mozc/commit/b955086d471c9e32174ea9eb39c7dd067aba4542))
* テスト用のセッションコマンドに `UPDATE_COMPOSITION` を追加


## 今後の予定

* GYP のビルドルールを削除
* 変換データの拡充


## そのほか

### macOS 15 (Sequoia)  でのクラッシュ

解決済み。候補ウインドウとのプロセス間通信の実装を変更しました

### 濁点の入力

"U+3099" を変換するか、ひらがな一文字を変換すると濁点付きが候補として表示されます

![濁点つき「あ」の変換候補ウインドウ](https://github.com/hiroyuki-komatsu/zenn/blob/main/articles/komatsuh_mozc_updates_from_2023_10_voiced.png?raw=true)


### US 配列とかな入力

US 配列でのかな入力の配置についての図解をしました

* [configurations.md#kana-input](https://github.com/google/mozc/blob/master/docs/configurations.md#kana-input)

![日本語キーボードのかな配列](https://github.com/google/mozc/blob/master/docs/kana.png?raw=true)
![US キーボードのかな配列](https://github.com/google/mozc/blob/master/docs/kana_us.png?raw=true)

参考: [かな入力 (英語キーボード) の IME ごとの配置の違い](https://zenn.dev/komatsuh/articles/komatsuh_kana_us_keyboard)

### 入力モードの遷移図

入力状態の説明と遷移図を書きました

* [configurations.md#keymap-shortcut-keys](https://github.com/google/mozc/blob/master/docs/configurations.md#keymap-shortcut-keys) 
* [src/data/keymap](https://github.com/google/mozc/tree/master/src/data/keymap)

![入力モードの状態遷移図](https://raw.githubusercontent.com/google/mozc/refs/heads/master/docs/input_modes.svg)
![入力モードのスクリーンショット](https://raw.githubusercontent.com/google/mozc/refs/heads/master/docs/input_modes.png)


## さいごに

PR 範囲の拡大や、誤変換の報告方法を簡略化したことなどもあり、数多く方々からご協力をいただけています。どうもありがとうございます。また、Mozc にかぎらず IME に関心を持っていたり、実際に開発に取り組んでいる方がいらっしゃることもとてもうれしく思っています。これからも応援をよろしくお願いいたします。
