# picobrowser
## Category
Web Exploitation
## Problem Description
This website can be rendered only by picobrowser, go and catch the flag! https://jupiter.challenges.picoctf.org/problem/50522/ ([link](https://jupiter.challenges.picoctf.org/problem/50522/)) or http://jupiter.challenges.picoctf.org:50522
## Approach
Since the website can be rendered by only picobrowser we go into the file flag in the network tab of inspect element and take the curl.
```
curl 'https://jupiter.challenges.picoctf.org/problem/50522/flag' -H 'User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:101.0) Gecko/20100101 Firefox/101.0' -H 'Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8' -H 'Accept-Language: en-US,en;q=0.5' -H 'Accept-Encoding: gzip, deflate, br' -H 'Referer: https://jupiter.challenges.picoctf.org/problem/50522/' -H 'Connection: keep-alive' -H 'Cookie: _ga=GA1.2.1905962877.1654003369; _gid=GA1.2.348668275.1656037401; __cf_bm=hQIpmRokK.GD3kA78460nPjz4dAKL5L3SLK2w_WHK4I-1656042678-0-AYmt6zDDkMIlQOHZb7df7ajBcV89cFJ+iSv0zBJ89PD3P0Tgh6AJdlT2SsIEEyLmuqXkFrS0V8mZ+4XZfMfswYv1FTwJsyoBXL2f2PPfyyZuXkvDMlJ1KZcRezOapIxP8HjtUwda4ETU0CXN660WEXfyzhVaMj8YcTgS+iGr+IIa' -H 'Upgrade-Insecure-Requests: 1' -H 'Sec-Fetch-Dest: document' -H 'Sec-Fetch-Mode: navigate' -H 'Sec-Fetch-Site: same-origin' -H 'Sec-Fetch-User: ?1'
```
Changing the User-Agent to picobrowser and viewing in compressed form will reveal the flag.
```
curl 'https://jupiter.challenges.picoctf.org/problem/50522/flag' -H 'User-Agent: picobrowser' -H 'Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8' -H 'Accept-Language: en-US,en;q=0.5' -H 'Accept-Encoding: gzip, deflate, br' -H 'Referer: https://jupiter.challenges.picoctf.org/problem/50522/' -H 'Connection: keep-alive' -H 'Cookie: _ga=GA1.2.1905962877.1654003369; _gid=GA1.2.348668275.1656037401; __cf_bm=hQIpmRokK.GD3kA78460nPjz4dAKL5L3SLK2w_WHK4I-1656042678-0-AYmt6zDDkMIlQOHZb7df7ajBcV89cFJ+iSv0zBJ89PD3P0Tgh6AJdlT2SsIEEyLmuqXkFrS0V8mZ+4XZfMfswYv1FTwJsyoBXL2f2PPfyyZuXkvDMlJ1KZcRezOapIxP8HjtUwda4ETU0CXN660WEXfyzhVaMj8YcTgS+iGr+IIa' -H 'Upgrade-Insecure-Requests: 1' -H 'Sec-Fetch-Dest: document' -H 'Sec-Fetch-Mode: navigate' -H 'Sec-Fetch-Site: same-origin' -H 'Sec-Fetch-User: ?1' --compressed
```
## Flag
picoCTF{p1c0_s3cr3t_ag3nt_51414fa7}
