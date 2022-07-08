# asm2
## Category
Reverse Engineering
## Problem Description
What does asm2(0x4,0x2d) return? Submit the flag as a hexadecimal value (starting with '0x'). NOTE: Your submission for this question will NOT be in the normal flag format. [Source](https://jupiter.challenges.picoctf.org/static/ceac75672637589213b952abe32c84b3/test.S)
## Approach
```
asm2:
	<+0>:	push   ebp
	<+1>:	mov    ebp,esp                        ; ebp = esp
	<+3>:	sub    esp,0x10                       ; esp - 16
	<+6>:	mov    eax,DWORD PTR [ebp+0xc]        ; eax = 45
	<+9>:	mov    DWORD PTR [ebp-0x4],eax        ; var1 = 45
	<+12>:	mov    eax,DWORD PTR [ebp+0x8]      ; eax = 4
	<+15>:	mov    DWORD PTR [ebp-0x8],eax      ; var2 = 4
	<+18>:	jmp    0x50c <asm2+31>              ; unconditional jmp
	<+20>:	add    DWORD PTR [ebp-0x4],0x1      ; var1 += 1
	<+24>:	add    DWORD PTR [ebp-0x8],0xd1     ; var2 += 209
	<+31>:	cmp    DWORD PTR [ebp-0x8],0x5fa1   ; cmp 4 with 24481
	<+38>:	jle    0x501 <asm2+20>              ; loops condtn
	<+40>:	mov    eax,DWORD PTR [ebp-0x4]      ; eax = var1
	<+43>:	leave  
	<+44>:	ret    

```
```
24481/209 = 117
var = 45 + (1 * 118) = 163 = 0xa3
```
## Flag
0xa3
