---
title: "かな入力の英語キーボードでの配列の IME ごとの違い"
emoji: "⌨"
type: "idea"
topics:
  - "keyboard"
  - "ime"
  - "Mozc"
published: false
---

初稿: 2024-03-16
小松弘幸 ([@komatsuh:bsky](https://bsky.app/profile/komatsuh.bsky.social), [@komatsuh:twitter](https://twitter.com/komatsuh))

## 概要

かな入力を英語キーボードで使う場合には、IME ごとに配列が異なるのでまとめました。

## かな入力と英語キーボード

かな入力は日本語キーボードのキーレイアウトに基づいた配置がされています。

![かな入力(日本語キーボード)](https://github.com/hiroyuki-komatsu/keyboard_layouts/raw/main/data/kana.png)
*かな入力(日本語キーボード)*

英語キーボードと日本語キーボードでは、キーの物理的なレイアウトが異なります。そのため、英語キーボードではかな入力の配置を調整する必要があります。具体的には、日本語キーボードの `¥ ー` `] む` `\ ろ` の位置に対応するキーが、英語キーボードにはありません。

![かな入力(日本語キーボード)](https://github.com/hiroyuki-komatsu/keyboard_layouts/raw/main/data/kana_highlight.png)
![英語キーボード](https://github.com/hiroyuki-komatsu/keyboard_layouts/raw/main/data/ANSI_61.png)

そのため、`ー` `む` `ろ` の位置を英語キーボード用に配置する必要があります。この調整の仕方は IME ごとに異なっています。

### Mozc

![Mozc でのかな入力 (英語キーボード)](https://github.com/hiroyuki-komatsu/keyboard_layouts/raw/main/data/kana_us_highlight.png)
![かな入力(日本語キーボード)](https://github.com/hiroyuki-komatsu/keyboard_layouts/raw/main/data/kana_highlight.png)
*Mozc でのかな入力 (英語キーボードと日本語キーボード)*

Mozc は、調整が必要なキーのみを英語キーボードで利用できるキーに当てはめています。後述する Windows と同様の調整をしていますが、日本語キーボードとできるだけ同じ配置になるようにしています。Google 日本語入力でも同様です。

### Windows の標準 IME

![Windows でのかな入力 (英語キーボード)](https://github.com/hiroyuki-komatsu/keyboard_layouts/raw/main/data/kana_us_win_highlight.png)
![かな入力(日本語キーボード)](https://github.com/hiroyuki-komatsu/keyboard_layouts/raw/main/data/kana_highlight.png)
*Windows の IME でのかな入力 (英語キーボードと日本語キーボード)*

Windows の標準 IME は、調整が必要な `ー` `む` `ろ` にくわえて `「` `」` の位置も調整しています。`[]` `{}` と対応づけるための調整だと思われますが `「` の位置が日本語キーボードとは異なります。

### macOS の標準 IME

![macOS でのかな入力 (英語キーボード)](https://github.com/hiroyuki-komatsu/keyboard_layouts/raw/main/data/kana_us_mac_highlight.png)
![かな入力(日本語キーボード)](https://github.com/hiroyuki-komatsu/keyboard_layouts/raw/main/data/kana_highlight.png)
*macOS の IME でのかな入力 (英語キーボードと日本語キーボード)*

macOS の標準 IME は、調整が必要な `ー` `む` `ろ` にくわえて `「` `」` `゛` `゜` `へ` の位置も調整しています。他の IME で見られる `ろ` の大移動を避けてシフトキーとの組み合わせた配置であったり、`へ` の位置をあえて変更するなどの特徴があります。

## まとめ

かな入力の英語キーボードでの配置は IME ごとに若干異なっています。IME 開発の参考にしていただけたら幸いです。

現在も使われているかな入力の配置で、ここであげたもの以外の配置がありましたらぜひ教えてください。

## 参照

* [JISキーボード - Wikipedia](https://ja.wikipedia.org/wiki/JIS%E3%82%AD%E3%83%BC%E3%83%9C%E3%83%BC%E3%83%89)
* [USキーボードで「かな入力」 - Macで楽しくお仕事](https://blog.goo.ne.jp/mac-de-oshigoto/e/fa466c8b50a210af84bab595ccf08b7c)
* [hiroyuki-komatsu/keyboard_layouts: Keyboard layouts](https://github.com/hiroyuki-komatsu/keyboard_layouts)
* [mozc/src/unix/ibus/key_translator.cc at master · google/mozc](https://github.com/google/mozc/blob/master/src/unix/ibus/key_translator.cc)

-----

:::message
この文章では、ANSI 104 ベースのキーボードを英語キーボード、OADG 109A ベースのキーボードを日本語キーボードと表記しています。
:::
