---
title: "キーボード／マウス エミュレーターを macOS で操作する"
emoji: "🎛️"
type: "tech"
topics:
  - "keyboard"
  - "USB"
  - "macOS"
published: true
published_at: "2024-05-05 23:30"
---

初稿: 2024-05-05
小松弘幸 ([@komatsuh:bsky](https://bsky.app/profile/komatsuh.bsky.social)), [@komatsuh:twitter](https://twitter.com/komatsuh)

「キーボード／マウス エミュレーター」というデバイスを macOS の Python で動作させる方法のメモです。

## キーボード／マウス エミュレーター

「キーボード／マウス エミュレーター」は、USB キーボードおよび USB マウスとして動作する端末です。一般的なキーボードやマウスとの違い、プログラムによってキー入力やマウス操作を制御できます。

そのため、操作の自動化や、条件によってのキー入力などをプログラムによって実現できるようになります。

https://sites.google.com/site/ichiworkspace/%E3%83%9B%E3%83%BC%E3%83%A0/%E3%81%BF%E3%82%93%E3%81%AA%E3%81%AE%E3%83%A9%E3%83%9C/%E3%82%AD%E3%83%BC%E3%83%9C%E3%83%BC%E3%83%89%E3%83%9E%E3%82%A6%E3%82%B9%E3%82%A8%E3%83%9F%E3%83%A5%E3%83%AC%E3%83%BC%E3%82%BF

https://www.marutsu.co.jp/pc/i/2712062/


制御側が microUSB、使用側が USB-A の端子になっています。

今回の場合、macOS から操作して、他デバイスの外付けキーボードとして制御したいので、下記の接続になります。

* macOS と microUSB を接続する
* 他デバイスと USB-A を接続する

### デバイスの解説書およびサンプルコードと仕様書

デバイスの制作者の方が、解説書にくわえてサンプルコードと仕様書を提供してくださっておりとても参考になります。

https://techbookfest.org/product/iaTanH0UsU9j5TPnFT44rF?productVariantID=4Q1yNxZMFWWs9UJbkx7c6b

https://drive.google.com/file/d/17Dn9tl1YqW_iVWj6vO8monKASKgg6fJ2/view

### デバイスの構成 (参考)

デバイスには 2 つのチップが使われていました。

* CH340: USB でシリアル通信を行うチップ (microUSB 側)
* CH9329: USB HID デバイスとして動作し、シリアル通信で制御を受け付ける (USB-A 側)


## macOS の Python で操作する

Python で書かれたサンプルコードを macOS で動作させるには若干の変更が必要でした。この記事の執筆時点での環境は次の通りです。

* macOS 14.4.1 (Sonoma)
* Python 3.11.4

### pyserial をインストールする

サンプルコードでは `serial` をインポートしています。

```python
import sys,time,serial
```

そのため、macOS では `pyserial` を追加でインストールします。

```shell
python3 -m pip install pyserial
```

:::message
新たに `pip install` をする場合は、`venv` による仮想環境を作成すること推奨されています。

https://packaging.python.org/ja/latest/guides/installing-using-pip-and-virtual-environments/
:::

### デバイス ID の指定

サンプルコードでは後半部分 176 行目で、デバイス ID として `COM24` を指定しています。

```python
drv=CH9329('COM24',9600,1920,1080)
```

macOS では `/dev/tty.usbserial-1234567` という形式で指定します。`1234567` の部分は環境によって異なりますので、 `ls` などで確認してください。

```shell
ls /dev/tty.usbserial-*
```

```python
drv=CH9329('/dev/tty.usbserial-1234567',9600,1920,1080)  # COM24 から書き換える
```

### 制御コードを送信する

サンプルコード内では、制御コードを送信する部分はコメントアウトされています。適宜コメントを外せば、該当する制御コードを送信できます。

```python
drv.print('#Abc')  # ’#Abc' の4文字をキー入力として送信する
# drv.write('#')
# drv.push(0x02,0x04)
# drv.moveabs(100,100)
# drv.moveabs(968,500)
# ...
```

これで macOS から「キーボード／マウス エミュレーター」の操作を確認できます。

さらなる操作については、サンプルコードや仕様書が参考になります。


## まとめ

キーボードやマウスをプログラムで制御できるようになると、マクロパッドや手順の自動化などで便利に使えるようになります。

まずはサンプルコードからはじめて、いろいろな面白いデバイスに発展していけたらいいですね。
