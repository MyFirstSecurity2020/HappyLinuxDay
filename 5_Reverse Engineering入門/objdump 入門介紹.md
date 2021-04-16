# objdump
```
objdump是在Unix-like作業系統上 顯示 關於 目的檔 的各種資訊的命令行程式  <==  這是 你的 作業

也可用作反組譯器來以組譯代碼形式檢視可執行檔   <==  這是要教你的

它是GNU Binutils的一部分，用於在可執行檔和其他二進位資料上進行精細粒度控制。
```
# objdump指令參數
```
https://man7.org/linux/man-pages/man1/objdump.1.html
```
```
root@kali:~# objdump 

Usage: objdump <option(s)> <file(s)>

Display information from object <file(s)>.
 At least one of the following switches must be given:
  -a, --archive-headers    Display archive header information
  -f, --file-headers       Display the contents of the overall file header
  -p, --private-headers    Display object format specific file header contents
  -P, --private=OPT,OPT... Display object format specific contents
  -h, --[section-]headers  Display the contents of the section headers
  -x, --all-headers        Display the contents of all headers
  -d, --disassemble        Display assembler contents of executable sections  <===反組譯要用的參數
  -D, --disassemble-all    Display assembler contents of all sections <===反組譯要用的參數
  -S, --source             Intermix source code with disassembly <===反組譯可用的參數
  -s, --full-contents      Display the full contents of all sections requested <===反組譯可用的參數
  -g, --debugging          Display debug information in object file
  -e, --debugging-tags     Display debug information using ctags style
  -G, --stabs              Display (in raw form) any STABS info in the file
  -W[lLiaprmfFsoRtUuTgAckK] or
  --dwarf[=rawline,=decodedline,=info,=abbrev,=pubnames,=aranges,=macro,=frames,
          =frames-interp,=str,=loc,=Ranges,=pubtypes,
          =gdb_index,=trace_info,=trace_abbrev,=trace_aranges,
          =addr,=cu_index,=links,=follow-links]
                           Display DWARF info in the file
  -t, --syms               Display the contents of the symbol table(s)
  -T, --dynamic-syms       Display the contents of the dynamic symbol table
  -r, --reloc              Display the relocation entries in the file
  -R, --dynamic-reloc      Display the dynamic relocation entries in the file
  @<file>                  Read options from <file>
  -v, --version            Display this program's version number
  -i, --info               List object formats and architectures supported
  -H, --help               Display this information
```
