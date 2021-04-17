# GDB
```
https://www.gnu.org/software/gdb/

GDB是GNU Project調試器，它使您可以查看另一個程序在“執行”期間正在執行的操作–或該程序崩潰時正在執行的操作。

GDB可以做四種主要的事情（以及支持這些事情的其他事情）來幫助您捕獲行為中的錯誤：
(1)啟動您的程序，並指定可能影響其行為的所有內容。
(2)使程序在指定條件下停止。
(3)檢查程序停止時發生的情況。
(4)更改程序中的內容，以便您可以嘗試糾正一個錯誤的影響，然後繼續學習另一個錯誤。
```
# 推薦書籍[比較深]
```
Debug Hacks 除錯駭客 － 極致除錯的技巧與工具
吉岡弘隆、大和一洋、大岩尚宏、安部東洋、吉田俊輔 著、Studio Tib. 譯  歐萊禮  2012-09-09
https://www.tenlong.com.tw/products/9789862765678
```
# gdb 參數 ==> gdb -h 
```
This is the GNU debugger.  Usage:

    gdb [options] [executable-file [core-file or process-id]]
    gdb [options] --args executable-file [inferior-arguments ...]

Selection of debuggee and its files:

  --args             Arguments after executable-file are passed to inferior
  --core=COREFILE    Analyze the core dump COREFILE.
  --exec=EXECFILE    Use EXECFILE as the executable.
  --pid=PID          Attach to running process PID.
  --directory=DIR    Search for source files in DIR.
  --se=FILE          Use FILE as symbol file and executable file.
  --symbols=SYMFILE  Read symbols from SYMFILE.
  --readnow          Fully read symbol files on first access.
  --readnever        Do not read symbol files.
  --write            Set writing into executable and core files.

Initial commands and command files:

  --command=FILE, -x Execute GDB commands from FILE.
  --init-command=FILE, -ix
                     Like -x but execute commands before loading inferior.
  --eval-command=COMMAND, -ex
                     Execute a single GDB command.
                     May be used multiple times and in conjunction
                     with --command.
  --init-eval-command=COMMAND, -iex
                     Like -ex but before loading inferior.
  --nh               Do not read ~/.gdbinit.
  --nx               Do not read any .gdbinit files in any directory.

Output and user interface control:

  --fullname         Output information used by emacs-GDB interface.
  --interpreter=INTERP
                     Select a specific interpreter / user interface
  --tty=TTY          Use TTY for input/output by the program being debugged.
  -w                 Use the GUI interface.
  --nw               Do not use the GUI interface.
  --tui              Use a terminal user interface.
  --dbx              DBX compatibility mode.
  -q, --quiet, --silent
                     Do not print version number on startup.

Operating modes:

  --batch            Exit after processing options.
  --batch-silent     Like --batch, but suppress all gdb stdout output.
  --return-child-result
                     GDB exit code will be the child's exit code.
  --configuration    Print details about GDB configuration and then exit.
  --help             Print this message and then exit.
  --version          Print version information and then exit.

Remote debugging options:

  -b BAUDRATE        Set serial port baud rate used for remote debugging.
  -l TIMEOUT         Set timeout in seconds for remote debugging.

Other options:

  --cd=DIR           Change current directory to DIR.
  --data-directory=DIR, -D
                     Set GDB's data-directory to DIR.

At startup, GDB reads the following init files and executes their commands:
   * system-wide init file: /etc/gdb/gdbinit

For more information, type "help" from within GDB, or consult the
GDB manual (available as on-line info or a printed manual).
Report bugs to "<http://www.gnu.org/software/gdb/bugs/>".
```
