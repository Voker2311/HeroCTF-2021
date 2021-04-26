### Description

![image](https://user-images.githubusercontent.com/65862031/116141278-19cd9080-a6f6-11eb-9732-df3c5136947e.png)

We have given the encrypted flag and the script used to encrypt that flag. Let's check it out.

```
#!/usr/bin/env python3
from os import urandom
from random import randint
from pwn import xor

input_img = open("flag.png", "rb").read()
outpout_img = open("flag.png.enc", "wb")

key = urandom(8) + bytes([randint(0, 9)])
outpout_img.write(xor(input_img, key))
```
So the key is 9 bytes long, we can get the key as we already know the PNG file headers. 
The first 9 bytes of PNG file are as follows:

`89 50 4E 47 0D 0A 1A 0A 00`

If we perform XOR operation with these bytes, we will get the key and then we can decrypt the rest of the bytes.

```
#!/usr/bin/env python

from pwn import xor

file = open('flag.png.enc',"rb")
raw = file.read()

array = bytearray(raw)
to_xor = [137,80,78,71,13,10,26,10,0]

key = [array[x] ^ to_xor[x] for x in range(9)]

img = open("flag.png","wb")

img.write(xor(raw,key))
```
![image](https://user-images.githubusercontent.com/65862031/116141855-db84a100-a6f6-11eb-96ed-bd0a02be37da.png)

