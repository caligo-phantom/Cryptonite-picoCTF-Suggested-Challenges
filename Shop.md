# Shop
## Category
Reverse Engineering
## Problem Description
Best Stuff - Cheap Stuff, Buy Buy Buy... Store Instance: source. The shop is open for business at nc mercury.picoctf.net 24851.
## Approach 
### Analysis
```
You have 40 coins
        Item            Price   Count
(0) Quiet Quiches       10      12
(1) Average Apple       15      8
(2) Fruitful Flag       100     1
(3) Sell an Item
(4) Exit
Choose an option:
```
We have 40 coins. In order to buy the "Fruitful Flag" we need 60 more coins.
```
You have 40 coins
        Item            Price   Count
(0) Quiet Quiches       10      12
(1) Average Apple       15      8
(2) Fruitful Flag       100     1
(3) Sell an Item
(4) Exit
Choose an option: 
0 
How many do you want to buy?
-10
You have 140 coins
```
Now we can buy the "Fruitful Flag".<br>
The flag is given as [112 105 99 111 67 84 70 123 98 52 100 95 98 114 111 103 114 97 109 109 101 114 95 53 51 50 98 99 100 57 56 125]<br>
This is clearly an ASCII code which can be converted to plaintext to get the flag.
## Flag
picoCTF{b4d_brogrammer_532bcd98}
