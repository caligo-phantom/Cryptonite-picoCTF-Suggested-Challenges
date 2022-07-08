# tunn3l-v1s10n
## Category
Forensics
## Problem Description
We found this [file](https://mercury.picoctf.net/static/21c07c9dd20cd9f2459a0ae75d99af6e/tunn3l_v1s10n). Recover the flag.
## Approach
The downloadable file is of an unknown file type.
```
ExifTool Version Number         : 11.88
File Name                       : tunn3l_v1s10n.bmp
Directory                       : .
File Size                       : 2.8 MB
File Modification Date/Time     : 2022:06:05 11:07:44+05:30
File Access Date/Time           : 2022:06:05 11:10:19+05:30
File Inode Change Date/Time     : 2022:06:05 11:10:19+05:30
File Permissions                : rw-rw-r--
File Type                       : BMP
File Type Extension             : bmp
MIME Type                       : image/bmp
BMP Version                     : Windows V3
Image Width                     : 1134
Image Height                    : 832
Planes                          : 1
Bit Depth                       : 24
Compression                     : None
Image Length                    : 2893400
Pixels Per Meter X              : 5669
Pixels Per Meter Y              : 5669
Num Colors                      : Use BitDepth
Num Important Colors            : All
Image Size                      : 1134x832
Megapixels                      : 0.943
```
Running exiftool we discover that the given file is a bitmap image (bmp).
Opening the file in Bless Hex Editor I discovered that the number of bytes in the DIB header are wrong and the number of bits per pixel are also wrong I realized that I need to edit the bytes at offset 0x0e and 0x1c.
```
42 4d 8e 26 2c 00 00 00 00 00 ba d0 00 00 ba d0
00 00 6e 04 00 00 32 01
```
The correct bytes are as follows.
```
42 4d 8e 26 2c 00 00 00 00 00 ba d0 00 00 28 00
00 00 6e 04 00 00 40 03
```
Moving the file 'tunn3lv1s10n' to 'tunn3lv1s10n.bmp' we get the final image as follows.<br>

![Final Image](https://github.com/caligo-phantom/tunn3l-v1s10n/blob/main/tunn3l_v1s10n.bmp)

## Flag
picoCTF{qu1t3_a_v13w_2020}
