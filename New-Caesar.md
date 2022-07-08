# New-Caesar
## Category
Cryptography
## Problem Description<br>
We found a brand new type of encryption, can you break the secret code? (Wrap with picoCTF{}) apbopjbobpnjpjnmnnnmnlnbamnpnononpnaaaamnlnkapndnkncamnpapncnbannaapncndnlnpna new_caesar.py
## Approach
### Analyzing the Code
```python
import string

LOWERCASE_OFFSET = ord("a")
ALPHABET = string.ascii_lowercase[:16]

def b16_encode(plain):
	enc = ""
	for c in plain:
		binary = "{0:08b}".format(ord(c))
		enc += ALPHABET[int(binary[:4], 2)]
		enc += ALPHABET[int(binary[4:], 2)]
	return enc

def shift(c, k):
	t1 = ord(c) - LOWERCASE_OFFSET
	t2 = ord(k) - LOWERCASE_OFFSET
	return ALPHABET[(t1 + t2) % len(ALPHABET)]

flag = "redacted"
key = "redacted"
assert all([k in ALPHABET for k in key])
assert len(key) == 1

b16 = b16_encode(flag)
enc = ""
for i, c in enumerate(b16):
	enc += shift(c, key[i % len(key)])
print(enc)
```
The assert statements show that the key needs to be one character and be a letter between a to p. It is necessary to change the values of flag and key in order to get an output of "apbopjbobpnjpjnmnnnmnlnbamnpnononpnaaaamnlnkapndnkncamnpapncnbannaapncndnlnpna".<br>Testing the code "binary = "{0:08b}".format(ord(c))", it outputs the ascii value of c in binary form. The following two lines split the binary number in half, in which the integer value is the index of a letter in the list ALPHABET that will be added to the variable encryption.<br>The final process of encrypting the flag is above. Usine enumerate loops through the values of b16, assigning i to the index at a particular point and c the value. The values for the function include the values of b16 and the key (len(key) = 1, i%1 = 0).<br>The function shift returns a value in ALPHABET at the index ascii value of the c minus 97 plus the ascii value of the key minus 97 mod 16.
### Solution
```python
import string
import binascii
enc ="apbopjbobpnjpjnmnnnmnlnbamnpnononpnaaaamnlnkapndnkncamnpapncnbannaapncndnlnpna"
ALPHABET = string.ascii_lowercase[:16] 

b16 = []

for i in range(len(ALPHABET)):
	b16.append("")

for i in enc:
	for k in range(len(ALPHABET)):
		index = ALPHABET.index(i)
		if(k <= index):
			b16[k]+=chr(index -k+97)
		else:
			b16[k]+=chr(index +16-k+97)

for k in range(len(ALPHABET)):
    flag=""
    b=b16[k]
    for i in range(0, len(b), 2):
    	if(b[i+1] in ALPHABET and b[i] in ALPHABET):
		    index1 = ALPHABET.index(b[i])
		    index2 = ALPHABET.index(b[i+1])
		    flag+= chr((index1 <<4) +index2)
    print(flag)
```
All outputs include invalid characters except et_tu?_23217b54456fb10e908b5e87c6e89156.
## Flag
et_tu?_23217b54456fb10e908b5e87c6e89156
