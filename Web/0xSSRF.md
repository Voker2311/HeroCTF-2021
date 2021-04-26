## Description

![image](https://user-images.githubusercontent.com/65862031/116079157-1960d580-a6b5-11eb-8cc3-a62c85b685af.png)

#### The website looks like a proxy service accepting URL from the end user.

![image](https://user-images.githubusercontent.com/65862031/116079329-4ad9a100-a6b5-11eb-8745-05718479226f.png)

We can try certain SSRF Payloads. Payload can be found [here](https://book.hacktricks.xyz/pentesting-web/ssrf-server-side-request-forgery).

We can only access the flag from the localhost. So I tried the following payload to get localhost access.

``` Payload used: http://0:3000/flag ```

![image](https://user-images.githubusercontent.com/65862031/116079705-c0de0800-a6b5-11eb-8e2c-394ce0d6cfd2.png)
