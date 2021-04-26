## This challenge falls under the category of Web Exploitation
### Description 

![image](https://user-images.githubusercontent.com/65862031/116077570-41e7d000-a6b3-11eb-9197-40caa41e13b1.png)

### Let's visit the URL and view the source page to get more info!

![image](https://user-images.githubusercontent.com/65862031/116077673-5af08100-a6b3-11eb-8f78-331071a6c924.png)

Download the login.php.bak file and analyze it. 

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
`password LIKE :password` looks intersting as we can inject something like 'a%' and if the password starts with 'a' then we are logged in. 
We can FUZZ the first letter using Burp Suite's Intruder TAB.

![image](https://user-images.githubusercontent.com/65862031/116078396-2b8e4400-a6b4-11eb-9a4b-dd751dd57d2e.png)

Add the following sets of characters "ABCDEFGHIJKLMNOPQRSTUVWXYabcdefghijklmnopqrstuvwxyz" and start the attack.

And we get the flag

![image](https://user-images.githubusercontent.com/65862031/116078829-b7a06b80-a6b4-11eb-816a-7dae534db9c1.png)



