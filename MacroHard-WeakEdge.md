# MacroHard-WeakEdge
## Category
Forensics
## Problem Description
I've hidden a flag in this file. Can you find it? [Forensics is fun.pptm](https://mercury.picoctf.net/static/c00c449c3b08daaccacca6f9d5c55d49/Forensics%20is%20fun.pptm)
## Approach
When I performed binwalk "Forensics is fun.pptm" I saw there's a bunch of .zip files. I extracted it using binwalk -e "Forensics is fun.pptm".<br>
Inside the extracted folder the text inside '/Downloads/ppt/slideMasters/hidden' stood out to me.
```
Z m x h Z z o g c G l j b 0 N U R n t E M W R f d V 9 r b j B 3 X 3 B w d H N f c l 9 6 M X A 1 f Q
```
Decoding the above script at [CyberChef](https://gchq.github.io/CyberChef/) using 'From Base64' I was able to discover the flag.
## Flag
picoCTF{D1d_u_kn0w_ppts_r_z1p5}
