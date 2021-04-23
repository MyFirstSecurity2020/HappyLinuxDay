# Steg-101
```
CSAW QUALS 2015: keep-calm-and-ctf(必)50
```
[檔案下載處 metadata圖片隱寫術](https://raw.githubusercontent.com/MyFirstSecurity2020/backup/main/steg/steg102/img.jpg)
# 參考解題步驟
```
解題步驟1:查看檔案格式
   file /root/Desktop/img.jpg
```

# 解題步驟2:查看檔案內藏的字串
```
strings /root/Desktop/img.jpg
```

# 解題步驟3:安裝工具並學習使用技術
```
google搜尋jpg metadata linux

看看怎麼用 ==>
http://xahlee.info/img/metadata_in_image_files.html
http://libre-software.net/edit-image-metadata-on-linux/

安裝工具 ==> sudo apt-get install exiftool

```
# 解題步驟4:查看檔案並讀出答案
```
exiftool img.jpg  ==>即可讀出答案
```
