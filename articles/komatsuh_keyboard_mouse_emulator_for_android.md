---
title: "キーボード／マウス エミュレーターを Android で操作する"
emoji: "🎛️"
type: "tech"
topics:
  - "keyboard"
  - "USB"
  - "Android"
published: true
published_at: "2024-05-12 23:30"
---

初稿: 2024-05-12
小松弘幸 ([@komatsuh:bsky](https://bsky.app/profile/komatsuh.bsky.social), [@komatsuh:twitter](https://twitter.com/komatsuh))

「キーボード／マウス エミュレーター」というデバイスを Android (Kotlin) で動作させる方法のメモです。

## キーボード／マウス エミュレーター

(この章は [キーボード／マウス エミュレーターを macOS で操作する](https://zenn.dev/komatsuh/articles/komatsuh_keyboard_mouse_emulator_for_macos) と同じ内容です)

「キーボード／マウス エミュレーター」は、USB キーボードおよび USB マウスとして動作する端末です。一般的なキーボードやマウスとの違い、プログラムによってキー入力やマウス操作を制御できます。

そのため、操作の自動化や、条件によってのキー入力などをプログラムによって実現できるようになります。

https://sites.google.com/site/ichiworkspace/%E3%83%9B%E3%83%BC%E3%83%A0/%E3%81%BF%E3%82%93%E3%81%AA%E3%81%AE%E3%83%A9%E3%83%9C/%E3%82%AD%E3%83%BC%E3%83%9C%E3%83%BC%E3%83%89%E3%83%9E%E3%82%A6%E3%82%B9%E3%82%A8%E3%83%9F%E3%83%A5%E3%83%AC%E3%83%BC%E3%82%BF

https://www.marutsu.co.jp/pc/i/2712062/


制御側が microUSB、キーボード側が USB-A の端子になっています。

今回の場合、Android から操作して、他デバイスの外付けキーボードとして制御したいので、下記の接続になります。

* Android と microUSB を接続する
* 他デバイスと USB-A を接続する

### デバイスの解説書およびサンプルコードと仕様書

デバイスの制作者の方が、解説書にくわえてサンプルコードと仕様書を提供してくださっておりとても参考になります。

https://techbookfest.org/product/iaTanH0UsU9j5TPnFT44rF?productVariantID=4Q1yNxZMFWWs9UJbkx7c6b

https://drive.google.com/file/d/17Dn9tl1YqW_iVWj6vO8monKASKgg6fJ2/view

### デバイスの構成 (参考)

デバイスには 2 つのチップが使われていました。

* CH340: USB でシリアル通信を行うチップ (microUSB 側)
* CH9329: USB HID デバイスとして動作し、シリアル通信で制御を受け付ける (USB-A 側)

USB デバイスとしての Vendor-ID と Product-ID は次の通りでした。

* Vendor ID: 0x1A86
* Product ID: 0x7523


## Android での制御

実装はおおまかに2つの項目に分割できます。

* Android での USB によるシリアル通信
* シリアル通信を介した制御コードの送受信

### Android での USB によるシリアル通信

Android では USB で接続した機器と、シリアル通信でやりとりできます。
今回は `usb-serial-for-android` というライブラリを活用して、シリアル通信を実装します。

シリアル通信の方法は機器側のチップによって異なります。このライブラリはチップごと違いを吸収して統一的な操作方法も提供しています。

https://github.com/mik3y/usb-serial-for-android

:::message
* Android でも機種によっては USB によるシリアル通信に対応していないものもあります。
* iOS では USB によるシリアル通信には対応していないようです。 (2024-05-12 現在)
:::

#### `usb-serial-for-android` の設定 (Kotlin 用)

`usb-serial-for-android` の (Quick Start)[https://github.com/mik3y/usb-serial-for-android?tab=readme-ov-file#quick-start] に設定方法が詳しく記載されていますが、これは Java 用です。

Kotlin の場合は、以下の 3 つファイルを変更します。

* settings.gradle.kts
* gradle/libs.versions.toml
* app/build.gradle.kts

```kt:settings.gradle.kts
dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
    repositories {
        google()
        mavenCentral()
        maven(url = "https://jitpack.io")  // "jitpack.io" を追加
    }
}
```

```toml:gradle/libs.versions.toml
[versions]
# usbSerial を追加
usbSerial = "3.7.0"
agp = "8.3.1"
...

[libraries]
# usbSerial を追加
usbSerial = { module = "com.github.mik3y:usb-serial-for-android", version.ref = "usbSerial" }
androidx-core-ktx = { group = "androidx.core", name = "core-ktx", version.ref = "coreKtx" }
...
```

```kt:app/build.gradle.kts
dependencies {
    implementation(libs.usbSerial)  // libs.usbSerial を追加
    implementation(libs.androidx.core.ktx)
    ...
}
```

#### デバイス接続時に自動起動する設定

`AndroidManifest.xml` と `device_filter.xml` を設定すると、デバイスを接続した時に自動的にアプリケーションを起動できるようなります。パーミッションの取得もあわせて行われるようです。

```xml:app/src/main/AndroidManifest.xml
<activity
    android:name="..."
    ...>
    <intent-filter>...</intenfilter>
    <!-- ここから -->
    <intent-filter>
        <action android:name="android.hardware.usb.action.USB_DEVICE_ATTACHED" />
    </intent-filter>
    <meta-data
        android:name="android.hardware.usb.action.USB_DEVICE_ATTACHED"
        android:resource="@xml/device_filter" />
    <!-- ここまで -->
</activity>
```

```xml:app/src/main/res/xml/device_filter.xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <usb-device vendor-id="0x1A86" product-id="0x7523" />
</resources>
```

#### USB デバイスとの接続

`usb-serial-for-android` の (Quick Start)[https://github.com/mik3y/usb-serial-for-android?tab=readme-ov-file#quick-start] に書かれている Java のサンプルコードを Kotlin 用に変更すると以下のような感じになります。

VENDOR_ID や BAUD_RATE などは接続するデバイスの仕様に従います。

```kt
const val VENDOR_ID: Int = 0x1A86
const val PRODUCT_ID: Int = 0x7523
const val BAUD_RATE: Int = 9600
const val DATA_BITS: Int = 8

manager : UsbManager = getSystemService(Context.USB_SERVICE) as UsbManager

var driver: UsbSerialDriver? = null
for (candidate in UsbSerialProber.getDefaultProber().findAllDrivers(manager)) {
    val device: UsbDevice = candidate.device
        if (device.vendorId == VENDOR_ID && device.productId == PRODUCT_ID) {
        driver = candidate
    }
}

if (driver == null || !manager.hasPermission(driver.device)) {
    // No valid device
    return
}

val connection = manager.openDevice(driver.device)
if (connection == null) {
    // No connection
    return
}

val port = driver.ports[0]
port.open(connection)

port.setParameters(BAUD_RATE, DATA_BITS, UsbSerialPort.STOPBITS_1, UsbSerialPort.PARITY_NONE)
```

これでシリアル通信をする準備ができました。`port.write` と `port.read` でデータの送受信ができます.

```kt
const val WRITE_WAIT_MILLIS: Int = 20
const val READ_WAIT_MILLIS: Int = 20

val packet = byteArrayOf(0x01, 0x02, 0x03)
port.write(packet, WRITE_WAIT_MILLIS)

val readBuffer = ByteArray(size = 16)
val readLength = port.read(readBuffer, READ_WAIT_MILLIS)
```

### シリアル通信を介した制御コードの送受信

いよいよシリアル通信によって、キーボードとマウスのエミュレーションを行います。実装としては CH9329 というチップ用の制御コードを送受信することで実現します。

#### CH9329 への送受信の概要

CH9329 の制御は、下記のフォーマットのパケットを送受信することで行います。

| ヘッダ + アドレス | コマンド | データ長 | データ      | チェックサム |
| -------------- | ------- | ------- | ---------- | --------- |
| 0x57 0xAB 0x00 | 1 バイト | 1 バイト | 0-64 バイト | 1 バイト   |

* ヘッダ + アドレス: 0x57 0xAB 0x00 で固定です
* コマンド: キーボードやマウスなどのイベントの分類
* チェックサム: 全データ合計値を 0xFF でマスクした値

:::message
CH9329 の仕様では、アドレスを示す 0x00 は別の値を使うことも可能です。詳しくは、解説書や仕様書を参照してください。
:::

#### マウスカーソル操作の制御コード送受信

マウスを右に 100 ピクセル、上に 50 ピクセル移動させる場合、次のパケットを送信します。

| ヘッダ + アドレス | コマンド | データ長 | データ                    | チェックサム |
| -------------- | ------- | ------- | ------------------------ | --------- |
| 0x57 0xAB 0x00 | 0x05    | 0x05    | 0x01 0x00 0x64 0xCE 0x00 | 0x3F     |

コマンドの 0x05 がマウス操作を意味します。

データの 3 番目の 0x64 (= 100) が右に 100 ピクセル、4 番目の 0xCE (= -50) が上に 50 ピクセルを意味します。

チェックサムは、チェックサムまでの値の合計値 (0x23F) と 0xFF をマスクした値です。

Kotlin では次のようなコードになります。

```kt
val packet = byteArrayOf(
            0x57,
            0xAB.toByte(),
            0x00,
            0x05,  // CMD_SEND_MS_REL_DATA
            0x05,  // Length of data
            0x01,  // Always 0x01
            0x00,
            0x64,  // Delta of X
            0xCE.toByte(),  // Delta of Y
            0x00,
            0x3F,  // Check sum: Sum of bytes (mod 0xFF)
        )
port.write(packet, WRITE_WAIT_MILLIS)
```

`byteArrayOf` のデータで `0x80` 以上の値には `toByte()` を付与する必要があります。これは Kotlin の Byte 型には符号があり、0 〜 255 ではなく -128 〜 127 が値の範囲だからです。

:::message
Kotlin 1.5 からは符号のない UByte 型もありますが、`use-serial-for-android` は Byte 型のみを受け付けます。
:::

上記のパケットを送信したのち、今度は返信用のパケットを受信します。

| ヘッダ + アドレス | コマンド | データ長 | データ   | チェックサム |
| -------------- | ------- | ------- | ------- | --------- |
| 0x57 0xAB 0x00 | 0x85    | 0x01    | 1 バイト | 1 バイト   |

データの 1 バイトが 0x00 であれば送信に成功しています。失敗の場合は理由に応じて 0xE1 〜 0xE6 の値が返ります。詳しくは仕様書を参照してください。

```kt
val readBuffer = ByteArray(size = 16)
val readLength = port.read(readBuffer, READ_WAIT_MILLIS)
```

#### マウスクリック操作の制御コード送受信

マウスの左クリックをする場合、次の 2 つのパケットを送信します。

| ヘッダ + アドレス | コマンド | データ長 | データ                    | チェックサム |
| -------------- | ------- | ------- | ------------------------ | --------- |
| 0x57 0xAB 0x00 | 0x05    | 0x05    | 0x01 0x01 0x00 0x00 0x00 | 0x0E      |

| ヘッダ + アドレス | コマンド | データ長 | データ                    | チェックサム |
| -------------- | ------- | ------- | ------------------------ | --------- |
| 0x57 0xAB 0x00 | 0x05    | 0x05    | 0x01 0x00 0x00 0x00 0x00 | 0x0D      |

1 番目のパケットが down イベントで、2 番目のパケットが up イベントです。2 番目のパケットを送信しないと、押したままの状態になります。

データの 2 番目がクリックのボタンを意味しています。左ボタンが 0x01, 右ボタンが 0x02, 中ボタンが 0x04 です。

送受信をあわせると、次のようなコードになります。

```kt
val packetDown = byteArrayOf(
            0x57,
            0xAB.toByte(),
            0x00,
            0x05,  // CMD_SEND_MS_REL_DATA
            0x05,  // Length of data
            0x01,  // Always 0x01
            0x01,  // [0..0, mid_btn, r_btn, l_btn]
            0x00,  // Delta of X
            0x00,  // Delta of Y
            0x00,  // Delta of wheel
            0x0E,  // Check sum: Sum of bytes (mod 0xFF)
        )
port.write(packetDown, WRITE_WAIT_MILLIS)

val readBuffer = ByteArray(size = 16)
val readLength = port.read(readBuffer, READ_WAIT_MILLIS)

val packetUp = byteArrayOf(
            0x57,
            0xAB.toByte(),
            0x00,
            0x05,  // CMD_SEND_MS_REL_DATA
            0x05,  // Length of data
            0x01,  // Always 0x01
            0x00,  // [0..0, mid_btn, r_btn, l_btn]
            0x00,  // Delta of X
            0x00,  // Delta of Y
            0x00,  // Delta of wheel
            0x0D,  // Check sum: Sum of bytes (mod 0xFF)
        )
port.write(packetUp, WRITE_WAIT_MILLIS)

val readBuffer2 = ByteArray(size = 16)
val readLength2 = port.read(readBuffer2, READ_WAIT_MILLIS)
```

カーソルの移動とクリックのイベントを同じパケットであわせて送るとマウスドラッグの操作になります。

また、データの 5 番目はホイールの操作です。

#### キー入力の制御コード送受信

キー入力 `a` を送信する場合、次の 2 つのパケットを送信します。マウスクリックと同様に down と up それぞれのイベントです。

| ヘッダ + アドレス | コマンド | データ長 | データ                                   | チェックサム |
| -------------- | ------- | ------- | --------------------------------------- | --------- |
| 0x57 0xAB 0x00 | 0x02    | 0x08    | 0x00 0x00 0x04 0x00 0x00 0x00 0x00 0x00 | 0x10      |

| ヘッダ + アドレス | コマンド | データ長 | データ                                   | チェックサム |
| -------------- | ------- | ------- | --------------------------------------- | --------- |
| 0x57 0xAB 0x00 | 0x02    | 0x08    | 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 | 0x0C      |

Kotlin のコードは、マウスのクリックイベントと同様ですので省略します。

キー入力では 8 バイト分のデータを送信します。

1 番目のバイトは、Shift などのモディファイアキーを意味します。それぞれのビットが次の対応を取ります。

| 7     | 6    | 5       | 4      | 3    | 2     | 1       | 0     |
| ----  | ---- | ------- | ------ | ---- | ----- | ------- | ----- |
| 右Win | 右Alt | 右Shift | 右Ctrl | 左Win | 左Alt | 左Shift | 左Ctrl |

2 番目のバイトは、常に 0x00 です。

3 番目から 8 番目までは、入力するキーを意味します。つまり 6 キーまで同時に入力することができます。

値は USB HID のキーコードです。例えば `a` なら 0x04, `F1` なら 0x3A です。

https://www.usb.org/sites/default/files/documents/hut1_12v2.pdf#page=53

たとえば、左Ctrl + 左Shift + a を表すデータは `0x03 0x00 0x04 0x00 0x00 0x00 0x00 0x00` となります。

また、`a` `s` `d` を同時に押すデータは `0x00 0x00 0x04 0x16 0x07 0x00 0x00 0x00` になります。

## おわりに

Android をキーボードやマウスとして操作できるようになると、マクロパッドやトラックパッドとして活用できます。使用状況に応じて好みのレイアウトにできるのが魅力です。また、Android 端末のタッチパッドの精度を活用できますし、各種センサーや他のアプリケーションとの連携など活躍の幅が広がるのではと思います。

作成したデモアプリを、天下一キーボードわいわい会 Vol.6 というイベントに展示していました。ざんねんながら機材トラブルに見舞われてしまったのですが、試していただいたりフィードバックをくださった方々ありがとうございました。

https://bsky.app/profile/komatsuh.bsky.social/post/3krlp5xvcqs2t
https://bsky.app/profile/komatsuh.bsky.social/post/3krocv3s4ll2r
