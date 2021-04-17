# radare2
```
wiki
Radare2是用於對二進製文件進行反向工程和分析的完整框架。
由一組可以與命令行一起使用或獨立使用的小型實用程序組成。
它圍繞計算機軟件的反彙編器而構建，該反彙編器可以從機器可執行代碼生成彙編語言源代碼，
它支持用於不同處理器體系結構和操作系統的各種可執行格式。
```
# 2_安裝
## KALI 64(本次上課提供的image) 已安裝
```
r2 -v  ==> 查看版本

radare2 3.2.1 0 @ linux-x86-64 git.
commit: unknown build: 2019-03-02__19:36:59
```
## 安裝
```
sudo apt-get install radare2
```


# 3_指令參數
```
r2 -h
Usage: r2 [-ACdfLMnNqStuvwzX] [-P patch] [-p prj] [-a arch] [-b bits] [-i file]
          [-s addr] [-B baddr] [-m maddr] [-c cmd] [-e k=v] file|pid|-|--|=
 --           run radare2 without opening any file
 -            same as 'r2 malloc://512'
 =            read file from stdin (use -i and -c to run cmds)
 -=           perform !=! command to run all commands remotely
 -0           print \x00 after init and every command
 -2           close stderr file descriptor (silent warning messages)
 -a [arch]    set asm.arch
 -A           run 'aaa' command to analyze all referenced code
 -b [bits]    set asm.bits
 -B [baddr]   set base address for PIE binaries
 -c 'cmd..'   execute radare command
 -C           file is host:port (alias for -c+=http://%s/cmd/)
 -d           debug the executable 'file' or running process 'pid'
 -D [backend] enable debug mode (e cfg.debug=true)
 -e k=v       evaluate config var
 -f           block size = file size
 -F [binplug] force to use that rbin plugin
 -h, -hh      show help message, -hh for long
 -H ([var])   display variable
 -i [file]    run script file
 -I [file]    run script file before the file is opened
 -k [OS/kern] set asm.os (linux, macos, w32, netbsd, ...)
 -l [lib]     load plugin file
 -L           list supported IO plugins
 -m [addr]    map file at given address (loadaddr)
 -M           do not demangle symbol names
 -n, -nn      do not load RBin info (-nn only load bin structures)
 -N           do not load user settings and scripts
 -q           quiet mode (no prompt) and quit after -i
 -Q           quiet mode (no prompt) and quit faster (quickLeak=true)
 -p [prj]     use project, list if no arg, load if no file
 -P [file]    apply rapatch file and quit
 -r [rarun2]  specify rarun2 profile to load (same as -e dbg.profile=X)
 -R [rr2rule] specify custom rarun2 directive
 -s [addr]    initial seek
 -S           start r2 in sandbox mode
 -t           load rabin2 info in thread
 -u           set bin.filter=false to get raw sym/sec/cls names
 -v, -V       show radare2 version (-V show lib versions)
 -w           open file in write mode
 -x           open without exec-flag (asm.emu will not work), See io.exec
 -X           same as -e bin.usextr=false (useful for dyldcache)
 -z, -zz      do not load strings or load them even in raw
```
# 4_BINARY 加載 與 退出
```
BINARY 加載 

$ r2 ./adder
 -- Learn pancake as if you were radare!
[0x004004b0]> quit

退出控制枱，==> 輸入 Quit 或 Exit 或按 Ctrl+D：
```
# 範例學習 ==> 基本常用指令
```
全功能的二進制文件分析工具 Radare2 指南
時間 2021-02-02 09:01:14 osc_4punxmqt
https://www.mdeditor.tw/pl/gvNU/zh-hk
```
```
(1)先分析BINARY ==> 使用 aaa 命令

$ r2 ./adder
 -- Sorry, radare2 has experienced an internal error.
[0x004004b0]>
[0x004004b0]>
[0x004004b0]> aaa

(2)取得BINARY的基本信息  ==> iI 命令
    二進制文件的格式（ELF、PE 等）、二進制的架構（x86、AMD、ARM 等），以及二進制是 32 位還是 64 位
    ：
列出二進制中存在的函數==> afl 命令

使用 s main 尋找 main 函數的地址，然後運行 pdf 命令來查看反彙編的指令
```
# easyCTF-2018-Adder
