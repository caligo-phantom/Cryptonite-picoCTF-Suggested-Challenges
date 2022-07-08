# Easy-Peasy
## Category
Cryptography
## Problem Description
A one-time pad is unbreakable, but can you manage to recover the flag? (Wrap with picoCTF{}) nc mercury.picoctf.net 11188 [otp.py](https://mercury.picoctf.net/static/3cdfde8de474ba94b23aba4a2dfc7eeb/otp.py)
## Approach 
I used the command below to produce the key for the flag.
```
python3 -c "print('\x00'*(50000-32)+'\n'+'\x00'*32)" | nc mercury.picoctf.net 36981 
```

Then I used CyberChef to produce the flag.<br>

![CyberChef](./CyberChef.png)

## Key
picoCTF{7904ff830f1c5bba8f763707247ba3e1}
