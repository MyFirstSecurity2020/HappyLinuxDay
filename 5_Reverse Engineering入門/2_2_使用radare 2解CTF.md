# easyCTF-2018-Adder
```
easyCTF-2018-Adder
https://github.com/asinggih/easyCTF-2018-writeups/blob/master/Reverse_Engineering/Adder.md
```
# 解題步驟
```
r2 ./adder 

[0x00400860]> aaa

[x] Analyze all flags starting with sym. and entry0 (aa)
[x] Analyze function calls (aac)
[x] Analyze len bytes of instructions for references (aar)
[x] Constructing a function name for fcn.* and sym.func.* functions (aan)
[x] Type matching analysis for all functions (aaft)
[x] Use -AA or aaaa to perform additional experimental analysis.

[0x00400860]> pdf
            ;-- section..text:
            ;-- rip:
/ (fcn) entry0 41
|   entry0 (func rtld_fini);
|           ; arg func rtld_fini @ rdx
|           0x00400860      31ed           xor ebp, ebp                ; [13] -r-x section size 1106 named .text
|           0x00400862      4989d1         mov r9, rdx                 ; func rtld_fini
|           0x00400865      5e             pop rsi                     ; int argc
|           0x00400866      4889e2         mov rdx, rsp                ; char **ubp_av
|           0x00400869      4883e4f0       and rsp, 0xfffffffffffffff0
|           0x0040086d      50             push rax
|           0x0040086e      54             push rsp
|           0x0040086f      49c7c0b00c40.  mov r8, sym.__libc_csu_fini ; 0x400cb0 ; func fini
|           0x00400876      48c7c1400c40.  mov rcx, sym.__libc_csu_init ; 0x400c40 ; "AWA\x89\xffAVI\x89\xf6AUI\x89\xd5ATL\x8d%\x80\x11 " ; func init
|           0x0040087d      48c7c71e0b40.  mov rdi, main               ; sym.main ; 0x400b1e ; func main
\           0x00400884      e877ffffff     call sym.imp.__libc_start_main ; int __libc_start_main(func main, int argc, char **ubp_av, func init, func fini, func rtld_fini, void *stack_end)
[0x00400860]> 

[0x00400860]> pdf@main
              ==>你就會看到答案
```
