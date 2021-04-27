### Description

![image](https://user-images.githubusercontent.com/65862031/116296864-5366d000-a7b8-11eb-8366-fec8ddc36914.png)

#### Here, we are given with a mem capture and to analyze this file, we need volatility tool which is great tool for analyzing raw files.
#### You can get volatility tool from here [https://github.com/volatilityfoundation/volatility](https://github.com/volatilityfoundation/volatility)

#### First we need to run imageinfo command to get the profile.

`vol.py -f capture.mem imageinfo`
#### This command will take some time to process the information

![image](https://user-images.githubusercontent.com/65862031/116297589-0b947880-a7b9-11eb-81ed-a04841e0bfc0.png)

#### We need a registry key that can reveal the hostname
`vol.py -f capture.mem --profile=Win7SP1x86_23418 hivelist`

![image](https://user-images.githubusercontent.com/65862031/116297834-53b39b00-a7b9-11eb-9795-80d219513fd3.png)

#### We will use the SYSTEM REGISTRY.

`vol.py -f capture.mem --profile=Win7SP1x86_23418 printkey -o 0x8941a2c0 -K 'ControlSet001\Control\ComputerName\ComputerName'`

`-o` flag is the location and `-K` flag is to list the Subkeys

![image](https://user-images.githubusercontent.com/65862031/116298240-d3da0080-a7b9-11eb-9e46-7afedc11246b.png)

`Flag : Hero{KANNIBAL}`
