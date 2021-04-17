# 0-1.EasyCTF_hexedit 解題
### 題目敘述
```
flag 格式為 easyctf{...}

附件：hexedit
```
### 解答
0. 下載檔案

1. 先查看一下檔案是什麼類型：使用file指令```file --help```
```
$ file hexedit

hexedit: ELF 64-bit LSB executable, <==  檔案是一個ELF(Executable and Linkable Format)可執行檔
x86-64, version 1 (SYSV), dynamically linked, 
interpreter /lib64/ld-linux-x86-64.so.2, 
for GNU/Linux 2.6.24,   BuildID[sha1]=be7897ed315b5c5a619013ec7c84c47a5278c9ee, 
not stripped
```
2. 查看檔案權限：使用ls指令```ls --help```
```
ls -a會顯示隱藏檔
ls -l會顯示詳細檔案
ls -al顯示所有檔案的詳細資料
```
```
$ ls -all
total 20
drwxr-xr-x  2 user user 4096  十  21 20:21 .
drwxr-xr-x 17 user user 4096  十  21 20:31 ..
-rw-r--r--  1 user user 8566  六  29 01:58 hexedit
   
-rw-r--r--  <- 發現只有可讀(r)可寫(w)權限，缺少可執行(x)權限   
```
3. 修改檔案權限：使用chmod指令```chmod --help```
```   
$ chmod +x hexedit  <- 將hexedit檔案加上可執行(x)權限
   
$ ls -all      <- 再次查看檔案權限
drwxr-xr-x  2 user user 4096  十  21 20:21 .
drwxr-xr-x 17 user user 4096  十  21 20:31 ..
-rwxr-xr-x  1 user user 8566  六  29 01:58 hexedit
   
-rwxr-xr-x  <- 已經有可讀(r)可寫(w)可執行(x)的權限了  
```
4. 執行程式看看執行結果
```
$ ./hexedit
Find the flag!
   
執行後只出現一行文字Find the flag!
```
5. Reverse起手式：查看檔案中的所有可視字元：使用strings指令```strings --help```
```   
$ strings hexedit
   
[]A\A]A^A_
Find the flag!
;*3$"
easyctf{????????}        <- 在開頭不遠處就可以找到flag！
GCC: (Ubuntu 4.8.4-2ubuntu1~14.04.3) 4.8.4
```
