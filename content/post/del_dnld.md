---
title: "ダウンロードフォルダ内自動削除"
date: 2018-04-04T16:27:09+09:00
draft: false
categories: "windows"
---

Windows のダウンロードフォルダは、不要になったファイルや容量の大きなファイルがたまりがちです。  
そこで、起動時に5日より前にダウンロードしたファイルを自動削除するバッチファイル del_dnld.bat を用意しました。

[こちらの記事](https://aitoyozn.net/2015/07/post-653/) を参考にしました。

```bash
@echo off
forfiles /p "%USERPROFILE%\Downloads" /D -5 /c "cmd /c del /F /S /Q @file"
forfiles /p "%USERPROFILE%\Downloads" /D -5 /c "cmd /c IF @isdir==TRUE rmdir /S /Q @file"
```

参考元のスクリプトだとフォルダは削除対象外だったので、フォルダも削除されるよう追記してみました。

このバッチファイルが起動時に実行されるよう、スタートアップに登録します。  
Windows 10 のスタートアップフォルダは以下なので、del_dnld.bat をここに入れます。
```text
C:\Users\<ユーザ名>\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup
```

これで、ダウンロードフォルダはいつでもすっきりですね🌸