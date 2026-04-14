---
title: "2026年1月のIMEに関するできごと"
emoji: "🗞️"
type: "idea"
topics:
  - "IME"
  - "日本語入力"
published: true
published_at: "2026-02-08 01:00"
---

初稿: 2026-02-07
更新: 2026-02-09
小松弘幸 ([@komatsuh:bsky](https://bsky.app/profile/komatsuh.bsky.social), [@komatsuh:twitter](https://twitter.com/komatsuh))

* [2026年2月分](https://zenn.dev/komatsuh/articles/komatsuh_ime_news_2026_02)

## 主なできごと

### Copilot Keyboard が注目を集める

Copilot Keyboard - 日本語入力を、もっと心地よいものにしたくて - Windows Blog for Japan
https://blogs.windows.com/japan/2026/01/20/copilot-keyboard-japanese-input/

新語は“Google超え”――Microsoftの「Copilot Keyboard」は、正常進化したAI日本語入力だった：小寺信良のIT大作戦（1/3 ページ） - ITmedia NEWS
https://www.itmedia.co.jp/news/articles/2601/15/news131.html


### ATOK Passport のベーシックプランが2026年1月31日で終了

ベーシックプラン (月額330円) が終了し、プレミアムプラン (月額660円)へ一本化

『ATOK Passport』新プランのご案内 | お知らせ |【公式】ATOK.com
https://atok.com/new_plan/


### Simeji が『恋と深空』とのコラボを開催

ゲーム『恋と深空』がテーマのきせかえや特別エフェクトを配布

恋と深空』とキーボードアプリ“Simeji”のコラボが開催。セイヤやレイたちの限定着せ替えや特別エフェクトが期間限定で登場 | ゲーム・エンタメ最新情報のファミ通.com
https://www.famitsu.com/article/202601/64224


## バージョンの更新・リリース

### Mozc が 3.33.6079 に

読みの訂正や日付フォーマットのカスタマイズが改善

Update BUILD_OSS to 6079 and the version to 3.33. · google/mozc@
https://github.com/google/mozc/commit/8a3cf958002f5a48a6f4405d666d3fecd9aadbde


### azooKey (macOS)　が v0.1.3 に

Apple Intelligenceをいい感じ変換のバックエンドに利用できるようになったほか、Colemak・Dvorak配列のサポート、Unicode直接入力などの機能追加

https://github.com/azooKey/azooKey-Desktop/releases/tag/v0.1.3


### azoo-key-skkserv が v0.4.0 に

予測変換の実装など

Release v0.4.0 · gitusp/azoo-key-skkserv

https://github.com/gitusp/azoo-key-skkserv/releases/tag/v0.4.0


### macSKK が 2.9.0 に

補完・変換候補ウィンドウのフォント・背景色を設定可能に

https://github.com/mtgto/macSKK/releases/tag/2.9.0


### KanchokuWS が v1.2.8.9 に

DvorakJ 同様の機能キー定義を導入。薙刀式v17、Merlin、和音漢直配列の同梱

https://github.com/oktopus1959/KanchokuWS/releases/tag/v1.2.9


### AyaoriHIME がα1版をリリース

シン漢直WS改め「AyaoriHIME」（漢織媛）のα1版をリリース

https://github.com/oktopus1959/AyaoriHIME

### 物理学用キーボードアプリ「PhysKeys」がβ版（オープンテスト）中

https://x.com/CharuLab_app/status/2011293277476327830
https://play.google.com/apps/testing/com.charulab.physkeys

### ひらがな手書きキーボードがリリース

https://x.com/KazumaN1172/status/2016037889696493605
https://play.google.com/store/apps/details?id=com.kazumaproject.hiraganahandwritekeyboard
https://github.com/KazumaProject/Hiragana-Hand-Writting-Keyboard

### Akaza が v0.2.1 に

Rust で書かれた日本語 IME の Akaza が v0.2.1 に

https://github.com/akaza-im/akaza/releases/tag/v0.2.1

### IBus-PSKK がアップデート

 『IME として最低限必要な機能を実装できた』と作者によるコメント

 https://github.com/kirameister/ibus-pskk


## IME 関連の技術記事

日本語IMの歴史のまとめ
https://x.com/Matanuki/status/2013182774753350051

jf：「じゅ」から始まるローマ字改造生活 #業務効率化 - Qiita
https://qiita.com/kanekanekaneko/items/4ce3a21b2badd6b57f65

Gemma 3 270M で「かな→漢字」IME向けモデルを開発してみた：SFT / DPO / GRPO 検証まとめ #LLM - Qiita
https://qiita.com/katsuki_ono/items/905fc0ea0b2b9fb573e0


### 関連ツール

【Windows・Mac・Linux】IME変更の取得 #Rust - Qiita
https://qiita.com/deepgreenAN/items/bd79b0b7978639540d3a

Windows IME状態検出の難しさと解決策 #`Windows` - Qiita
https://qiita.com/obott/items/21e71dab752ae65e713b

【Windows】今どの入力モード？IMEの状態を常に表示できる無料アプリ #`Windows` - Qiita
https://qiita.com/obott/items/5e203511c694d2d0b827

【macOS】IME状態をビジュアルで表示するデスクトップ時計アプリを作った #`IME` - Qiita
https://qiita.com/obott/items/4cd4a0337f875498a17c


### 環境構築

Arch(CachyOS)でHazkeyを使う
https://zenn.dev/uliboooo/articles/8a00deb7333477

【備忘録】Ubuntuで日本語入力を導入したときのメモ #Ubuntu - Qiita
https://qiita.com/keihitotose/items/63fb822629fb76c8841b

Chrome Remote Desktop で半角/全角キーが効かない！とその解決方法
https://zenn.dev/masafuro/articles/b30aadc93e9003

Macbook air 2017にインストールしたUbuntuのwayland環境で日英入力切り替えでハマった #Linux - Qiita
https://qiita.com/aikagi/items/c082390408dc6a81bb22

Emacsのmozc.elで変換候補が表示されないときに読む記事
https://zenn.dev/kiyoka/articles/emacs-mozc-version-upgrade-issue

Emacs 精進 18: 今日だけ SKK #Emacs - Qiita
https://qiita.com/toyboot4e/items/d14d7059214ca9ec1145

MacOS EmacsのIMEパッチなしで快適な日本語入力を実現する #GitHubCopilot - Qiita
https://qiita.com/ma0001/items/9fa448b5932dfa4e2c1a


### 開発日記: Android 用の日本語入力アプリをゼロから作る

品詞の細分化／Android 用の日本語入力アプリをゼロから作る その39｜scopedptr
https://note.com/scopedptr/n/n25da3d24a391

タップでの文節区切り／Android 用の日本語入力アプリをゼロから作る その42｜scopedptr
https://note.com/scopedptr/n/n8eeacc3ebc8d


### 開発日記: 日本語IME「ひともじ」

全然、安定せえへんなぁ...。仕切りなおすかぁ。｜えがおIT研究所
https://note.com/egao_it/n/n1892c6c3457f

日本語IME「ひともじ」：漢字以外の文字種がほぼ入力できるようになったヨ(v0.1.4.1)｜えがおIT研究所
https://note.com/egao_it/n/n149679505c6f
