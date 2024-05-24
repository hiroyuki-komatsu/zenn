---
title: "macOS 上の Qt のビルドで .syncqt_staging のコピーがエラーなる場合の対応方法"
emoji: "🥷"
type: "tech"
topics:
  - "Qt"
  - "macOS"
  - "ninja"
published: true
published_at: "2024-05-24 22:40"
---
結論: macOS での Qt のビルドには Ninja が必要です。

macOS 上で Qt をビルドした際に、次のようなエラーによって失敗しました。

```
[  0%] Generating ../../mkspecs/modules/qt_lib_printsupport_private.pri
Error copying directory from "/tmp/qt/include/QtGui/.syncqt_staging" to "/tmp/qt/lib/QtGui.framework/Versions/A/Headers".
make[2]: *** [src/gui/CMakeFiles/Gui_copy_fw_sync_headers] Error 1
make[1]: *** [src/gui/CMakeFiles/Gui_copy_fw_sync_headers.dir/all] Error 2
Error copying directory from "/tmp/qt/include/QtPrintSupport/.syncqt_staging" to "/tmp/qt/lib/QtPrintSupport.framework/Versions/A/Headers".
[  0%] Building CXX object src/tools/syncqt/CMakeFiles/syncqt.dir/main.cpp.o
make[2]: *** [src/printsupport/CMakeFiles/PrintSupport_copy_fw_sync_headers] Error 1
make[1]: *** [src/printsupport/CMakeFiles/PrintSupport_copy_fw_sync_headers.dir/all] Error 2
Error copying directory from "/tmp/qt/include/QtWidgets/.syncqt_staging" to "/tmp/qt/lib/QtWidgets.framework/Versions/A/Headers".
make[2]: *** [src/widgets/CMakeFiles/Widgets_copy_fw_sync_headers] Error 1
[  0%] Built target Core_lib_pri
make[1]: *** [src/widgets/CMakeFiles/Widgets_copy_fw_sync_headers.dir/all] Error 2
```

`.syncqt_staging` というディレクトリーのコピーに失敗しているようです。

このエラーメッセージから推測するのは難しいのですが、この問題は Ninja というビルドツールがインストールされていないことが原因です。

Ninja をインストールすると期待通りビルドできるようになります。
https://github.com/ninja-build/ninja/releases/

答えが分かった上で Qt のビルドエラーを再確認すると、下記の表記が手がかりだということが分かりました。

```
CMake Warning at cmake/QtBuildHelpers.cmake:12 (message):
  The officially supported CMake generator for building Qt is Ninja / Ninja
  Multi-Config.  You are using: 'Unix Makefiles' instead.  Thus, you might
  encounter issues.  Use at your own risk.
```
