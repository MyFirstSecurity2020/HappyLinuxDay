# Steg-101
```
CSAW QUALS 2015: keep-calm-and-ctf(必)50
```
[檔案下載處 metadata圖片隱寫術](https://raw.githubusercontent.com/MyFirstSecurity2020/backup/main/steg/steg102/img.jpg)
# 參考解題步驟
## 解題步驟1:查看檔案格式
```

   file /root/Desktop/img.jpg
```

## 解題步驟2:查看檔案內藏的字串
```
strings /root/Desktop/img.jpg
```

## 解題步驟3:安裝工具並學習使用技術
```
google搜尋jpg metadata linux

看看怎麼用 ==>
http://xahlee.info/img/metadata_in_image_files.html
http://libre-software.net/edit-image-metadata-on-linux/

安裝工具 ==> sudo apt-get install exiftool

```
## 解題步驟4:查看檔案並讀出答案
```
exiftool img.jpg  ==>即可讀出答案
```
# 作業
```
上網找資料學習ImageMagick的技巧 試看看用此工具解此題
http://xahlee.info/img/imagemagic.html
```
# metadata ==> 關於資料 的 資料（data-about-data）
```
https://zh.wikipedia.org/wiki/元資料

1969年，由Jack E. Myers所提出的.metadata即關於資料的資料（data-about-data），
可以說是一種標準，是為支援互通性的資料描述，所取得一致的準則
```
# 解析 圖片 元資料 的 ExifTool
```
https://zh.wikipedia.org/wiki/ExifTool

ExifTool是Phil Harvey以Perl寫成的免費開源軟體，可讀寫及處理圖像、視頻及音頻的metadata，
例如Exif、IPTC、XMP、JFIF、GeoTIFF、ICC Profile。
它是跨平台的，可作為命令列(我們上課用的)或Perl函式庫使用。

==>官方網址  https://exiftool.org/
            https://github.com/exiftool/exiftool
            https://zh.wikipedia.org/wiki/ExifTool
```
