# GDB常用指令
```
請根據你的學習經歷逐步整理相關"筆記"(存在你的github以後,可以申請學校佳芬用)
```
```
底下參考下列網址整理
https://jasonblog.github.io/note/gdb/gdbchang_yong_zhi_ling.html
```
# GDB主要功能：
```
啟動程式，可以按照自訂的要求隨心所欲的運行程式。
可讓被調試的程式在你所指定的調置的中斷點處停住。（中斷點可以是條件運算式）
當程式被停住時，可以檢查此時你的程式中所發生的事。
動態的改變你程式的執行環境。
```
## 載入與離開
```
[1]載入被調試的可執行程式檔 ==> file <檔案名>
因為一般都在被偵錯工具所在目錄下執行GDB，因而文本名不需要帶路徑。

[2]關聯指定行程(process) ==> attach <PID>

    (gdb) attach 1024 //關聯行程號為1024的行程進行調試

[3]q  ==> Quit的簡寫，退出GDB調試環境。
```
## 使用help 查詢用法
```
help [命令名稱]

GDB幫助命令，提供對GDB名種命令的解釋說明。
如果指定了“命令名稱”參數，則顯示該命令的詳細說明；
如果沒有指定參數，則分類顯示所有GDB命令，供用戶進一步流覽和查詢。

(gdb) help display

(gdb) help p  ==> 查看print命令的詳細說明。

Print value of expression EXP.
Variables accessible are those of the lexical environment of the selected stack frame, 
plus all those whose scope is global or an entire file.

$NUM gets previous value number NUM.  
$ and $$ are the last two values.
$$NUM refers to NUM'th value back from the last one.
Names starting with $ refer to registers (with the values they would have 
if the program were to return to the stack frame now selected, 
restoring all registers saved by frames farther in) or else 
to debugger "convenience" variables (any such name not a known register).
Use assignment expressions to give values to convenience variables.

{TYPE}ADREXP refers to a datum of data type TYPE, located at address ADREXP.

@ is a binary operator for treating consecutive data objects
anywhere in memory as an array.  

FOO@NUM gives an array whose first element is FOO, 
whose second element is stored in the space following where FOO is stored, etc.  
FOO must be an expression whose value resides in memory.

EXP may be preceded with /FMT, where FMT is a format letter
but no count or size letter (see "x" command).

@參數==> 讓你像查看陣列內容一樣列印連續記憶體的資料物件。
“@”的左邊是第一個記憶體的位址的值，
“@”的右邊則你你想查看記憶體的長度。

例如，你的程式中有這樣的語句：
   int *array = (int *)malloc(len * sizeof(int));
==> 在GDB調試過程中，可以如下命令顯示出這個動態陣列的取值：
   (gdb) p *array@len
```
## 
```
[1]  l ==> List的簡寫
列出當前位置之後的10行代碼；
list line_number;  ==>列出line_number之後的十行代碼。

[2] r ==> Run的簡寫，運行被調試的程式。
如果此前沒有下過中斷點，則執行完整個程式；
如果有中斷點，則程式暫停在第一個可用中斷點處。

[3]c ==> Continue的簡寫，繼續執行被偵錯工具，直至下一個中斷點或程式結束。
   (gdb) c
```
## 設置中斷點 ==> b是Breakpoint的簡寫
```
b <行號>
b <函數名稱>
b *<函數名稱>
b *<代碼地址>


設置中斷點。兩可以使用“行號”“函數名稱”“執行位址”等方式指定中斷點位置。
其中在函數名稱前面加*符號表示將中斷點設置在“由編譯器生成的prolog代碼處”。如果不瞭解彙編，可以不予理會此用法。

break ... if ...：條件中斷。

d [編號]
d是Delete breakpoint的簡寫，刪除指定編號的某個中斷點，或刪除所有中斷點。
中斷點編號從1開始遞增。

(gdb) b 8
(gdb) b main
(gdb) b *main
(gdb) b *0x804835c
(gdb) d
```

# 設置變數 ==> set
```
在單步偵錯工具的中間使用調試器設置變數的值是非常有用的。
命令是
    (gdb) set x = 12
可以通過gdb的set args 命令設置程式的命令列參數。

設置“方便變數”，命令是
    (gdb) set $q = p
用來記錄特定節點的歷史，這個變數q不會去改變自己的位址。

在調用gdb時，可以指定“開機檔案”。例如：
    gdb –command=z x
表示要在可執行檔x上運行gdb，首先要從檔z中讀取命令。   

    (gdb) jump 34  ==> 程式直接跳到34行。

使用strace命令，可以跟蹤系統做過的所有系統調用。
```
## bt ==> backtrace的簡寫，列出呼叫的stack
```
(gdb) bt
```
```
s ==> 執行一行來源程式代碼
如果此行代碼中有函式呼叫，則進入該函數。
相當於其它調試器中的“Step Into (單步跟蹤進入)”。
這個命令必須在有原始程式碼調試資訊的情況下才可以使用
（GCC編譯時使用“-g”參數）。

n ==> 執行一行來源程式代碼，此行代碼中的函式呼叫也一併執行。
相當於其它調試器中的“Step Over (單步跟蹤)”。
這個命令必須在有原始程式碼調試資訊的情況下才可以使用
（GCC編譯時使用“-g”參數）。
(gdb) n

si ==> si命令類似於s命令，但針對彙編指令。

ni ==> ni命令類似於n命令，但針對彙編指令。
```
```
p <變數名稱>
Print的簡寫，顯示指定變數（臨時變數或全域變數）的值。
```
```
x
和print命令需要指定變數不同，x命令需要指定記憶體位址。

(gdb) help x
Examine memory: x/FMT ADDRESS.
ADDRESS is an expression for the memory address to examine.
FMT is a repeat count followed by a format letter and a size letter.

Format letters are o(octal), x(hex), d(decimal), u(unsigned decimal),
  t(binary), f(float), a(address), i(instruction), c(char) and s(string).

Size letters are b(byte), h(halfword), w(word), g(giant, 8 bytes).

The specified number of objects of the specified size are printed
according to the format.
Defaults for format and size letters are those previously used.
Default count is 1.  Default address is following last thing printed
with this command or "print".

(gdb) x /6cb 0x804835c //列印位址0x804835c起始的記憶體內容，連續6個位元組，以字元格式輸出。
```
```
display ...
undisplay <編號>
display，設置程式中斷後欲顯示的資料及其格式。

例如，如果希望每次程式中斷後可以看到即將被執行的下一條彙編指令，可以使用命令display /i $pc，其中 $pc 代表當前彙編指令，/i 表示以十六進行顯示。

當需要關心彙編代碼時，此命令相當有用。

undispaly，取消先前的display設置，編號從1開始遞增。
```
## i ==> Info的簡寫，用於顯示各類資訊
```
詳情請查閱“help i”。

(gdb) help i
info address -- Describe where symbol SYM is stored
info all-registers -- List of all registers and their contents
info args -- Argument variables of current stack frame
info auto-load -- Print current status of auto-loaded files
info auto-load-scripts -- Print the list of automatically loaded   
                     Python scripts
info auxv -- Display the inferior's auxiliary vector
info bookmarks -- Status of user-settable bookmarks
info breakpoints -- Status of specified breakpoints 
           (all user-settable breakpoints if no argument)
info checkpoints -- IDs of currently known checkpoints
info classes -- All Objective-C classes
info common -- Print out the values contained in a Fortran COMMON block
info copying -- Conditions for redistributing copies of GDB
info dcache -- Print information on the dcache performance
info display -- Expressions to display when program stops
info extensions -- All filename extensions associated with a source language
info files -- Names of targets and files being debugged
info float -- Print the status of the floating point unit
info frame -- All about selected stack frame
info frame-filter -- List all registered Python frame-filters
info functions -- All function names
info handle -- What debugger does when program gets various signals
info inferiors -- IDs of specified inferiors (all inferiors if no argument)
info line -- Core addresses of the code for a source line
info locals -- Local variables of current stack frame
info macro -- Show the definition of MACRO
info macros -- Show the definitions of all macros at LINESPEC
info mem -- Memory region attributes
info os -- Show OS data ARG
info pretty-printer -- GDB command to list all registered pretty-printers
info probes -- Show available static probes
info proc -- Show /proc process information about any running process
info program -- Execution status of the program
info record -- Info record options
info registers -- List of integer registers and their contents
info scope -- List the variables local to a scope
info selectors -- All Objective-C selectors
info set -- Show all GDB settings
info sharedlibrary -- Status of loaded shared object libraries
info signals -- What debugger does when program gets various signals
info skip -- Display the status of skips
info source -- Information about the current source file
info sources -- Source files in the program
info stack -- Backtrace of the stack
info static-tracepoint-markers -- List target static tracepoints markers
info symbol -- Describe what symbol is at location ADDR
info target -- Names of targets and files being debugged
info tasks -- Provide information about all known Ada tasks
info terminal -- Print inferior's saved terminal status
info threads -- Display currently known threads
info tracepoints -- Status of specified tracepoints (all tracepoints if no argument)
info tvariables -- Status of trace state variables and their values
info type-printers -- GDB command to list all registered type-printers
info types -- All type names
info variables -- All global and static variable names
info vector -- Print the status of the vector unit
info vtbl -- Show the virtual function table for a C++ object
info warranty -- Various kinds of warranty you do not have
info watchpoints -- Status of specified watchpoints (all watchpoints if no argument)
info win -- List of all displayed windows


(gdb) i r
```


## 中斷點相關指令彙編
```
break 設定中斷點
info break: 查詢已設定的中斷點
disp 運算式: 每次中斷所顯示的運算式
info disp: 查詢已設定那些顯示式
next: 執行一列程式碼 (可加欲執行的列數)
step: 執行一列程式碼, 但如遇到函數呼叫, 則進入函數裡一步步執行
cont: 執行, 直到中斷點或程式結束為止
```
## 與堆疊有關的指令
```
where: 顯示目前副程式層層呼叫的狀況
up: 往上一層
down: 往下一層
```

## 列印與查看記憶體內容 ==>格式: x /nfu
```
x 是 examine 的縮寫

n表示要顯示的內存單元的個數

f表示顯示方式, 可取如下值
  x 按十六進制格式顯示變量。
  d 按十進制格式顯示變量。
  u 按十進制格式顯示無符號整型。
  o 按八進制格式顯示變量。
  t 按二進制格式顯示變量。
  a 按十六進制格式顯示變量。
  i 指令地址格式
  c 按字符格式顯示變量。
  f 按浮點數格式顯示變量。

u表示一個地址單元的長度
  b表示單字節，
  h表示雙字節，
  w表示四字節，
  g表示八字節

Format letters ==>
o(octal), 
x(hex), 
d(decimal), 
u(unsigned decimal),
t(binary), 
f(float), 
a(address), 
i(instruction), 
c(char) and 
s(string).

Size letters ==> 
b(byte), 
h(halfword), 
w(word), 
g(giant, 8 bytes)
```
```
x/3uh buf 
表示從內存地址buf讀取內容，
h表示以雙字節為一個單位，
3表示三個單位，
u表示按十六進制顯示
```

