# Compress-and-Attack
## Category
Cryptography
## Problem Description
Your goal is to find the flag. [compress_and_attack.py](https://mercury.picoctf.net/static/24f9e793900aeba6f183dce8e0b14e90/compress_and_attack.py) nc mercury.picoctf.net 33976
## Approach
Salsa20 is a cipher that was submitted to eSTREAM project, running from 2004 to 2008, which was supposed to promote development of stream ciphers. It is considered to be a well-designed and efficient algorithm. There aren't any known and effective attacks on the family of Salsa20 ciphers.<br>
I input picoCTF{ which is the known part of the plaintext, this gives me a ciphertext of length 30 instead of 35, so some compression happened.<br>
```python
from pwn import *
import string

sh = remote("mercury.picoctf.net", 33976)

def oracle(text):
    sh.recvuntil("encrypted:")
    sh.sendline(text)
    sh.recvline()
    sh.recvline()
    return int(sh.recvline().decode())

known = "picoCTF{sheriff_you_"

length = oracle(known)
print(known, end="")

current = ""
while current != "}":
    for c in string.printable:
        if oracle(known + c) == length:
            known += c
            current = c
            print(c, end="")
            break
```
## Flag
picoCTF{sheriff_you_solved_the_crime}
