#
```

```

# Linux 101-Linux CTF 3
```
你知道如何 在Linux上做hex to string嗎?

提示 : 檔案位置 /home/lab/hex.txt
```
### 解題思維
```
hex to string ==>  ?
              ==> 就是 ASCII code

http://www.tutorialspoint.com/unix_commands/xxd.htm
https://linux.die.net/man/1/xxd
```
### 解法一:使用線上工具 直接解
```
Google 一下 hex to string ==> 找線上工具 直接解
```
### 解法二:使用linux指令解題
```
列出當前檔案與目錄==> ls

檢視hex.txt檔案內容==>cat hex.txt

使用xxd工具將hex.txt的16進位內容轉換為字串==>xxd -r -p hex.txt
```
### 解法三:開發python程式解題  see HappyPythonDay 

# Linux 101-Linux CTF 4
```
你知道如何 在Linux上做base64 解碼嗎?

提示 : 檔案位置 /home/lab/base64.txt
```
### 解法一:使用線上工具 直接解
```
列出當前檔案與目錄==> ls

檢視base64.txt檔案內容 ==> cat base64.txt

Google 一下base64  decoder==> 找線上工具 直接解
```
### 解法二:使用linux指令解題
```
https://linux.die.net/man/1/base64

列出當前檔案與目錄==> ls

檢視base64.txt檔案內容 ==> cat base64.txt

使用base64工具將base64.txt的內容解碼==>base64 -d base64.txt
```
### 解法三:開發python程式解題  see HappyPythonDay 
