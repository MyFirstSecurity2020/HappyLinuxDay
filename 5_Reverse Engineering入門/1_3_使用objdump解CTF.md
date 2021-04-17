# easyCTF-2018-Adder
```
先找出main()函數
再找出關鍵程式分析 ==> 找底下組合語言程式
                      call
                      cmp ==> 比較
```
```
objdump -S -j .text -M intel adder --no-show-raw-insn

adder:     file format elf64-x86-64


Disassembly of section .text:

0000000000400860 <_start>:
  400860:	xor    ebp,ebp
  400862:	mov    r9,rdx
  400865:	pop    rsi
  400866:	mov    rdx,rsp
  400869:	and    rsp,0xfffffffffffffff0
  40086d:	push   rax
  40086e:	push   rsp
  40086f:	mov    r8,0x400cb0
  400876:	mov    rcx,0x400c40
  40087d:	mov    rdi,0x400b1e
  400884:	call   400800 <__libc_start_main@plt>
  400889:	hlt    
  40088a:	nop    WORD PTR [rax+rax*1+0x0]

0000000000400890 <deregister_tm_clones>:
  400890:	mov    eax,0x60207f
  400895:	push   rbp
  400896:	sub    rax,0x602078
  40089c:	cmp    rax,0xe
  4008a0:	mov    rbp,rsp
  4008a3:	ja     4008a7 <deregister_tm_clones+0x17>
  4008a5:	pop    rbp
  4008a6:	ret    
  4008a7:	mov    eax,0x0
  4008ac:	test   rax,rax
  4008af:	je     4008a5 <deregister_tm_clones+0x15>
  4008b1:	pop    rbp
  4008b2:	mov    edi,0x602078
  4008b7:	jmp    rax
  4008b9:	nop    DWORD PTR [rax+0x0]

00000000004008c0 <register_tm_clones>:
  4008c0:	mov    eax,0x602078
  4008c5:	push   rbp
  4008c6:	sub    rax,0x602078
  4008cc:	sar    rax,0x3
  4008d0:	mov    rbp,rsp
  4008d3:	mov    rdx,rax
  4008d6:	shr    rdx,0x3f
  4008da:	add    rax,rdx
  4008dd:	sar    rax,1
  4008e0:	jne    4008e4 <register_tm_clones+0x24>
  4008e2:	pop    rbp
  4008e3:	ret    
  4008e4:	mov    edx,0x0
  4008e9:	test   rdx,rdx
  4008ec:	je     4008e2 <register_tm_clones+0x22>
  4008ee:	pop    rbp
  4008ef:	mov    rsi,rax
  4008f2:	mov    edi,0x602078
  4008f7:	jmp    rdx
  4008f9:	nop    DWORD PTR [rax+0x0]

0000000000400900 <__do_global_dtors_aux>:
  400900:	cmp    BYTE PTR [rip+0x2019a9],0x0        # 6022b0 <completed.6345>
  400907:	jne    40091a <__do_global_dtors_aux+0x1a>
  400909:	push   rbp
  40090a:	mov    rbp,rsp
  40090d:	call   400890 <deregister_tm_clones>
  400912:	pop    rbp
  400913:	mov    BYTE PTR [rip+0x201996],0x1        # 6022b0 <completed.6345>
  40091a:	repz ret 
  40091c:	nop    DWORD PTR [rax+0x0]

0000000000400920 <frame_dummy>:
  400920:	cmp    QWORD PTR [rip+0x2014c8],0x0        # 601df0 <__JCR_END__>
  400928:	je     400948 <frame_dummy+0x28>
  40092a:	mov    eax,0x0
  40092f:	test   rax,rax
  400932:	je     400948 <frame_dummy+0x28>
  400934:	push   rbp
  400935:	mov    edi,0x601df0
  40093a:	mov    rbp,rsp
  40093d:	call   rax
  40093f:	pop    rbp
  400940:	jmp    4008c0 <register_tm_clones>
  400945:	nop    DWORD PTR [rax]
  400948:	jmp    4008c0 <register_tm_clones>

000000000040094d <_Z3geni>:
  40094d:	push   rbp
  40094e:	mov    rbp,rsp
  400951:	sub    rsp,0x20
  400955:	mov    DWORD PTR [rbp-0x14],edi
  400958:	mov    eax,0x16
  40095d:	mov    rdi,rax
  400960:	call   4007f0 <malloc@plt>
  400965:	mov    QWORD PTR [rbp-0x8],rax
  400969:	mov    rax,QWORD PTR [rbp-0x8]
  40096d:	mov    BYTE PTR [rax],0x79
  400970:	mov    rax,QWORD PTR [rbp-0x8]
  400974:	lea    rsi,[rax+0x1]
  400978:	mov    ecx,DWORD PTR [rbp-0x14]
  40097b:	mov    edx,0x92492493
  400980:	mov    eax,ecx
  400982:	imul   edx
  400984:	lea    eax,[rdx+rcx*1]
  400987:	sar    eax,0x2
  40098a:	mov    edx,eax
  40098c:	mov    eax,ecx
  40098e:	sar    eax,0x1f
  400991:	sub    edx,eax
  400993:	mov    eax,edx
  400995:	shl    eax,0x3
  400998:	sub    eax,edx
  40099a:	sub    ecx,eax
  40099c:	mov    edx,ecx
  40099e:	mov    eax,edx
  4009a0:	add    eax,0x30
  4009a3:	mov    BYTE PTR [rsi],al
  4009a5:	mov    rax,QWORD PTR [rbp-0x8]
  4009a9:	lea    rdx,[rax+0x2]
  4009ad:	mov    eax,DWORD PTR [rbp-0x14]
  4009b0:	add    eax,0x3c
  4009b3:	mov    BYTE PTR [rdx],al
  4009b5:	mov    rax,QWORD PTR [rbp-0x8]
  4009b9:	add    rax,0x3
  4009bd:	mov    BYTE PTR [rax],0x5f
  4009c0:	mov    rax,QWORD PTR [rbp-0x8]
  4009c4:	lea    rdx,[rax+0x4]
  4009c8:	mov    rax,QWORD PTR [rbp-0x8]
  4009cc:	add    rax,0x2
  4009d0:	movzx  eax,BYTE PTR [rax]
  4009d3:	sub    eax,0x14
  4009d6:	mov    BYTE PTR [rdx],al
  4009d8:	mov    rax,QWORD PTR [rbp-0x8]
  4009dc:	lea    rdx,[rax+0x5]
  4009e0:	mov    rax,QWORD PTR [rbp-0x8]
  4009e4:	add    rax,0x4
  4009e8:	movzx  eax,BYTE PTR [rax]
  4009eb:	add    eax,0x3
  4009ee:	mov    BYTE PTR [rdx],al
  4009f0:	mov    rax,QWORD PTR [rbp-0x8]
  4009f4:	lea    rdx,[rax+0x6]
  4009f8:	mov    rax,QWORD PTR [rbp-0x8]
  4009fc:	movzx  eax,BYTE PTR [rax+0x5]
  400a00:	mov    BYTE PTR [rdx],al
  400a02:	mov    rax,QWORD PTR [rbp-0x8]
  400a06:	add    rax,0x7
  400a0a:	mov    BYTE PTR [rax],0x65
  400a0d:	mov    rax,QWORD PTR [rbp-0x8]
  400a11:	lea    rdx,[rax+0x8]
  400a15:	mov    rax,QWORD PTR [rbp-0x8]
  400a19:	movzx  eax,BYTE PTR [rax+0x6]
  400a1d:	mov    BYTE PTR [rdx],al
  400a1f:	mov    rax,QWORD PTR [rbp-0x8]
  400a23:	lea    rdx,[rax+0x9]
  400a27:	mov    rax,QWORD PTR [rbp-0x8]
  400a2b:	movzx  eax,BYTE PTR [rax+0x3]
  400a2f:	mov    BYTE PTR [rdx],al
  400a31:	mov    rax,QWORD PTR [rbp-0x8]
  400a35:	add    rax,0xa
  400a39:	mov    BYTE PTR [rax],0x74
  400a3c:	mov    rax,QWORD PTR [rbp-0x8]
  400a40:	lea    rdx,[rax+0xb]
  400a44:	mov    rax,QWORD PTR [rbp-0x8]
  400a48:	add    rax,0xa
  400a4c:	movzx  eax,BYTE PTR [rax]
  400a4f:	sub    eax,0xc
  400a52:	mov    BYTE PTR [rdx],al
  400a54:	mov    rax,QWORD PTR [rbp-0x8]
  400a58:	add    rax,0xc
  400a5c:	mov    BYTE PTR [rax],0x72
  400a5f:	mov    rax,QWORD PTR [rbp-0x8]
  400a63:	add    rax,0xd
  400a67:	mov    BYTE PTR [rax],0x33
  400a6a:	mov    rax,QWORD PTR [rbp-0x8]
  400a6e:	add    rax,0xe
  400a72:	mov    BYTE PTR [rax],0x33
  400a75:	mov    rax,QWORD PTR [rbp-0x8]
  400a79:	lea    rdx,[rax+0xf]
  400a7d:	mov    rax,QWORD PTR [rbp-0x8]
  400a81:	movzx  eax,BYTE PTR [rax+0x3]
  400a85:	mov    BYTE PTR [rdx],al
  400a87:	mov    rax,QWORD PTR [rbp-0x8]
  400a8b:	add    rax,0x10
  400a8f:	mov    BYTE PTR [rax],0x6e
  400a92:	mov    rax,QWORD PTR [rbp-0x8]
  400a96:	lea    rdx,[rax+0x11]
  400a9a:	mov    rax,QWORD PTR [rbp-0x8]
  400a9e:	movzx  eax,BYTE PTR [rax+0x2]
  400aa2:	mov    BYTE PTR [rdx],al
  400aa4:	mov    rax,QWORD PTR [rbp-0x8]
  400aa8:	lea    rdx,[rax+0x12]
  400aac:	mov    rax,QWORD PTR [rbp-0x8]
  400ab0:	add    rax,0x10
  400ab4:	movzx  eax,BYTE PTR [rax]
  400ab7:	sub    eax,0x1
  400aba:	mov    BYTE PTR [rdx],al
  400abc:	mov    rax,QWORD PTR [rbp-0x8]
  400ac0:	add    rax,0x13
  400ac4:	mov    BYTE PTR [rax],0x73
  400ac7:	mov    rax,QWORD PTR [rbp-0x8]
  400acb:	add    rax,0x14
  400acf:	mov    BYTE PTR [rax],0x21
  400ad2:	mov    rax,QWORD PTR [rbp-0x8]
  400ad6:	add    rax,0x15
  400ada:	mov    BYTE PTR [rax],0xa
  400add:	mov    rax,QWORD PTR [rbp-0x8]
  400ae1:	leave  
  400ae2:	ret    

0000000000400ae3 <_Z9print_ptrPc>:
  400ae3:	push   rbp
  400ae4:	mov    rbp,rsp
  400ae7:	sub    rsp,0x20
  400aeb:	mov    QWORD PTR [rbp-0x18],rdi
  400aef:	mov    DWORD PTR [rbp-0x4],0x0
  400af6:	jmp    400b16 <_Z9print_ptrPc+0x33>
  400af8:	mov    eax,DWORD PTR [rbp-0x4]
  400afb:	movsxd rdx,eax
  400afe:	mov    rax,QWORD PTR [rbp-0x18]
  400b02:	add    rax,rdx
  400b05:	movzx  eax,BYTE PTR [rax]
  400b08:	movsx  eax,al
  400b0b:	mov    edi,eax
  400b0d:	call   4007d0 <putchar@plt>
  400b12:	add    DWORD PTR [rbp-0x4],0x1
  400b16:	cmp    DWORD PTR [rbp-0x4],0x14
  400b1a:	jle    400af8 <_Z9print_ptrPc+0x15>
  400b1c:	leave  
  400b1d:	ret    

0000000000400b1e <main>:    <== main()函數
  400b1e:	push   rbp
  400b1f:	mov    rbp,rsp
  400b22:	sub    rsp,0x20
  400b26:	mov    DWORD PTR [rbp-0xc],0x0
  400b2d:	mov    DWORD PTR [rbp-0x10],0x0
  400b34:	mov    DWORD PTR [rbp-0x14],0x0
  400b3b:	mov    esi,0x400cd0
  400b40:	mov    edi,0x6021a0
  400b45:	call   400830 <_ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc@plt>
  400b4a:	lea    rax,[rbp-0xc]
  400b4e:	mov    rsi,rax
  400b51:	mov    edi,0x602080
  400b56:	call   400850 <_ZNSirsERi@plt>
  400b5b:	lea    rdx,[rbp-0x10]
  400b5f:	mov    rsi,rdx
  400b62:	mov    rdi,rax
  400b65:	call   400850 <_ZNSirsERi@plt>
  400b6a:	lea    rdx,[rbp-0x14]
  400b6e:	mov    rsi,rdx
  400b71:	mov    rdi,rax
  400b74:	call   400850 <_ZNSirsERi@plt>
  400b79:	mov    edx,DWORD PTR [rbp-0xc]
  400b7c:	mov    eax,DWORD PTR [rbp-0x10]
  400b7f:	add    edx,eax
  400b81:	mov    eax,DWORD PTR [rbp-0x14]
  400b84:	add    eax,edx
  400b86:	mov    edi,eax
  400b88:	call   40094d <_Z3geni>
  400b8d:	mov    QWORD PTR [rbp-0x8],rax
  400b91:	mov    edx,DWORD PTR [rbp-0xc]
  400b94:	mov    eax,DWORD PTR [rbp-0x10]
  400b97:	add    edx,eax
  400b99:	mov    eax,DWORD PTR [rbp-0x14]
  400b9c:	add    eax,edx
  400b9e:	cmp    eax,0x539   <================= 關鍵程式分析 
  400ba3:	jne    400bcc <main+0xae>
  400ba5:	mov    esi,0x400ce6
  400baa:	mov    edi,0x6021a0
  400baf:	call   400830 <_ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc@plt>
  400bb4:	mov    rax,QWORD PTR [rbp-0x8]
  400bb8:	mov    rdi,rax
  400bbb:	call   400ae3 <_Z9print_ptrPc>
  400bc0:	mov    edi,0x400cef
  400bc5:	call   4007c0 <puts@plt>
  400bca:	jmp    400bdb <main+0xbd>
  400bcc:	mov    esi,0x400cf1
  400bd1:	mov    edi,0x6021a0
  400bd6:	call   400830 <_ZStlsISt11char_traitsIcEERSt13basic_ostreamIcT_ES5_PKc@plt>
  400bdb:	mov    rax,QWORD PTR [rbp-0x8]
  400bdf:	mov    rdi,rax
  400be2:	call   400840 <free@plt>
  400be7:	mov    eax,0x0
  400bec:	leave  
  400bed:	ret    

0000000000400bee <_Z41__static_initialization_and_destruction_0ii>:
  400bee:	push   rbp
  400bef:	mov    rbp,rsp
  400bf2:	sub    rsp,0x10
  400bf6:	mov    DWORD PTR [rbp-0x4],edi
  400bf9:	mov    DWORD PTR [rbp-0x8],esi
  400bfc:	cmp    DWORD PTR [rbp-0x4],0x1
  400c00:	jne    400c29 <_Z41__static_initialization_and_destruction_0ii+0x3b>
  400c02:	cmp    DWORD PTR [rbp-0x8],0xffff
  400c09:	jne    400c29 <_Z41__static_initialization_and_destruction_0ii+0x3b>
  400c0b:	mov    edi,0x6022b1
  400c10:	call   4007e0 <_ZNSt8ios_base4InitC1Ev@plt>
  400c15:	mov    edx,0x400cc8
  400c1a:	mov    esi,0x6022b1
  400c1f:	mov    edi,0x400820
  400c24:	call   400810 <__cxa_atexit@plt>
  400c29:	leave  
  400c2a:	ret    

0000000000400c2b <_GLOBAL__sub_I__Z3geni>:
  400c2b:	push   rbp
  400c2c:	mov    rbp,rsp
  400c2f:	mov    esi,0xffff
  400c34:	mov    edi,0x1
  400c39:	call   400bee <_Z41__static_initialization_and_destruction_0ii>
  400c3e:	pop    rbp
  400c3f:	ret    

0000000000400c40 <__libc_csu_init>:
  400c40:	push   r15
  400c42:	mov    r15d,edi
  400c45:	push   r14
  400c47:	mov    r14,rsi
  400c4a:	push   r13
  400c4c:	mov    r13,rdx
  400c4f:	push   r12
  400c51:	lea    r12,[rip+0x201180]        # 601dd8 <__frame_dummy_init_array_entry>
  400c58:	push   rbp
  400c59:	lea    rbp,[rip+0x201188]        # 601de8 <__init_array_end>
  400c60:	push   rbx
  400c61:	sub    rbp,r12
  400c64:	xor    ebx,ebx
  400c66:	sar    rbp,0x3
  400c6a:	sub    rsp,0x8
  400c6e:	call   400778 <_init>
  400c73:	test   rbp,rbp
  400c76:	je     400c96 <__libc_csu_init+0x56>
  400c78:	nop    DWORD PTR [rax+rax*1+0x0]
  400c80:	mov    rdx,r13
  400c83:	mov    rsi,r14
  400c86:	mov    edi,r15d
  400c89:	call   QWORD PTR [r12+rbx*8]
  400c8d:	add    rbx,0x1
  400c91:	cmp    rbx,rbp
  400c94:	jne    400c80 <__libc_csu_init+0x40>
  400c96:	add    rsp,0x8
  400c9a:	pop    rbx
  400c9b:	pop    rbp
  400c9c:	pop    r12
  400c9e:	pop    r13
  400ca0:	pop    r14
  400ca2:	pop    r15
  400ca4:	ret    
  400ca5:	nop
  400ca6:	nop    WORD PTR cs:[rax+rax*1+0x0]

0000000000400cb0 <__libc_csu_fini>:
  400cb0:	repz ret 
```
