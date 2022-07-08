# asm1
## Category 
Reverse Engineering
## Problem Description
What does asm1(0x2e0) return? Submit the flag as a hexadecimal value (starting with '0x'). NOTE: Your submission for this question will NOT be in the normal flag format. [Source](https://jupiter.challenges.picoctf.org/static/f1c2358ff7d1e9386e41552c549cf2f6/test.S)
## Approach
```
asm1:
	<+0>:	push   ebp
	<+1>:	mov    ebp,esp
	<+3>:	cmp    DWORD PTR [ebp+0x8],0x3fb ; 1019
	<+10>:	jg     0x512 <asm1+37> 	  	 ; jump if greater
	<+12>:	cmp    DWORD PTR [ebp+0x8],0x280 ; 640
	<+19>:	jne    0x50a <asm1+29> 	  	 ; jump if not equal
	<+21>:	mov    eax,DWORD PTR [ebp+0x8]
	<+24>:	add    eax,0xa
	<+27>:	jmp    0x529 <asm1+60>
	<+29>:	mov    eax,DWORD PTR [ebp+0x8] 
	<+32>:	sub    eax,0xa 		  	 ; 726
	<+35>:	jmp    0x529 <asm1+60> 	  	 ; jump
	<+37>:	cmp    DWORD PTR [ebp+0x8],0x559
	<+44>:	jne    0x523 <asm1+54>
	<+46>:	mov    eax,DWORD PTR [ebp+0x8]
	<+49>:	sub    eax,0xa
	<+52>:	jmp    0x529 <asm1+60>
	<+54>:	mov    eax,DWORD PTR [ebp+0x8]
	<+57>:	add    eax,0xa
	<+60>:	pop    ebp
	<+61>:	ret    			  	 ; 726 -> 0x2d6

```
## Flag
0x2d6
