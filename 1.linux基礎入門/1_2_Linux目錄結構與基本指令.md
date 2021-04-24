# 目錄結構
## windows 作業系統目錄結構
```
Windows 作業系統目錄結構==> 有 C: D:

   目錄 C:\Windows\System32 ==>  有許多檔案與子目錄  
   ==> 點選  diskmgmt ==> 開啟 【磁碟管理】 
   ==> 點選  compmgmt ==> 開啟 【電腦管理】    
   
   calc
   notepad
   winword
```
## Linux 作業系統目錄結構 
```
沒有 C: D:

最上層目錄 /
          /etc  ==> 主機或系統配置文件或設定檔絕大部分都在此目錄
          /bin
          /root ==> 最高權限使用者(管理者)登入時的目錄
          /home ==> 一般使用者登入時的目錄
          /home/ksu ==> ksu使用者登入時的目錄
          
```
# lab實作:目錄存取常用指令(linux command)
```
pwd ==>  顯示目前的工作目錄位置(Print Working Directory)

cd ==> 用來變換工作目錄的指令(Change Directory)
cd ==> 回到使用者目錄
cd .. ==> 回到上層目錄
cd /bin ==> 切竄到/bin 目錄

ls ==> 列出目前目錄中的檔案與目錄列表

cat ==> (1)印出檔案內容 (2)合併多檔(concatenate）
  cat flag
  cat /etc/passwd
```
```
試輸入底下指令與參數 看看結果有何不同
ls
ls -l   <== 注意:有空格  顯示檔案與目錄的詳細資訊
ls -a    <== 注意:大小寫有區別(Case-sensitive) -a 參數可以顯示隱藏的檔案與目錄
ls -A

可以把兩個參數合在一起
ls -Al

梗多說明請參看
https://blog.gtwang.org/linux/linux-ls-command-tutorial/
```
## 指令語法與參數
```
pwd 的語法:  pwd [OPTION]

參數[OPTION]：
-L 如果當前目錄為連結檔, 會顯示連結檔名稱。
-P: 如果當前目錄為連結檔, 不會以連結檔的路徑來顯示, 會顯示實際的目錄位置。
–help: 顯示幫忙訊息。
–version: 顯示 pwd 版本。
```
## 查閱指令參數小撇步
```
1.直接在terminal 查 
    ls -h
    ls --h
    ls -help
    ls --help
    
2.上網google ==> linux ls

3.man ls
```
# 完成linux-101 ==> linux-1 與linux-2

### 補充資料(學生自行練習) cat ==>  (2)合併多檔(concatenate）
```
把 textfile1 的檔案內容加上行號後輸入 textfile2 這個檔案裡
cat -n textfile1 > textfile2
　　
把 textfile1 和 textfile2 的檔案內容加上行號（空白行不加）之後將內容附加到 textfile3 裡。
　　 cat -b textfile1 textfile2 >> textfile3
　　
清空/etc/test.txt檔案內容 ==>   cat /dev/null > /etc/test.txt 
```
