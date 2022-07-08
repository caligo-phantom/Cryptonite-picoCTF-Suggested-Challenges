# Wireshark-doo-dooo-do-doo...
## Category
Forensics
## Problem Description
Can you find the flag? [shark1.pcapng](https://mercury.picoctf.net/static/4c996ecfb7fbada15a9799511f24dc99/shark1.pcapng).
## Approach
I opened the downloadable file in Wireshark and followed the TCP Stream.<br>
Stream 5 (tcp.stream eq 5) contained something that looked promising
```
Gur synt vf cvpbPGS{c33xno00_1_f33_h_qrnqorrs}
```
After decoding `Gur synt vf cvpbPGS{c33xno00_1_f33_h_qrnqorrs}` with ROT13 at [CyberChef](https://gchq.github.io/CyberChef/), the flag was revealed.
## Flag
picoCTF{p33kab00_1_s33_u_deadbeef}
