---
title: "WISS 2024 入力関連の発表"
emoji: "📜"
type: "idea"
topics:
  - "keyboard"
published: true
published_at: "2024-12-16 01:00"
---

初稿: 2024-12-15
小松弘幸 ([@komatsuh:bsky](https://bsky.app/profile/komatsuh.bsky.social), [@komatsuh:twitter](https://twitter.com/komatsuh))

[WISS 2024](https://www.wiss.org/WISS2024/program.html) で聴講した入力関連の発表です。発表してくださった方々ありがとうございます。

https://www.wiss.org/WISS2024/program.html

関連
* [WISS 2023 文字入力関連の発表](https://zenn.dev/komatsuh/articles/komatsuh_wiss2023_input)


## Whisphone: ささやき声で入力できるイヤホン [05] [1-B03]

https://www.wiss.org/WISS2024Proceedings/data/paper/5.pdf

ささやき声でも音声入力が可能な手法。自分の声は骨伝導によって耳の内部にも伝わるので、ノイズキャンセリングホンの内側についているマイクを活用して集音する。市販のノイズキャンセリングホンでもファームウェアが書き換えられれば実現可能。特許は取得していないので自由に利用可能。

![Whisphone: ささやき声で入力できるイヤホン](https://github.com/hiroyuki-komatsu/zenn/blob/main/articles/komatsuh_wiss2024_input/05.png?raw=true)

## 眼鏡の鼻あてに搭載した圧力センサを用いた耳ぴく入力と身体活動検出手法 [09] [2-A04]

https://www.wiss.org/WISS2024Proceedings/data/international/9.pdf

耳をぴくぴく動かす動作を読み取って入力として活用するための装置の提案。耳ぴくだけではなく、瞬き、歩行、脈拍もそれぞれ同時に取得できている。

![眼鏡の鼻あてに搭載した圧力センサを用いた耳ぴく入力と身体活動検出手法](https://github.com/hiroyuki-komatsu/zenn/blob/main/articles/komatsuh_wiss2024_input/09.png?raw=true)

## 母音，子音の順に選択を行う間接タッチ用かな文字入力手法 [10] [2-A11]

https://www.wiss.org/WISS2024Proceedings/data/international/10.pdf

スマートウォッチを活用した文字入力手法。ベゼルを活用してスライドインすることによって、フリック入力に近い母音入力を実現している。そのために、フリック入力とは逆に母音→子音という順番での入力になっている。(例: 「に」の入力 = 左からスライドイン + 中央でタッチアップ)

![母音，子音の順に選択を行う間接タッチ用かな文字入力手法](https://github.com/hiroyuki-komatsu/zenn/blob/main/articles/komatsuh_wiss2024_input/10.png?raw=true)

## picoRing: battery-free rings for subtle thumb-to-index input [24]

https://www.wiss.org/WISS2024Proceedings/data/international/24.pdf

電池が不要な指輪型デバイスの提案。リストバンドデバイスと協調し、それぞれがセンサーコイルとリーダーコイルとして働いている。

![picoRing: battery-free rings for subtle thumb-to-index input](https://github.com/hiroyuki-komatsu/zenn/blob/main/articles/komatsuh_wiss2024_input/24.png?raw=true)

## 近距離無線通信を用いた形状自在キーボードシステム [1-A03]

https://www.wiss.org/WISS2024Proceedings/data/demo/1-A03.pdf

キーボードでキーを自由に配置できる仕組みの提案。キーのそれぞれに NFC タグを設置する。ボード側にはコイルがあり、NFC への無線給電と信号の読み取りを行っている。

![近距離無線通信を用いた形状自在キーボードシステム](https://github.com/hiroyuki-komatsu/zenn/blob/main/articles/komatsuh_wiss2024_input/1-A03.png?raw=true)

## HMKとアイポインティングを組み合わせたマルチモーダルな入力手法 [1-A10]

https://www.wiss.org/WISS2024Proceedings/data/demo/1-A10.pdf

ヘッドマウントディスプレイの横側にキーボードを配置した HMK (ヘッドマウントキーボード) の発展型。HMK と視線によるポインティングを組み合わせた手法の提案。

![HMKとアイポインティングを組み合わせたマルチモーダルな入力手法](https://github.com/hiroyuki-komatsu/zenn/blob/main/articles/komatsuh_wiss2024_input/1-A10.png?raw=true)

## LensTouch+: スマートグラスのレンズ面を使った入力手法の拡張 [1-B11]

https://www.wiss.org/WISS2024Proceedings/data/demo/1-B11.pdf

AR グラスのレンズ面をタッチパネルとして活用する LensTouch の発展型。現実の物体への操作などの手法の提案。

![LensTouch+: スマートグラスのレンズ面を使った入力手法の拡張](https://github.com/hiroyuki-komatsu/zenn/blob/main/articles/komatsuh_wiss2024_input/1-B11.png?raw=true)

## 導電性／強磁性を併せ持つ毛状の入力インタフェースの提案 [2-B18]

3D プリンターによって作成した毛状の素材を入力装置として活用する提案。磁力によって毛先が変化するペンデバイスを作成している。

![導電性／強磁性を併せ持つ毛状の入力インタフェースの提案](https://github.com/hiroyuki-komatsu/zenn/blob/main/articles/komatsuh_wiss2024_input/2-B18.png?raw=true)

## ハンドヘルド円筒面タッチインタフェースの提案 [2-B19]

https://www.wiss.org/WISS2024Proceedings/data/demo/2-B19.pdf

円筒型のタッチパッドの提案。縦持ちや横持ち、環状のドラッグ操作や、右手左手それぞれの回転操作などが可能。

![ハンドヘルド円筒面タッチインタフェースの提案](https://github.com/hiroyuki-komatsu/zenn/blob/main/articles/komatsuh_wiss2024_input/2-B19.png?raw=true)

## 入力途中の文字列をリアルタイム共有する同期的なグループチャットシステム [3-B15]

https://www.wiss.org/WISS2024Proceedings/data/demo/3-B15.pdf

チャットへの送信前の入力中の文字入力もリアルタイムで表示するシステムの提案。複数人が同時に入力している際にどのように表示すべきかを議論している。

![入力途中の文字列をリアルタイム共有する同期的なグループチャットシステム](https://github.com/hiroyuki-komatsu/zenn/blob/main/articles/komatsuh_wiss2024_input/3-B15.png?raw=true)

