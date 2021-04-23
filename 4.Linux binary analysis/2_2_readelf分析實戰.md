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
