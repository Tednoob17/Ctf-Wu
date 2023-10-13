This Challenge is proposed by [Theblackside Platform](https://theblackside.fr) 
*Author* : [TRIKKSS](https://twitter.com/0xTRIKKSS) 
*Chall Link* : [PNG_BREAK1](https://theblackside.fr/challenges/steganographie/PNG_BREAK-1) 
*File* : [file](http://tbsctf.fr/steganographie/PNG_BREAK-1.png) 
Date: 02/09/2023

After download the chall file i begin with the basics command 
```bash
j3kyll@blkkk-van-gogh ~/Documents/Chall/TheBlackSide/Steg$ file PNG_BREAK-1.png                                                 
PNG_BREAK-1.png: data
```
Personally i hate when i see that this file is "data" so i decide to see the hexdump of  this file with `xxd` 
```bash
j3kyll@blkkk-van-gogh ~/Documents/Chall/TheBlackSide/Steg$ xxd PNG_BREAK-1.png|head                                      127 ↵  
00000000: 8955 7e67 0d0a 1a0a 0000 000d 4948 4452  .U~g........IHDR
00000010: 0000 0491 0000 0288 0802 0000 004f 25fc  .............O%.
00000020: 8c00 0000 0173 5247 4200 aece 1ce9 0000  .....sRGB.......
00000030: 0004 6741 4d41 0000 b18f 0bfc 6105 0000  ..gAMA......a...
00000040: 0009 7048 5973 0000 0ec3 0000 0ec3 01c7  ..pHYs..........
00000050: 6fa8 6400 0043 8c49 4441 5478 5eed ddcd  o.d..C.IDATx^...
00000060: 79db 3cb3 0050 5795 45ba 7937 a925 cb14  y.<..PW.E.y7.%..
00000070: 9275 da48 01e9 e26b e05e c872 1c79 4490  .u.H...k.^.r.yD.
00000080: 2008 5243 f9e0 399b 496c 99c4 ff90 94f4   .RC..9.Il......
00000090: f27f ff03 0000 20a9 1803 0000 9047 8c01  ...... ......G..
```

This output is not conventional for verify this affirmation i check The png magic number 
Here : [Magic number](https://en.wikipedia.org/wiki/List_of_file_signatures) 
After searching PNG in the table i see this : 
`  89 50 4E 47 0D 0A 1A 0A`|`‰PNG␍␊␚␊ ` 
and i compare with my output and i see that the two output is different so for rewrite the header of this file i use `hexedit`

```bash
j3kyll@blkkk-van-gogh ~/Documents/Chall/TheBlackSide/Steg$ hexedit --help                                                       
usage: hexedit [-s | --sector] [-m | --maximize] [-l<n> | --linelength <n>] [--color] [-h | --help] filename
```

```bash 
j3kyll@blkkk-van-gogh ~/Documents/Chall/TheBlackSide/Steg$ hexedit --color PNG_BREAK-1.png
```
Let's go with color 
Info : For see the help press `F1` for modifie a characters one by one press `tab` two time
After modifying the header i obtain 
` 00000000   89 50 4E 47  0D 0A 1A 0A  00 00 00 0D  49 48 44 52  00 00 04 91  00 00 02 88  08 02 00 00  .PNG........IHDR............`
For Save press `F2` and for Save and exit press `CTRL +X` 

for verify this file now 
```bash 
j3kyll@blkkk-van-gogh ~/Documents/Chall/TheBlackSide/Steg$ file PNG_BREAK-1.png                                                 
PNG_BREAK-1.png: PNG image data, 1169 x 648, 8-bit/color RGB, non-interlaced
```
Ok and when i open 
![output](./img/output-break.png) 

Flag :  TBS{check_magig_numb3r}  
