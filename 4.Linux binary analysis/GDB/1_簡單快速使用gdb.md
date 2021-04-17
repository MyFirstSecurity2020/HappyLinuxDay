# 範例程式
```
#include <stdio.h>

int func(int n)
{
   int sum =0,i;
   
   for( i=1;i<=n; i++)
      sum +=1 ;
   
   return sum;
}

int main(void)
{
  int L;
  long result = 0;
  
  for(int i=1; i<=100; i++)
     result += i;

   printf("result[1-100] = %d \n", result);  
   printf("result[1-250] = %d \n", func(250));
   
   return 0;
}
```
# 編譯 要加 -g參數
```
gcc -g test1.c -o test1
```
# 啟用gdb簡單分析
```
gdb ./test1


GNU gdb (Debian 8.2.1-2) 8.2.1
Copyright (C) 2018 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
Type "show copying" and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
    <http://www.gnu.org/software/gdb/documentation/>.

For help, type "help".
Type "apropos word" to search for commands related to "word"...
Reading symbols from ./test1...done.

//不帶參數的list 指令
(gdb) list


//帶一個參數的list 指令
//顯示參數行之前和之後的10 行內容
(gdb) list 10  

//帶兩個參數的list 指令
//顯示原始檔案從一行到另一行其中的所有內容
(gdb) list 2,6


(gdb) help

(gdb) help all

//離開
(gdb) q
```
