# Linux C 程式的編譯與運行:
## 範例
```
// helloCTFer.c
#include <stdio.h>

int main()
{
   printf("Hello CTFer\n ”);
   return 0;
}
```
## 
```
(1)編譯
   ==> gcc helloCTFer.c  ==>  產生a.out執行檔   
   ==> gcc helloCTFer.c -o helloCTFer ==>  產生helloCTFer執行檔
   ==> gcc helloCTFer.c -o helloCTFer.exe ==>  產生helloCTFer.exe執行檔{故意使用windows 執行檔副檔名}

(2)執行
    ==> ./a.out
    ==> ./helloCTFer
    ==> ./helloCTFer.exe
    
 (3)檢查執行檔檔案格式
    ==> file ./a.out
    ==> file ./helloCTFer
    ==> file ./helloCTFer.exe ==>  特別注意{故意使用windows 執行檔副檔名}
  
  (4)使用hexdump檢查檔案特徵格式
       hexdump ./helloCTFer | head
       
  strings ./a.out
```
# 挑選 linuxC範例程式 數題 練習

# gcc 常用編譯技術{待補充}
```
gcc -g helloCTFer.c -o helloCTFer 

官方網址 https://gcc.gnu.org/
```

