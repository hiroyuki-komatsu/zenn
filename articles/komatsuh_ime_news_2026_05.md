---
title: "2026年5月のIMEに関するできごと"
emoji: "🗞️"
type: "idea"
topics:
  - "IME"
  - "日本語入力"
published: true
published_at: "2026-06-22 00:30"
---

初稿: 2026-06-22
小松弘幸 ([@komatsuh:bsky](https://bsky.app/profile/komatsuh.bsky.social), [@komatsuh:twitter](https://twitter.com/komatsuh))

* [2026年4月分](https://zenn.dev/komatsuh/articles/komatsuh_ime_news_2026_04)
* [2026年6月分](https://zenn.dev/komatsuh/articles/komatsuh_ime_news_2026_06)


## 主なニュース

### Colipot Keyboard が機能更新

Copilot Keyboard が大型アップデート。辞書のインポート/エクスポート、日付入力などを追加

>Copilot Keyboard — GA 後はじめての大型アップデートをお届けします - Windows Blog for Japan

https://blogs.windows.com/japan/2026/05/29/copilot-keyboard-ga-%e5%be%8c%e3%81%af%e3%81%98%e3%82%81%e3%81%a6%e3%81%ae%e5%a4%a7%e5%9e%8b%e3%82%a2%e3%83%83%e3%83%97%e3%83%87%e3%83%bc%e3%83%88%e3%82%92%e3%81%8a%e5%b1%8a%e3%81%91/

https://winblogs.thesourcemediaassets.com/sites/31/2026/05/b7d1cee4cc3c81bb0f97cf70dd5fcbf1.png


> 「Copilot Keyboard」は「カイル」くんが居るだけのIMEではない ～開発者に聞く開発秘話【特集・集中企画】 - 窓の杜

https://forest.watch.impress.co.jp/docs/special/2108844.html



### ATOK が辞書を更新
ATOK がキーワード Express, 乗換案内 駅名変換辞書, 第 37 回 ATOK 変換改善を更新

> XユーザーのATOK公式さん: 「【5月の配信キーワード】 ATOKキーワードExpressで今月配信された単語を一部ご紹介。気になるワードはワンクリック検索できます。 ●野球「キック・セリー」 ●時事「ヒューマノイドロボット」「GUNMA PASSPORT」「ハンタウイルス」「映画館大賞」「ブルームーン」 詳細は→https://t.co/u0HcEpsIIF https://t.co/2OZs2x4Xqz」 / X

https://x.com/atok_js/status/2059098338012840215


> XユーザーのATOK公式さん: 「【第37回・ATOK変換改善のご連絡】 本日、最新辞書を公開しましたのでアップデートしてお使いください。 ※改善例：「申請/現る」→「新星/現る」、「スピカ/津」→「スピ活」、「外/組み直し」→「租特/見直し」など その他の改善事例はこちらから：https://t.co/qoa8HBOfzM https://t.co/2OeDj1iJ0w」 / X

https://x.com/atok_js/status/2054024353726288338

> XユーザーのATOK公式さん: 「ATOK Passportで、「乗換案内 駅名変換辞書」2026年5月版を公開しました。新駅に対応しています。 最初の数文字を入力するだけで、正確な駅名を一発で表示します。 例） 「てがらやまへいわこうえん」→「手柄山平和公園」 詳しくは ↓ Win：https://t.co/7pANjQuIGj Mac：https://t.co/pGywOVAPXo https://t.co/TlfIur7LEq」 / X

https://x.com/atok_js/status/2056548340293394770


## 新規 IME の公開情報

### Bonolith
Linux 用のローカル LLM を活用した IME が公開。JaIM から改名

> BonoJovi/Bonolith: LLM-powered Japanese input method for Linux (IBus & Fcitx5), written in Rust.

https://github.com/BonoJovi/Bonolith

> 【今年55歳のおっちゃん】オリジナルIMEをリブランディングするの巻 #Linux - Qiita

https://qiita.com/BonoJovi/items/11e97a3f0af18a33c8ff


### T-Code IME for Windows

Windows 用の T-Code (漢字直接入力) IME が公開

> NicheAppLab/T-Code-IME-for-Win

https://github.com/NicheAppLab/T-Code-IME-for-Win

> Xユーザーのimuno@シリコンバレー8年目さん: 「エンジン部分完全に再利用でいろいろやったところ, Windowsでも自作IME動くようになりました. あとはインストーラーをどうするか, ですね. しかしどうして実装がこんなにバラバラになった…(エンジンをScalaで書いたから自業自得) #新配列 の日 https://t.co/niywNKh1iM」 / X

https://x.com/imunolion/status/2056574435705176287

> Xユーザーのimuno@シリコンバレー8年目さん: 「Windows用のT-Code IMEのテストリリースができました. https://t.co/e4MqNmqW7B 問題があれば私にDMか GitHub にて Issue に登録していただけると幸いです.」 / X

https://x.com/imunolion/status/2057608702203727877

### ja-furigana

日本語のふりがなを取得するライブラリ

> RyuuNeko1107/ja-furigana: 日本語フリガナ (ルビ) を扱う Rust 製ライブラリ + ローカル HTTP サーバー。ルールはすべてデータ駆動 (TOML)。

https://github.com/RyuuNeko1107/ja-furigana

> ふりがなAPIの core を OSS にしました — ja-furigana 0.1.0 stable リリース - 黒猫ゲーム部

https://ryuuneko.com/blog/api-core-oss-ja-furigana-010-stable

> Xユーザーの黒猫ゲーム部(YouTube配信者兼個人開発)さん: 「ついに、OSS版「ja-furigana」 v0.1.0 Stable 公開しました。 🎉 TTS向け前処理を目的にした、日本語ルビ振りエンジンです。 単純な辞書置換ではなく、 文脈・候補スコアリングを用いた読み推定に対応。 VOICEVOX等の読み上げ前処理、 配信コメント読み上げ、 TTS補助用途を想定しています。」 / X
https://x.com/ryuuou_neko/status/2055204007812235643

### Mozc-UT-dpkg-installer

Mozc 用の拡張辞書 Mozc-UT を Debign/Ubuntu などの dpkg 環境でインストールするためのスクリプト

> PenguinCabinet/Mozc-UT-dpkg-installer: dpkg環境においてmozc-utをワンライナーでインストールするスクリプト
 
https://github.com/PenguinCabinet/Mozc-UT-dpkg-installer


## IME の更新情報

デスクトップ用

### Mozc
「語彙集合および変換結果に関する方針」が作成される

https://github.com/google/mozc/blob/master/VOCABULARY_POLICY.md

### Mozkey
koyasi777/mozc が Mozkey として公開。v0.7.3 へ更新。ニューラル変換の Zenzai との統合、ライブ変換機能と遅延変換やルビ表示などの機能追加、変換結果の調整、ショートカットキーの複数コマンド対応など

> Release Mozkey v0.7.4 · koyasi777/mozkey

https://github.com/koyasi777/mozkey/releases/tag/v0.7.4


> Xユーザーのkoyasi777さん: 「v0.7.0公開しました。本バージョンから 『Mozkey（もずきー）』という名称に 変更します（アイコンも変わりました） ご愛顧のほど宜しくお願い致します。 https://t.co/e9vTnlXmDj」 / X

https://x.com/koyasi777/status/2058521919666982940

> Xユーザーのkoyasi777さん: 「v0.6.0公開しました。 ライブ変換の『補正機能』として ニューラルかな漢字変換(zenz-v3.2)を導入しました。 少し待つだけで、このようにzenzが補正してくれます。 またzenz学習を有効にすると、通常のライブ変換ですぐその変換が表示されます。 AIで変換結果と辞書を補正していくアプローチです。 https://t.co/aDiRoOQraO」 / X

https://x.com/koyasi777/status/2056914486603432330

>Xユーザーのkoyasi777さん: 「v0.4.1公開致しました。ライブ変換に対応しました。 工夫点としては、リアルタイムで変換がかかるため、入力中の「かな」が分かるようにルビウィンドウを搭載。 また入力途中で変換が実行されることによる意図しない変換を避けるため、変換遅延のパラメータを設定可能に。 https://t.co/iu3gVioDy4 https://t.co/LTeE00iXHD」 / X

https://x.com/koyasi777/status/2050924730203693372


### mozc-ports for FreeBSD
2026-05-12 に bazel9-build に更新。バグの修正やライブラリの更新など

> kdeguchi/mozc-ports: Latest version mozc ports for FreeBSD

https://github.com/kdeguchi/mozc-ports


### azooKey on macOS
v0.1.4 に更新。zenz-v3.2 への更新より変換精度が向上。予測入力機能・誤入力訂正機能を実験的に導入

> Release v0.1.4 · azooKey/azooKey-Desktop

https://github.com/azooKey/azooKey-Desktop/releases/tag/v0.1.4

> XユーザーのMiwa - azooKeyの開発者さん: 「azooKey (macOS) v0.1.4を出しました！新規に8名の方からPRをいただいてマージしてます！ ニューラルかな漢字変換モデルを新しくしたほか、開発中の新機能を試験実装しています。 https://t.co/KKaoGTmLQz」 / X

https://x.com/miwa_ensan/status/2056016378206056487


### Karukan
絵文字入力や記号入力に対応

> Xユーザーのtogatogaさん: 「Karukanの絵文字入力機能をサポートしました。Slack風入力もサポートしているので:kiniku =&gt; 💪 :pien =&gt; 🥺 で絵文字が打てるようになりました。 そろそろ機能が揃ってきたのでv0.2.0を出す予定です。 https://t.co/hSfqP22oK9 https://t.co/Kx2jYPmGv6」 / X
 
https://x.com/togatoga_/status/2056712528760328558

> Xユーザーのtogatogaさん: 「Karukanの記号や数字の変換機能を強化しました。丸数字①や括弧など「」みたいなのが変換しやすくなりました。 https://t.co/j5PUmMDJS5 https://t.co/vJr4ukgaNY」 / X

https://x.com/togatoga_/status/2055553567772328319


### rakukan
0.9.4 に更新。ライブ変換時の設定項目の追加や変換候補の順序調整など

> Release 0.9.4 · fukuyori/rakukan

https://github.com/fukuyori/rakukan/releases/tag/0.9.4


### SwiftyGyaim
v1.5.6 に更新。辞書の更新、辞書インポート機能の追加、候補ウインドウの修正など

> Release v1.5.6 · tanabe1478/SwiftyGyaim
 
https://github.com/tanabe1478/SwiftyGyaim/releases/tag/v1.5.6


> Xユーザーのtanabe1478さん: 「ずっと気になっていたSwiftyGyaimの候補ウィンドウの位置の問題に手を入れてみた https://t.co/dcIYKFvKRf」 / X

https://x.com/t__nabe1478/status/2051514907124957370


### Akaza (ibus-akaza)
v2026.530.0 に更新。変換速度の最適化など

> Release v2026.530.0 · akaza-im/akaza

https://github.com/akaza-im/akaza/releases/tag/v2026.530.0


> akaza v2026.530.0 を出しました - tokuhirom's blog

https://blog.64p.org/entry/2026/05/30/012857


### Akaza for Mac
v2026.519.0 に更新。バグの修正など

> Release v2026.519.0 · akaza-im/mac-akaza

https://github.com/akaza-im/mac-akaza/releases/tag/v2026.519.0


> mac-akaza v2026.519.0 が出ました - tokuhirom's blog

https://blog.64p.org/entry/2026/05/20/142642


### ひともじ
v0.5.3 に更新。候補ウインドウへの対応や人名漢字の追加など

> Release v0.5.3 人名漢字と、アプリ側のモード認識処理の追加 · Toshishi-egaoit/hitomoji

https://github.com/Toshishi-egaoit/hitomoji/releases/tag/v0.5.3

> 日本語IME「ひともじ」:人名漢字の追加と、アプリ動作モードの認識処理(v0.5.3)｜えがおIT研究所
 
https://note.com/egao_it/n/n5caa4b78a690


### MZ-IME日本語入力
v1.0.0.8 に更新。メインアイコンの色調更新など

> Release v1.0.0.8 · katahiromz/mzimeja
 
https://github.com/katahiromz/mzimeja/releases/tag/v1.0.0.8


### Canna

郵便番号の更新、ローマ字変換のバグ修正や漢字変換の精度向上など

> 日本語入力システム Canna (『かんな』)

https://canna-input.github.io/index.ja.html


> canna/CHANGES.jp at release-3.8 · canna-input/canna

https://github.com/canna-input/canna/blob/release-3.8/CHANGES.jp


----
モバイル用

### Gboard

音声入力機能の Rambler を Google I/O で発表。言い淀みや言い直しなどを自然に解釈

> Gemini Intelligence brings proactive AI to Android

https://blog.google/products-and-platforms/platforms/android/gemini-intelligence/

> グーグル、次世代の音声入力「Rambler」発表　言いよどみや言い直しをAIが自動で整理 - ケータイ Watch

https://k-tai.watch.impress.co.jp/docs/news/2107625.html


### Sumire

v1.7.73 へ更新。カスタムキーボードの設定項目の拡充、グライド入力の実装、辞書の更新など

> XユーザーのKazuma.Nさん: 「Sumire キーボード 1.7.52 をリリースしました。カスタムキーボードに Shift、CapsLock、直接入力などのアクションを追加し、テンプレートに QWERTY 配列も追加しました。QWERTY は今後のカスタマイズ拡張に向けた土台として実装しています。 https://t.co/uZFPmS4nuc」 / X

https://x.com/KazumaN1172/status/2051114975595216906


> XユーザーのKazuma.Nさん: 「Sumire キーボード v1.7.55 をリリースしました。 今回のアップデートでは、英語 QWERTY キーボードでグライド入力の実装を試みました。 キーを1つずつタップする代わりに、指を滑らせることで単語を入力できるため、入力時のタップ数を減らすことができます。 https://t.co/4zf1XMnXDk https://t.co/SG2Tm92nRn」 / X

https://x.com/KazumaN1172/status/2052210238883783046


> XユーザーのKazuma.Nさん: 「Sumire キーボード 1.7.57 をリリースしました。グライド入力の連続入力設定を追加し、カスタムQWERTYでキー・スペーサー・半マス配置に対応しました。 https://t.co/seCigBYQUx https://t.co/kuaaxqfJDF」 / X

https://x.com/KazumaN1172/status/2053503915543437553


### Simeji

ぷよぷよとのコラボでキーボードのテーマを配布

> Z世代に大人気！キーボードアプリ「Simeji」、35周年を迎えた人気ゲーム『ぷよぷよ』シリーズとコラボキャンペーンを開催！ | バイドゥ株式会社のプレスリリース

https://prtimes.jp/main/html/rd/p/000000965.000006410.html


> XユーザーのSimejiさん: 「/／ 『 #ぷよぷよxSimeji 』コラボ第一弾！ 　2424れんさチャレンジ達成💚❤️💛💜💙 \＼ みんなのおかげで きせかえ【2️⃣種類】追加解放決定‼️ かわいい､ζ､°ょたちをGETしよう🫧 Simejiアプリ内バナーからチェックしてね〜🫶 https://t.co/9Hiwlv5Gv5 https://t.co/xcX3FrM6DS」 / X

https://x.com/Simeji_pr/status/2057658512252285220


### ニンジャマイルズ

iOS 版では背景画像の調整機能が追加、Android 版ではタイピングゲームが追加

> Xユーザーのニンジャマイルズ | キーボードポイ活さん: 「【アプデ情報🥷💭ios🍎】 \\✨カスタムキーボードについて✨// ユーザーさんからのお声でカスタムキーボードで背景画像を使用する際、背景画像のトリミング比率が調整できるようになったである！💨💖 キーボードも自分好みに仕上げてどんどんマイルを積み上げるでござる‼︎⚔️💰」 / X
 
https://x.com/ninjamiles_app/status/2056556475380896112


> Xユーザーのニンジャマイルズ | キーボードポイ活さん: 「【アプデ情報🥷💭Android】 \\✨"タイピング道場"現る✨// お待たせしたでござる🤖❤️ アンドロイドにオリジナルタイピングゲーム"ワークアウト"が実装⚔️ ランキング上位者には巻物📜も付与！毎週ランクもあげてマイルも巻物もGET💰🍃 いますぐアプデ！✅ #ニンジャマイルズ #キーボードポイ活」 / X

https://x.com/ninjamiles_app/status/2056217936038363327


----
SKK

### macSKK
2.16.0 へ更新。単語登録機能の拡充や辞書読み込み機能の追加など

> XユーザーのGTOさん: 「macSKK v2.16.0をリリースしました。 #macSKK ・変換候補のように補完候補をキー決定できるようにした ・単語登録モードでTabキーで読みを入力する ・バグ修正 補完候補のキー確定機能は自分で使っててもかなり便利です👍 https://t.co/qlqsZ7jXKo」 / X

https://x.com/mtgto/status/2060730149788848463

> XユーザーのGTOさん: 「macSKK v2.14.0をリリースしました。 #macSKK ・Gzip圧縮されたままのSKK辞書を読めるようにした ・単語登録時に先頭スペースを無視する設定を追加 (Thanks! @tekezo ) https://t.co/PSlh363yJ7」 / X

https://x.com/mtgto/status/2051918482292592737


### nskk.el
v0.2.1 へ更新。セキュリティを含むバグ修正など

> Release v0.2.1 · takeokunn/nskk.el

https://github.com/takeokunn/nskk.el/releases/tag/v0.2.1

----
漢字直接入力

### AyaoriHIME (漢織媛)
α5 へ更新。同時打鍵機能や辞書の改善、任意のキーを修飾キーにする機能の改修など

> Release AyaoriHIME α5 · oktopus1959/AyaoriHIME

https://github.com/oktopus1959/AyaoriHIME/releases/tag/alpha-5


### MacTcode
v0.20.0 へ更新。交ぜ書きや部首キャンセルでの問題の修正など

> XユーザーのKaoru Maeda 前田 薫さん: 「MacTcode v0.19.0をリリースしました。 変換キャンセルで消えすぎるのは、Ctrl-Hを押したときにMacTcodeが送るBackspaceがアプリによって「Ctrl-Backspace」と解釈されるのが原因でした。 Ctrlのいらないキャンセルキー「/」を追加してワークアラウンドします https://t.co/gsceh2e2wm」 / X

https://x.com/mad_p/status/2056188588111602021


### T-Code IME
2026-05-08 へ更新。部首合成機能の柔軟性の向上など

> T-Code IME - Google Play のアプリ

https://play.google.com/store/apps/details?id=com.nicheapplab.t_codeime

----
Emacs 用

### Sumibi
v6.1.0 へ更新。類語・対義語などを提示する語彙ナビゲーター機能の追加。句読点での変換に遅延を追加など

> Release Sumibi v6.1.0 · kiyoka/Sumibi

https://github.com/kiyoka/Sumibi/releases/tag/v6.1.0


### quail-naggy
v0.21 へ更新。動作確認用の Dockerfile の追加やドキュメントの追加など。単漢字変換辞書の公開も

> JRF-2018/quail-naggy: 単漢字変換 Input Method for Emacs

https://github.com/JRF-2018/quail-naggy

> Release 単漢字変換の動態保存のための特例設置 · JRF-2018/quail-naggy

https://github.com/JRF-2018/quail-naggy/releases/tag/jrf_tankanji-20120505

----
ツール・ライブラリ

### kotlin-kana-kanji-converter
v1.7.200 に更新。辞書の更新など

> KazumaProject/kotlin-kana-kanji-converter: Kotlin かな漢字変換プログラム

https://github.com/KazumaProject/kotlin-kana-kanji-converter

----
音声入力

### Amical Desktop
v1.7.1 へ更新。複数言語の音声入力への対応やバグの修正など

> Releases · amicalhq/amical

https://github.com/amicalhq/amical


## IME の技術記事

### 生成 AI 会での azooKey の発表

> 「ニューラルかな漢字変換」の 社会実装 - Speaker Deck

https://speakerdeck.com/miwa_keita/niyurarukanahan-zi-bian-huan-no-she-hui-shi-zhuang

> 生成AI会 Vol.2@渋谷（LLMプロダクト開発・ハーネスエンジニアリング） - connpass

https://seisei-ai.connpass.com/event/388188/


## IME 開発の記事

### アヤメキーボード

Talkback を使った視覚障害者が確実に入力できるための IME。Sumire キーボードがベース

> 視覚障害者のための Android IME「アヤメキーボード」開発ノート｜風吹き童子 やま

https://note.com/yama3nomori/n/n313242857ca4

> yama3nomori/ayame: Android用TalkBack対応のIME

https://github.com/yama3nomori/ayame


### GiME

ゲームパッドで文字入力をするためのアプリケーション。韓国語やヒンドゥー語などにも対応

> 【GiME】格ゲーぽく日本語を打てるIME #新配列｜msonrm（なるなる）

https://note.com/msonrm/n/nf932cb880149


### 日本語入力アプリ | scopedptr

Android 用 IME。ベータテスターを募集中

> 変換履歴でのサジェスト／Android 用の日本語入力アプリをゼロから作る その51｜scopedptr

https://note.com/scopedptr/n/n119b85ef5796

> シークレットモード／Android 用の日本語入力アプリをゼロから作る その53｜scopedptr

https://note.com/scopedptr/n/n164bcc2dfa8f


### ひともじ

Windows 用の漢字直接入力 IME。「風」の 64ビット版が目標

> 日本語IME「ひともじ」:漢字候補ウィンドウが出た！(v0.5)｜えがおIT研究所
 
https://note.com/egao_it/n/n4a244fffc2a3

> 日本語IME「ひともじ」：Undo処理（とりあえず）完了(v0.4.3.2)｜えがおIT研究所

https://note.com/egao_it/n/nae3aaef645c1


## IME に関する記事

### IME 全般の記事

> サブスクはデジタル税金? 33年間お世話になったATOKを卒業しました【老師オグチの家電カンフー】- 家電 Watch

https://kaden.watch.impress.co.jp/docs/column/kanhoo/2111720.html


> 【IMEユーザー辞書】 専門辞書で日本語入力を快適にしたい。 生物・医学分野のストレスを減らそう。｜えぶりょう

https://note.com/modern_serval63/n/nbcf53f4b8888


> XユーザーのF太🐈‍⬛さん: 「ローマ字のままAIに投げるのがラクすぎる」 / X

https://x.com/fta7/status/2059754329058488795


> パソコンで日本語が打てない！アルファベットになる時の直し方【初心者向け】｜Tscschool

https://note.com/tsc_school/n/n2cc41215af4a


> スマホやPCで中国語の入力ができるようになろう──準備からDAZIでの練習まで｜氷野善寛＠キクタン中国語・目白大学中国語学科・ドワンゴZenStudy中国語コース担当

https://note.com/cnstation/n/n1bdc79b26527


### macOS 標準 IME

> DMiME 医学医療用語変換辞書を『追加辞書』に登録する｜QuickTimer

https://note.com/quicktimer/n/nbf91c8e5a949

### iOS 標準 IME

> 日本語入力が時々おかしくなる（iOS26.4以降）｜ふと、メモ

https://note.com/hitokoto_archive/n/n2842edc2b62b


### Windows 標準 IME

> 日本語入力が画面左上に出る！ちょっと迷惑な機能の原因と直し方【Windows 10/11】 - きみよや

https://kimiyoya.com/windows-ime-text-top-left-fix/


### Copilot Keyboard

> AI時代のIME「Copilot Keyboard」にあのイルカが帰ってきた｜ペシェ（ゲーム攻略・解析）

https://note.com/gamecentergx/n/n1af0408b85ec


### ChromeOS 標準 IME

> ChromeOSの恐ろしいバグ｜ハイドロ - Hydro

https://note.com/hydro_detail/n/ne8baa2bf4e6e


### Google 日本語入力

> 【Mac Info】Appleシリコン対応「Google 日本語入力」はMac標準入力と何が違う？ - PC Watch

https://pc.watch.impress.co.jp/docs/column/macinfo/2109409.html


> Windowsの変換候補に間違った言葉が出る原因と消し方｜IMEの予測候補を削除・追加する方法｜eguweb

https://note.com/eguweb/n/n9c89b297f5b9


> Mac mini のGoogle日本語入力動かなくてムキーってなってたけどシステム設定のログイン項目と機能拡張のアプリのバックグラウンドでのアクティビティをオンにしたらやっと動いた件｜かやの🌿

https://note.com/kaya_n0te/n/nd792db255bdc


> Google日本語入力プロファイル切り替え用ソフト「せせらぎ」 - 小川謙三の毒にも薬にもならない話

https://jigendaddy.hatenablog.com/entry/2026/05/11/064455

### かわせみ

> Macの日本語入力ストレス解消へ。標準IMEからかわせみ4へ乗り換えた記録｜corneliuspapa

https://note.com/corne88/n/nf5c8f9bc7e2d

### FreeWnn

> tamago-tsunagi with FreeWnn on Emacs 30.2, Fedora 43 #fedora - Qiita

https://qiita.com/Mercury/items/11598c5a99f0ec1494c5

### SKKelton

> SkkeletonでAZIKするTips #Lua - Qiita

https://qiita.com/nakamura795/items/051414dc97b11c332989


### T-Code

> 今日5月21日は… - ujimushi(@旧sradjp(15364))の日記
 
https://ujimushisradjp.hatenablog.jp/entry/2026/05/21/031236

### IME 関連技術

> PySide(Qt)で日本語入力候補の位置を調整した話｜hon

https://note.com/genial_snipe3018/n/n1a56978e7f45


### キー配列関連

> 「自作キーボード」界隈のおとなり「論理配列」界隈。日本語の入力効率を爆上げしてくぜ | ギズモード・ジャパン

https://www.gizmodo.jp/article/naginata-ime/


> 【薙刀式】毎年5/19は新配列の日！　#新配列: 大岡俊彦の作品置き場

https://oookaworks.seesaa.net/article/520689736.html#gsc.tab=0


### IME 環境設定

> 第911回　Waylandで行こう[Kubuntu編] | gihyo.jp

https://gihyo.jp/admin/serial/01/ubuntu-recipe/0911

> Android（Termux + Ubuntu）でfcitx5 + mozcを使った日本語入力環境を構築した

https://zenn.dev/nognog/articles/android-termux-ubuntu-fcitx5-mozc-japanese-input


> MacBookにUbuntuをインストールして日本語入力できるようになるまで #Claude - Qiita

https://qiita.com/kazukikudo/items/da58164ec797394c0598

> Ubuntu26.04上のfcitx5-mozcの問題解決 | IMUZA.com
 
https://imuza.com/fcitx5-mozc-on-ubuntu2604/


## 今月紹介した IME / 関連ツール

* Colipot Keyboard
* ATOK
* Bonolith
* T-Code IME for Windows
* ja-furigana
* Mozc-UT-dpkg-installer
* Mozc
* Mozkey
* mozc-ports for FreeBSD
* azooKey on macOS
* Karukan
* rakukan
* SwiftyGyaim
* Akaza (ibus-akaza)
* Akaza for Mac
* ひともじ
* MZ-IME日本語入力
* Canna
* Gboard
* Sumire
* Simeji
* ニンジャマイルズ
* macSKK
* nskk.el
* AyaoriHIME (漢織媛)
* MacTcode
* T-Code IME
* Sumibi
* quail-naggy
* kotlin-kana-kanji-converter
* Amical Desktop
* アヤメキーボード
* GiME
* 日本語入力アプリ | scopedptr
* macOS 標準 IME
* iOS 標準 IME
* Windows 標準 IME
* ChromeOS 標準 IME
* Google 日本語入力
* かわせみ
* FreeWnn
* SKKelton
* T-Code
