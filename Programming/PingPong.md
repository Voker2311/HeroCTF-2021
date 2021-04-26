### Description

![image](https://user-images.githubusercontent.com/65862031/116143238-834e9e80-a6f8-11eb-9256-eab89880ddb4.png)

![image](https://user-images.githubusercontent.com/65862031/116143335-a711e480-a6f8-11eb-8c80-cda187ab1b44.png)

The "I" and "O" in the `output.txt` looks like 1s and 0s. So will write a script replacing 1s and 0s. 

```
#!/usr/bin/env python

file = open('output.txt')
raw = file.readlines()

out = ""
for i in raw:
    if "I" in i.strip():
        out += "1"
    else:
        out += "0"
flag = ""
for i in range(0,176,8):
     val = int(out[i:i+8],2)
     flag += chr(val)

print flag
```

#### Flag found: Hero{p1n6_p0n6_15_fun}
