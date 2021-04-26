## Description

![image](https://user-images.githubusercontent.com/65862031/116081382-d3594100-a6b7-11eb-810d-999de0866e24.png)


#### The website is a dark web market containing different type of attacks to buy. (Like DDOS, Malware,etc)

![image](https://user-images.githubusercontent.com/65862031/116081614-19160980-a6b8-11eb-9585-066ed8581362.png)

If we click on the Buy button, a cookie get's generated containing the basket list. (like JWT)
We can decode the cookie at the following [website](https://jwt.io/).

![image](https://user-images.githubusercontent.com/65862031/116081892-6befc100-a6b8-11eb-9f8e-1f2bf3741bb3.png)

There isn't any kind of algorithm involved in generating the cookies. That means we can modify the cookie and can even make it malicious.

The website looks like a node application, so i will insert a node command to process. The cookie loads its content at `/basket`

![image](https://user-images.githubusercontent.com/65862031/116082206-c4bf5980-a6b8-11eb-8c88-8b117a978ff0.png)

![image](https://user-images.githubusercontent.com/65862031/116082361-f0dada80-a6b8-11eb-944c-aa750b5a9f7d.png)

![image](https://user-images.githubusercontent.com/65862031/116082379-f59f8e80-a6b8-11eb-937b-ef173017bd3e.png)

We get Remote Code Execution, so let's try to list the files in the working directory.

`require('fs').readdirSync('.').toString()` 

![image](https://user-images.githubusercontent.com/65862031/116082672-4e6f2700-a6b9-11eb-9a23-c0b9bf5b42e1.png)

`require('fs').readFileSync('flag.txt')`

And we get the flag.

![image](https://user-images.githubusercontent.com/65862031/116082821-75c5f400-a6b9-11eb-86be-a607971cbf98.png)




