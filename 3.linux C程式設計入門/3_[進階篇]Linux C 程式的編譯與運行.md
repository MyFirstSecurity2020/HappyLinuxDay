# Linux C 程式的編譯與運行:

```
Program Lifetime Stages 編譯的各階段(編譯器 如何將 原始C程式 變成 執行檔)
Program Execution Stages 執行的各階段(作業系統 如何載入執行檔 使其執行)[略!]
```
```
本單元相對艱深
學生可先熟悉指令運用及結果展現
日後在閱讀底下書籍的內容
```
# 推薦閱讀
```
 Advanced C and C++ Compiling by Milan Stevanovic (Apress, 2014).
 https://github.com/Apress/adv-c-cpp-compiling
 
簡體中譯  高級C/C++編譯技術 （美）斯特瓦諾維奇
機械工業出版社  2015/04/01
 
 先看 
 第2章 程序生命周期階段基礎
 第3章 加載程序執行階段
```
### 程式範例
```
// helloCTFer.c
#include <stdio.h>

int main()
{
   printf("Hello CTFer\n ”);
   return 0;
}
```
```
編譯的各階段
 原始程式碼 helloCTFer.c
 1.預處理(Preprocessing) ===> gcc –E helloCTFer.c –o helloCTFer.i    ===> 查看.i的架構
 2.編譯(Assembling) ===> gcc –S helloCTFer.i  -o helloCTFer.s   ===> 查看.s的架構
 3.彙編(Compiling) ===> gcc -c helloCTFer.s -o helloCTFer.o ===> 查看.o的架構
 4.連結(Linking) ===> gcc  helloCTFer.o -o helloCTFer  ===> 查看helloCTFer的架構
```
### 1_預處理|前置處理 (preprocess)
```
 預處理|前置處理 (preprocess)===> 
 將原始程式檔hello.c 和相關的標頭檔(如stdio.h)等被前編譯器cpp 編譯成一個.i 檔案
                                      C 前置處理器(cpp, C Preprocessor)
```
```
gcc –E helloCTFer.c –o helloCTFer.i
```
```
 ls -al helloCTFer.*
 
-rw-rw-r-- 1 ksu ksu    76  三   5 01:23 helloCTFer.c
-rwxrwxr-x 1 ksu ksu  7352  三   5 01:32 helloCTFer.exe
-rw-rw-r-- 1 ksu ksu 17541  三   5 01:59 helloCTFer.i
```
```
前編譯過程主要處理那些原始程式檔中以“＃”開始的前編譯指令。比如此＃include”、“＃define”等

主要處理規則如下： 
1.將所有的“＃define＂刪除，並且展開所有的巨集定義。
2.處理所有條件前編譯指令，比如＂＃if＇、“＃ifdef＂、“＃elif＇、“＃else’，、“＃endif’。
3.處理“＃include”前編譯指令，將包含的檔案插入到該前編譯指令的位置。
  注意，這個過程是遞迴進行的，也就是說包含的檔案可能還包含其他檔。
4.刪除所有的註解"//"和"／*    *／" 
5.添加行號和檔案名稱標誌，比如＃2 “hello.c” 2 ，以便於編譯時編譯器產生除錯用的行號資訊，
   及用於編譯時產生編譯錯誤或警告時能揖顯示行號
6.保留所有的＃pragma 編譯器指令，因為編譯器需要使用它們。
```
```
cat helloCTFer.i


# 1 "helloCTFer.c"
# 1 "<built-in>"
# 1 "<command-line>"
# 1 "/usr/include/stdc-predef.h" 1 3 4
# 1 "<command-line>" 2
# 1 "helloCTFer.c"
# 1 "/usr/include/stdio.h" 1 3 4
# 27 "/usr/include/stdio.h" 3 4
# 1 "/usr/include/features.h" 1 3 4
# 367 "/usr/include/features.h" 3 4
# 1 "/usr/include/i386-linux-gnu/sys/cdefs.h" 1 3 4
# 410 "/usr/include/i386-linux-gnu/sys/cdefs.h" 3 4
# 1 "/usr/include/i386-linux-gnu/bits/wordsize.h" 1 3 4
# 411 "/usr/include/i386-linux-gnu/sys/cdefs.h" 2 3 4
# 368 "/usr/include/features.h" 2 3 4
# 391 "/usr/include/features.h" 3 4
# 1 "/usr/include/i386-linux-gnu/gnu/stubs.h" 1 3 4

# 1 "/usr/include/i386-linux-gnu/gnu/stubs-32.h" 1 3 4
# 8 "/usr/include/i386-linux-gnu/gnu/stubs.h" 2 3 4
# 392 "/usr/include/features.h" 2 3 4
# 28 "/usr/include/stdio.h" 2 3 4

# 1 "/usr/lib/gcc/i686-linux-gnu/5/include/stddef.h" 1 3 4
# 216 "/usr/lib/gcc/i686-linux-gnu/5/include/stddef.h" 3 4

 .............................
# 2 "helloCTFer.c" 2

# 3 "helloCTFer.c"
int main()
{
   printf("Hello CTFer\n");
   return 0;
}
```

### 2.編譯(Assembling)
```
把前置處理完的檔案進行一系列的 詞法分析、語法分析、語意分析及最佳化接產生相應的 組合語言程式碼

請上大學後再修 編譯原理 課程

產出 ==> .s 組合語言程式碼
```
```
gcc -S helloCTFer.i  -o helloCTFer.s   
```
```
ls -al helloCTFer.*

-rw-rw-r-- 1 ksu ksu    76  三   5 01:23 helloCTFer.c
-rwxrwxr-x 1 ksu ksu  7352  三   5 01:32 helloCTFer.exe
-rw-rw-r-- 1 ksu ksu 17541  三   5 01:59 helloCTFer.i
-rw-rw-r-- 1 ksu ksu   659  三   5 02:04 helloCTFer.s
```
### AT&T
```
 cat helloCTFer.s  ==> 
 
	.file	"helloCTFer.c"
	.section	.rodata
.LC0:
	.string	"Hello CTFer"
	.text
	.globl	main
	.type	main, @function
main:
.LFB0:
	.cfi_startproc
	leal	4(%esp), %ecx
	.cfi_def_cfa 1, 0
	andl	$-16, %esp
	pushl	-4(%ecx)
	pushl	%ebp
	.cfi_escape 0x10,0x5,0x2,0x75,0
	movl	%esp, %ebp
	pushl	%ecx
	.cfi_escape 0xf,0x3,0x75,0x7c,0x6
	subl	$4, %esp
	subl	$12, %esp
	pushl	$.LC0
	call	puts
	addl	$16, %esp
	movl	$0, %eax
	movl	-4(%ebp), %ecx
	.cfi_def_cfa 1, 0
	leave
	.cfi_restore 5
	leal	-4(%ecx), %esp
	.cfi_def_cfa 4, 4
	ret
	.cfi_endproc
.LFE0:
	.size	main, .-main
	.ident	"GCC: (Ubuntu 5.4.0-6ubuntu1~16.04.12) 5.4.0 20160609"
	.section	.note.GNU-stack,"",@progbits
```
## 3.彙編(Compiling) 
```
將組合語言程式碼轉成 機器可以執行的指令(機器碼 instruction)
每一個組語語句都對應一組機器指令。
組譯器的組譯過程相對於編譯器來講比較簡單，它沒有複雜的語法，也沒有語意，也不需要做指令最佳化，
只是根據組語指令和機器指令的對照表一一翻譯就可以了

產出 ==> .o (== object file)
```
```
gcc -c helloCTFer.s -o helloCTFer.o
```
```
ls -al helloCTFer.*

-rw-rw-r-- 1 ksu ksu    76  三   5 01:23 helloCTFer.c
-rwxrwxr-x 1 ksu ksu  7352  三   5 01:32 helloCTFer.exe
-rw-rw-r-- 1 ksu ksu 17541  三   5 01:59 helloCTFer.i
-rw-rw-r-- 1 ksu ksu  1072  三   5 02:13 helloCTFer.o
-rw-rw-r-- 1 ksu ksu   659  三   5 02:04 helloCTFer.s
```
### 查看helloCTFer.o
```
hexdump -C helloCTFer.o
00000000  7f 45 4c 46 01 01 01 00  00 00 00 00 00 00 00 00  |.ELF............|
00000010  01 00 03 00 01 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  28 02 00 00 00 00 00 00  34 00 00 00 00 00 28 00  |(.......4.....(.|
00000030  0d 00 0a 00 8d 4c 24 04  83 e4 f0 ff 71 fc 55 89  |.....L$.....q.U.|
00000040  e5 51 83 ec 04 83 ec 0c  68 00 00 00 00 e8 fc ff  |.Q......h.......|
00000050  ff ff 83 c4 10 b8 00 00  00 00 8b 4d fc c9 8d 61  |...........M...a|
00000060  fc c3 48 65 6c 6c 6f 20  43 54 46 65 72 00 00 47  |..Hello CTFer..G|
00000070  43 43 3a 20 28 55 62 75  6e 74 75 20 35 2e 34 2e  |CC: (Ubuntu 5.4.|
00000080  30 2d 36 75 62 75 6e 74  75 31 7e 31 36 2e 30 34  |0-6ubuntu1~16.04|
00000090  2e 31 32 29 20 35 2e 34  2e 30 20 32 30 31 36 30  |.12) 5.4.0 20160|
000000a0  36 30 39 00 14 00 00 00  00 00 00 00 01 7a 52 00  |609..........zR.|
000000b0  01 7c 08 01 1b 0c 04 04  88 01 00 00 28 00 00 00  |.|..........(...|

......................
```
```
file helloCTFer.o

helloCTFer.o: ELF 32-bit LSB relocatable, Intel 80386, version 1 (SYSV), not stripped
```
## 4.連結(Linking)
```
連結(Linking)主要內容就是把各個模組之間相互引用的部分部處理好，使得各個模組之間能夠正確地銜接

有許多工作 ...以後再學 原理
位址和記憶體配置（Address and Storage Allocation)
符號解析(Symbol Resolution) 
重定址（Relocation) ==> 修正程式中每個絕對位址引用的位置，使它們指向正確的位址

最後得到 ==>
執行檔 或
執行階段程式庫(Runtime Library)
```
```
gcc  helloCTFer.o -o helloCTFer 
```
```
./helloCTFer


Hello CTFer
```
```
ls -al helloCTFer*

-rwxrwxr-x 1 ksu ksu  7352  三   5 02:21 helloCTFer
-rw-rw-r-- 1 ksu ksu    76  三   5 01:23 helloCTFer.c
-rwxrwxr-x 1 ksu ksu  7352  三   5 01:32 helloCTFer.exe
-rw-rw-r-- 1 ksu ksu 17541  三   5 01:59 helloCTFer.i
-rw-rw-r-- 1 ksu ksu  1072  三   5 02:13 helloCTFer.o
-rw-rw-r-- 1 ksu ksu   659  三   5 02:04 helloCTFer.s
```

# 逆向reverse 執行檔==> 組合語言
```
objdump -S  helloCTFer.o ==> 會產生AT&T格式 的 組合語言程式

objdump -S -M intel helloCTFer.o ==> 會產生INTEL 格式 的 組合語言程式

objdump -S  -j .text -M intel helloCTFer.o ==> 只產生 程式區塊(.text)  INTEL 格式 的 組合語言程式

objdump -S  -j .text -M intel helloCTFer.o --no-show-raw-insn
     ==> 只產生 程式區塊(.text)  INTEL 格式 的 組合語言程式 且 不顯示  機器碼(machine code)

```
