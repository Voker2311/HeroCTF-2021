## Description

![image](https://user-images.githubusercontent.com/65862031/116079848-f256d380-a6b5-11eb-976c-05c027bfa800.png)

Visiting the page source again, I was able to get the following.

![image](https://user-images.githubusercontent.com/65862031/116079946-161a1980-a6b6-11eb-985d-30f883bea009.png)

#### Contents of admin.php.bak

```
<?php

if (session_status() == PHP_SESSION_NONE) {
    session_start();
}

if (!(isset($_SESSION["logged"]) && $_SESSION["logged"] === true)) {
    header("Location: /index.php?error=You are not admin !");
}

echo "Flag : " . getenv("FLAG_MARK3TING");
```

The way I got the flag is that I intercepted the admin.php request in Burp Suite and requested for response.

![image](https://user-images.githubusercontent.com/65862031/116080160-57aac480-a6b6-11eb-8071-6ba73fbd1086.png)

![image](https://user-images.githubusercontent.com/65862031/116080253-75782980-a6b6-11eb-86aa-da4b5f5424b4.png)


Flag found: Hero{r3d1r3c710n_c4n_b3_d4n63r0u5_57395379}
