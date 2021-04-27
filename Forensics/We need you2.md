### Description

![image](https://user-images.githubusercontent.com/65862031/116298388-01bf4500-a7ba-11eb-8413-12abc8a9b583.png)

In this challenge, we are supposed to find the user's name and password.

We can extract the hashes using hashdump command from volatility.

For that we need Virtual location for SAM and SYSTEM file. (We can get that using hivelist command)

![image](https://user-images.githubusercontent.com/65862031/116299102-e6086e80-a7ba-11eb-952a-7438e10a4c57.png)

The `-s` flag indicates SAM OFFSET and `-y` flag indicates SYSTEM OFFSET

Crack the hashes using JohnTheRipper tool using rockyou as the wordlist.

![image](https://user-images.githubusercontent.com/65862031/116299449-58794e80-a7bb-11eb-90e8-ac7e2e9a41cb.png)

`Flag : Hero{liverpoolfc123}`
