---
title: "Mozc の概要と周辺技術"
emoji: "🟠"
type: "tech"
topics:
  - "ime"
  - "mozc"
published: false
---

初稿: 2024-10-26

小松弘幸 ([@komatsuh:bsky](https://bsky.app/profile/komatsuh.bsky.social), [@komatsuh:twitter](https://twitter.com/komatsuh))

日本語入力ソフトウェア Mozc の概要と、Mozc で活用している外部のライブラリやツールを紹介します。

この文章は 2024-10-19 に [GDGs Innovatitve Crosstalk at 東大](https://gdgkwansai.connpass.com/event/329411/) で発表した内容をもとにしています。日本語入力の開発に関わっていない方にも興味を持っていただけるように、日本語入力の概要とさまざまな開発に応用できそうなものを幅広く紹介することが目標の内容です。


## Mozc の特徴

Mozc はオープンソースの日本語入力ソフトウェアです。Google 日本語入力と共通のコードベースを使用していますので、操作性や機能については同じものです。Mozc の変換用データは、オープンソース由来のデータをもとに作成しています。そのため、変換性能については Google 日本語入力と異なります。

また、Mozc の対応プラットフォームは Windows, macOS にくわえて、Android 用の変換ライブラリと Linux にも対応しています。

## かな漢字変換の仕組み

Mozc で使用しているかな漢字変換の仕組みを非常に単純化すると、最短経路問題です。

1. 入力されたひらがな列から、取りうる単語の組み合わせをすべて列挙します。
2. 取りうる各単語のどのくらい使われるものか（頻度情報）や、前後の単語が一緒によく使われるものか（接続コスト）を数値化しておきます。
3. 各組み合わせの数値を計算して、もっともよい数値になる組み合わせを変換結果とします。

次の図は、「いまはれです」を変換した場合の例です。単語とそれぞれを結ぶ線がコストという形で数値化されています。この中で、もっともコストが低くなる組み合わせから「今晴れです」を算出しています。

![組み合わせから「いまはれです」を「今晴れです」に変換する例](https://github.com/hiroyuki-komatsu/zenn/blob/main/articles/komatsuh_mozc_gdg2024/lattice.svg?raw=true)

### 単語の辞書引き

最短経路を取得するためには、取りうる単語を列挙する必要があります。このために Mozc では TRIE (トライ) という木構造を使っています。

TRIE は、各単語の先頭部分で共通する文字を同じノードとして共有します。

次の図は、t, the, this, thin, think, thinks, tv, to, too から構成される TRIE です。各単語に対応しているノードがハイライトされています。

![TRIE の例](https://github.com/hiroyuki-komatsu/zenn/blob/main/articles/komatsuh_mozc_gdg2024/trie.svg?raw=true =250x)

ここで "thinkso" という文字列から、取りうる単語の組み合わせを列挙してみます。上記の TRIE を t,h,i... と一文字ずつ巡っていくと、s までたどり着きます。今度は s から上に向かいつつハイライトされているノードを取得していきます。すると、thinks, think, thin, t が取得されました。これで、"thinkso" という文字列から取りうる単語を列挙できます。

![TRIE に thinkso を適用](https://github.com/hiroyuki-komatsu/zenn/blob/main/articles/komatsuh_mozc_gdg2024/trie_thinkso.svg?raw=true =250x)

同様にして、"hinkso", "inkso", ... と繰り返せばすべての単語を列挙できます。

![ithinkso の列挙](https://github.com/hiroyuki-komatsu/zenn/blob/main/articles/komatsuh_mozc_gdg2024/lattice_thinkso.png?raw=true)


