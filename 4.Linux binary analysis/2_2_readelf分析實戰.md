# readelf分析實戰
```
readelf - Displays information about ELF files.

查看ELF header   
查看可執行文件的入口處
查看Sections header
查看program header
查看重定表(Relocation Table)
[Examining the Relocation Section]
查看符號表system Table

查看某特定section
```
```
https://man.linuxde.net/readelf
```
## 查看ELF header ==> readelf -h 
```
root@kali:~# readelf -h /bin/ls
ELF Header:
  Magic:   7f 45 4c 46 02 01 01 00 00 00 00 00 00 00 00 00 
  Class:                             ELF64
  Data:                              2's complement, little endian
  Version:                           1 (current)
  OS/ABI:                            UNIX - System V
  ABI Version:                       0
  Type:                              DYN (Shared object file)
  Machine:                           Advanced Micro Devices X86-64
  Version:                           0x1
  Entry point address:               0x6130
  Start of program headers:          64 (bytes into file)
  Start of section headers:          137000 (bytes into file)
  Flags:                             0x0
  Size of this header:               64 (bytes)
  Size of program headers:           56 (bytes)
  Number of program headers:         11
  Size of section headers:           64 (bytes)
  Number of section headers:         29
  Section header string table index: 28
```
# 範例練習
```
https://linuxtools-rst.readthedocs.io/zh_CN/latest/tool/readelf.html
```
```
#include <stdio.h>

int z =1;

int main()
{
   int y =11;
   printf("Hello CTFer\n");
   return 0;
}
```
###  readelf -a ctfer
```
ELF Header:
  Magic:   7f 45 4c 46 02 01 01 00 00 00 00 00 00 00 00 00 
  Class:                             ELF64
  Data:                              2's complement, little endian
  Version:                           1 (current)
  OS/ABI:                            UNIX - System V
  ABI Version:                       0
  Type:                              DYN (Shared object file)
  Machine:                           Advanced Micro Devices X86-64
  Version:                           0x1
  Entry point address:               0x1050
  Start of program headers:          64 (bytes into file)
  Start of section headers:          14712 (bytes into file)
  Flags:                             0x0
  Size of this header:               64 (bytes)
  Size of program headers:           56 (bytes)
  Number of program headers:         11
  Size of section headers:           64 (bytes)
  Number of section headers:         30
  Section header string table index: 29

Section Headers:
  [Nr] Name              Type             Address           Offset
       Size              EntSize          Flags  Link  Info  Align
  [ 0]                   NULL             0000000000000000  00000000
       0000000000000000  0000000000000000           0     0     0
  [ 1] .interp           PROGBITS         00000000000002a8  000002a8
       000000000000001c  0000000000000000   A       0     0     1
  [ 2] .note.ABI-tag     NOTE             00000000000002c4  000002c4
       0000000000000020  0000000000000000   A       0     0     4
  [ 3] .note.gnu.build-i NOTE             00000000000002e4  000002e4
       0000000000000024  0000000000000000   A       0     0     4
  [ 4] .gnu.hash         GNU_HASH         0000000000000308  00000308
       0000000000000024  0000000000000000   A       5     0     8
  [ 5] .dynsym           DYNSYM           0000000000000330  00000330
       00000000000000a8  0000000000000018   A       6     1     8
  [ 6] .dynstr           STRTAB           00000000000003d8  000003d8
       0000000000000082  0000000000000000   A       0     0     1
  [ 7] .gnu.version      VERSYM           000000000000045a  0000045a
       000000000000000e  0000000000000002   A       5     0     2
  [ 8] .gnu.version_r    VERNEED          0000000000000468  00000468
       0000000000000020  0000000000000000   A       6     1     8
  [ 9] .rela.dyn         RELA             0000000000000488  00000488
       00000000000000c0  0000000000000018   A       5     0     8
  [10] .rela.plt         RELA             0000000000000548  00000548
       0000000000000018  0000000000000018  AI       5    23     8
  [11] .init             PROGBITS         0000000000001000  00001000
       0000000000000017  0000000000000000  AX       0     0     4
  [12] .plt              PROGBITS         0000000000001020  00001020
       0000000000000020  0000000000000010  AX       0     0     16
  [13] .plt.got          PROGBITS         0000000000001040  00001040
       0000000000000008  0000000000000008  AX       0     0     8
  [14] .text             PROGBITS         0000000000001050  00001050
       0000000000000171  0000000000000000  AX       0     0     16
  [15] .fini             PROGBITS         00000000000011c4  000011c4
       0000000000000009  0000000000000000  AX       0     0     4
  [16] .rodata           PROGBITS         0000000000002000  00002000
       0000000000000010  0000000000000000   A       0     0     4
  [17] .eh_frame_hdr     PROGBITS         0000000000002010  00002010
       000000000000003c  0000000000000000   A       0     0     4
  [18] .eh_frame         PROGBITS         0000000000002050  00002050
       0000000000000108  0000000000000000   A       0     0     8
  [19] .init_array       INIT_ARRAY       0000000000003de8  00002de8
       0000000000000008  0000000000000008  WA       0     0     8
  [20] .fini_array       FINI_ARRAY       0000000000003df0  00002df0
       0000000000000008  0000000000000008  WA       0     0     8
  [21] .dynamic          DYNAMIC          0000000000003df8  00002df8
       00000000000001e0  0000000000000010  WA       6     0     8
  [22] .got              PROGBITS         0000000000003fd8  00002fd8
       0000000000000028  0000000000000008  WA       0     0     8
  [23] .got.plt          PROGBITS         0000000000004000  00003000
       0000000000000020  0000000000000008  WA       0     0     8
  [24] .data             PROGBITS         0000000000004020  00003020
       0000000000000014  0000000000000000  WA       0     0     8
  [25] .bss              NOBITS           0000000000004034  00003034
       0000000000000004  0000000000000000  WA       0     0     1
  [26] .comment          PROGBITS         0000000000000000  00003034
       000000000000001c  0000000000000001  MS       0     0     1
  [27] .symtab           SYMTAB           0000000000000000  00003050
       0000000000000618  0000000000000018          28    45     8
  [28] .strtab           STRTAB           0000000000000000  00003668
       0000000000000205  0000000000000000           0     0     1
  [29] .shstrtab         STRTAB           0000000000000000  0000386d
       0000000000000107  0000000000000000           0     0     1
Key to Flags:
  W (write), A (alloc), X (execute), M (merge), S (strings), I (info),
  L (link order), O (extra OS processing required), G (group), T (TLS),
  C (compressed), x (unknown), o (OS specific), E (exclude),
  l (large), p (processor specific)

There are no section groups in this file.

Program Headers:
  Type           Offset             VirtAddr           PhysAddr
                 FileSiz            MemSiz              Flags  Align
  PHDR           0x0000000000000040 0x0000000000000040 0x0000000000000040
                 0x0000000000000268 0x0000000000000268  R      0x8
  INTERP         0x00000000000002a8 0x00000000000002a8 0x00000000000002a8
                 0x000000000000001c 0x000000000000001c  R      0x1
      [Requesting program interpreter: /lib64/ld-linux-x86-64.so.2]
  LOAD           0x0000000000000000 0x0000000000000000 0x0000000000000000
                 0x0000000000000560 0x0000000000000560  R      0x1000
  LOAD           0x0000000000001000 0x0000000000001000 0x0000000000001000
                 0x00000000000001cd 0x00000000000001cd  R E    0x1000
  LOAD           0x0000000000002000 0x0000000000002000 0x0000000000002000
                 0x0000000000000158 0x0000000000000158  R      0x1000
  LOAD           0x0000000000002de8 0x0000000000003de8 0x0000000000003de8
                 0x000000000000024c 0x0000000000000250  RW     0x1000
  DYNAMIC        0x0000000000002df8 0x0000000000003df8 0x0000000000003df8
                 0x00000000000001e0 0x00000000000001e0  RW     0x8
  NOTE           0x00000000000002c4 0x00000000000002c4 0x00000000000002c4
                 0x0000000000000044 0x0000000000000044  R      0x4
  GNU_EH_FRAME   0x0000000000002010 0x0000000000002010 0x0000000000002010
                 0x000000000000003c 0x000000000000003c  R      0x4
  GNU_STACK      0x0000000000000000 0x0000000000000000 0x0000000000000000
                 0x0000000000000000 0x0000000000000000  RW     0x10
  GNU_RELRO      0x0000000000002de8 0x0000000000003de8 0x0000000000003de8
                 0x0000000000000218 0x0000000000000218  R      0x1

 Section to Segment mapping:
  Segment Sections...
   00     
   01     .interp 
   02     .interp .note.ABI-tag .note.gnu.build-id .gnu.hash .dynsym .dynstr .gnu.version .gnu.version_r .rela.dyn .rela.plt 
   03     .init .plt .plt.got .text .fini 
   04     .rodata .eh_frame_hdr .eh_frame 
   05     .init_array .fini_array .dynamic .got .got.plt .data .bss 
   06     .dynamic 
   07     .note.ABI-tag .note.gnu.build-id 
   08     .eh_frame_hdr 
   09     
   10     .init_array .fini_array .dynamic .got 

Dynamic section at offset 0x2df8 contains 26 entries:
  Tag        Type                         Name/Value
 0x0000000000000001 (NEEDED)             Shared library: [libc.so.6]
 0x000000000000000c (INIT)               0x1000
 0x000000000000000d (FINI)               0x11c4
 0x0000000000000019 (INIT_ARRAY)         0x3de8
 0x000000000000001b (INIT_ARRAYSZ)       8 (bytes)
 0x000000000000001a (FINI_ARRAY)         0x3df0
 0x000000000000001c (FINI_ARRAYSZ)       8 (bytes)
 0x000000006ffffef5 (GNU_HASH)           0x308
 0x0000000000000005 (STRTAB)             0x3d8
 0x0000000000000006 (SYMTAB)             0x330
 0x000000000000000a (STRSZ)              130 (bytes)
 0x000000000000000b (SYMENT)             24 (bytes)
 0x0000000000000015 (DEBUG)              0x0
 0x0000000000000003 (PLTGOT)             0x4000
 0x0000000000000002 (PLTRELSZ)           24 (bytes)
 0x0000000000000014 (PLTREL)             RELA
 0x0000000000000017 (JMPREL)             0x548
 0x0000000000000007 (RELA)               0x488
 0x0000000000000008 (RELASZ)             192 (bytes)
 0x0000000000000009 (RELAENT)            24 (bytes)
 0x000000006ffffffb (FLAGS_1)            Flags: PIE
 0x000000006ffffffe (VERNEED)            0x468
 0x000000006fffffff (VERNEEDNUM)         1
 0x000000006ffffff0 (VERSYM)             0x45a
 0x000000006ffffff9 (RELACOUNT)          3
 0x0000000000000000 (NULL)               0x0

Relocation section '.rela.dyn' at offset 0x488 contains 8 entries:
  Offset          Info           Type           Sym. Value    Sym. Name + Addend
000000003de8  000000000008 R_X86_64_RELATIVE                    1130
000000003df0  000000000008 R_X86_64_RELATIVE                    10f0
000000004028  000000000008 R_X86_64_RELATIVE                    4028
000000003fd8  000100000006 R_X86_64_GLOB_DAT 0000000000000000 _ITM_deregisterTMClone + 0
000000003fe0  000300000006 R_X86_64_GLOB_DAT 0000000000000000 __libc_start_main@GLIBC_2.2.5 + 0
000000003fe8  000400000006 R_X86_64_GLOB_DAT 0000000000000000 __gmon_start__ + 0
000000003ff0  000500000006 R_X86_64_GLOB_DAT 0000000000000000 _ITM_registerTMCloneTa + 0
000000003ff8  000600000006 R_X86_64_GLOB_DAT 0000000000000000 __cxa_finalize@GLIBC_2.2.5 + 0

Relocation section '.rela.plt' at offset 0x548 contains 1 entry:
  Offset          Info           Type           Sym. Value    Sym. Name + Addend
000000004018  000200000007 R_X86_64_JUMP_SLO 0000000000000000 puts@GLIBC_2.2.5 + 0

The decoding of unwind sections for machine type Advanced Micro Devices X86-64 is not currently supported.

Symbol table '.dynsym' contains 7 entries:
   Num:    Value          Size Type    Bind   Vis      Ndx Name
     0: 0000000000000000     0 NOTYPE  LOCAL  DEFAULT  UND 
     1: 0000000000000000     0 NOTYPE  WEAK   DEFAULT  UND _ITM_deregisterTMCloneTab
     2: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND puts@GLIBC_2.2.5 (2)
     3: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND __libc_start_main@GLIBC_2.2.5 (2)
     4: 0000000000000000     0 NOTYPE  WEAK   DEFAULT  UND __gmon_start__
     5: 0000000000000000     0 NOTYPE  WEAK   DEFAULT  UND _ITM_registerTMCloneTable
     6: 0000000000000000     0 FUNC    WEAK   DEFAULT  UND __cxa_finalize@GLIBC_2.2.5 (2)

Symbol table '.symtab' contains 65 entries:
   Num:    Value          Size Type    Bind   Vis      Ndx Name
     0: 0000000000000000     0 NOTYPE  LOCAL  DEFAULT  UND 
     1: 00000000000002a8     0 SECTION LOCAL  DEFAULT    1 
     2: 00000000000002c4     0 SECTION LOCAL  DEFAULT    2 
     3: 00000000000002e4     0 SECTION LOCAL  DEFAULT    3 
     4: 0000000000000308     0 SECTION LOCAL  DEFAULT    4 
     5: 0000000000000330     0 SECTION LOCAL  DEFAULT    5 
     6: 00000000000003d8     0 SECTION LOCAL  DEFAULT    6 
     7: 000000000000045a     0 SECTION LOCAL  DEFAULT    7 
     8: 0000000000000468     0 SECTION LOCAL  DEFAULT    8 
     9: 0000000000000488     0 SECTION LOCAL  DEFAULT    9 
    10: 0000000000000548     0 SECTION LOCAL  DEFAULT   10 
    11: 0000000000001000     0 SECTION LOCAL  DEFAULT   11 
    12: 0000000000001020     0 SECTION LOCAL  DEFAULT   12 
    13: 0000000000001040     0 SECTION LOCAL  DEFAULT   13 
    14: 0000000000001050     0 SECTION LOCAL  DEFAULT   14 
    15: 00000000000011c4     0 SECTION LOCAL  DEFAULT   15 
    16: 0000000000002000     0 SECTION LOCAL  DEFAULT   16 
    17: 0000000000002010     0 SECTION LOCAL  DEFAULT   17 
    18: 0000000000002050     0 SECTION LOCAL  DEFAULT   18 
    19: 0000000000003de8     0 SECTION LOCAL  DEFAULT   19 
    20: 0000000000003df0     0 SECTION LOCAL  DEFAULT   20 
    21: 0000000000003df8     0 SECTION LOCAL  DEFAULT   21 
    22: 0000000000003fd8     0 SECTION LOCAL  DEFAULT   22 
    23: 0000000000004000     0 SECTION LOCAL  DEFAULT   23 
    24: 0000000000004020     0 SECTION LOCAL  DEFAULT   24 
    25: 0000000000004034     0 SECTION LOCAL  DEFAULT   25 
    26: 0000000000000000     0 SECTION LOCAL  DEFAULT   26 
    27: 0000000000000000     0 FILE    LOCAL  DEFAULT  ABS crtstuff.c
    28: 0000000000001080     0 FUNC    LOCAL  DEFAULT   14 deregister_tm_clones
    29: 00000000000010b0     0 FUNC    LOCAL  DEFAULT   14 register_tm_clones
    30: 00000000000010f0     0 FUNC    LOCAL  DEFAULT   14 __do_global_dtors_aux
    31: 0000000000004034     1 OBJECT  LOCAL  DEFAULT   25 completed.7325
    32: 0000000000003df0     0 OBJECT  LOCAL  DEFAULT   20 __do_global_dtors_aux_fin
    33: 0000000000001130     0 FUNC    LOCAL  DEFAULT   14 frame_dummy
    34: 0000000000003de8     0 OBJECT  LOCAL  DEFAULT   19 __frame_dummy_init_array_
    35: 0000000000000000     0 FILE    LOCAL  DEFAULT  ABS ctfer.c
    36: 0000000000000000     0 FILE    LOCAL  DEFAULT  ABS crtstuff.c
    37: 0000000000002154     0 OBJECT  LOCAL  DEFAULT   18 __FRAME_END__
    38: 0000000000000000     0 FILE    LOCAL  DEFAULT  ABS 
    39: 0000000000003df0     0 NOTYPE  LOCAL  DEFAULT   19 __init_array_end
    40: 0000000000003df8     0 OBJECT  LOCAL  DEFAULT   21 _DYNAMIC
    41: 0000000000003de8     0 NOTYPE  LOCAL  DEFAULT   19 __init_array_start
    42: 0000000000002010     0 NOTYPE  LOCAL  DEFAULT   17 __GNU_EH_FRAME_HDR
    43: 0000000000004000     0 OBJECT  LOCAL  DEFAULT   23 _GLOBAL_OFFSET_TABLE_
    44: 0000000000001000     0 FUNC    LOCAL  DEFAULT   11 _init
    45: 00000000000011c0     1 FUNC    GLOBAL DEFAULT   14 __libc_csu_fini
    46: 0000000000000000     0 NOTYPE  WEAK   DEFAULT  UND _ITM_deregisterTMCloneTab
    47: 0000000000004020     0 NOTYPE  WEAK   DEFAULT   24 data_start
    48: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND puts@@GLIBC_2.2.5
    49: 0000000000004034     0 NOTYPE  GLOBAL DEFAULT   24 _edata
    50: 0000000000004030     4 OBJECT  GLOBAL DEFAULT   24 z
    51: 00000000000011c4     0 FUNC    GLOBAL HIDDEN    15 _fini
    52: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND __libc_start_main@@GLIBC_
    53: 0000000000004020     0 NOTYPE  GLOBAL DEFAULT   24 __data_start
    54: 0000000000000000     0 NOTYPE  WEAK   DEFAULT  UND __gmon_start__
    55: 0000000000004028     0 OBJECT  GLOBAL HIDDEN    24 __dso_handle
    56: 0000000000002000     4 OBJECT  GLOBAL DEFAULT   16 _IO_stdin_used
    57: 0000000000001160    93 FUNC    GLOBAL DEFAULT   14 __libc_csu_init
    58: 0000000000004038     0 NOTYPE  GLOBAL DEFAULT   25 _end
    59: 0000000000001050    43 FUNC    GLOBAL DEFAULT   14 _start
    60: 0000000000004034     0 NOTYPE  GLOBAL DEFAULT   25 __bss_start
    61: 0000000000001135    34 FUNC    GLOBAL DEFAULT   14 main
    62: 0000000000004038     0 OBJECT  GLOBAL HIDDEN    24 __TMC_END__
    63: 0000000000000000     0 NOTYPE  WEAK   DEFAULT  UND _ITM_registerTMCloneTable
    64: 0000000000000000     0 FUNC    WEAK   DEFAULT  UND __cxa_finalize@@GLIBC_2.2

Histogram for `.gnu.hash' bucket list length (total of 2 buckets):
 Length  Number     % of total  Coverage
      0  1          ( 50.0%)
      1  1          ( 50.0%)    100.0%

Version symbols section '.gnu.version' contains 7 entries:
 Addr: 000000000000045a  Offset: 0x00045a  Link: 5 (.dynsym)
  000:   0 (*local*)       0 (*local*)       2 (GLIBC_2.2.5)   2 (GLIBC_2.2.5)
  004:   0 (*local*)       0 (*local*)       2 (GLIBC_2.2.5)

Version needs section '.gnu.version_r' contains 1 entry:
 Addr: 0x0000000000000468  Offset: 0x000468  Link: 6 (.dynstr)
  000000: Version: 1  File: libc.so.6  Cnt: 1
  0x0010:   Name: GLIBC_2.2.5  Flags: none  Version: 2

Displaying notes found in: .note.ABI-tag
  Owner                 Data size	Description
  GNU                  0x00000010	NT_GNU_ABI_TAG (ABI version tag)
    OS: Linux, ABI: 3.2.0

Displaying notes found in: .note.gnu.build-id
  Owner                 Data size	Description
  GNU                  0x00000014	NT_GNU_BUILD_ID (unique build ID bitstring)
    Build ID: fa039abb7cd7c19985ad8d4cd852404278fda797
```
##
```
-a –all 全部 Equivalent to: -h -l -S -s -r -d -V -A -I

-h –file-header 文件頭 Display the ELF file header

-l –program-headers 程式 Display the program headers

–segments An alias for –program-headers

-S –section-headers 段頭 Display the sections’ header

--sections	
An alias for –section-headers

-e –headers 全部頭 Equivalent to: -h -l -S

-s –syms 符號表 Display the symbol table

--symbols	
An alias for –syms

-n –notes 內核注釋 Display the core notes (if present)

-r –relocs 重定位 Display the relocations (if present)

-u –unwind Display the unwind info (if present)

-d –dynamic 動態段 Display the dynamic segment (if present)

-V –version-info 版本 Display the version sections (if present)
-A –arch-specific CPU構架 Display architecture specific information (if any).
-D –use-dynamic 動態段 Use the dynamic section info when displaying symbols
-x –hex-dump=<number> 顯示 段內內容Dump the contents of section <number>

-w[liaprmfFso] or

-I –histogram Display histogram of bucket list lengths

-W –wide 寬行輸出 Allow output width to exceed 80 characters

-H –help Display this information
-v –version Display the version number of readelf
```
