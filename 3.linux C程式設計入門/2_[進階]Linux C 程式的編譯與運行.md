# Linux C 程式的編譯與運行:
```
編譯的各階段 ==> 參考底下延伸閱讀的資料
 原始程式碼 ===>  
 預處理 ===> 
 編譯 ===>
 彙編 ===>
 連結 ===>
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
 原始程式碼 ===>  helloCTFer.c
 預處理 ===> gcc –E helloCTFer.c –o helloCTFer.i    ===> 查看.i的架構
 編譯 ===> gcc –S helloCTFer.i  -o helloCTFer.s   ===> 查看.s的架構
 彙編 ===> gcc -c helloCTFer.s -o helloCTFer.o ===> 查看.o的架構
 連結 ===> gcc  helloCTFer.o -o helloCTFer  ===> 查看helloCTFer的架構
```
### 預處理
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

### 編譯 
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
## 彙編 
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
## 連結 
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
# 進階閱讀
```
 Advanced C and C++ Compiling by Milan Stevanovic (Apress, 2014).
 https://github.com/Apress/adv-c-cpp-compiling
 
簡體中譯  高級C/C++編譯技術 （美）斯特瓦諾維奇
機械工業出版社  2015/04/01
 
 先看 
 第2章 程序生命周期階段基礎
 第3章 加載程序執行階段
```
