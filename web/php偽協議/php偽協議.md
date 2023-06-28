```
file:/1一访问本地文件系统

http://一访问HTTP(S)网址

ftp://一访问FTP(S)URLS

php：//一访问各个输入/输出流(1/0streams)

zlib://一压缩流

data://一数据(RFC2397)

glob://一查找匹配的文件路径模式

phar://一PHP归档

ssh2:// - Secure Shell 2

rar: - RAR

ogg://一音频流

expect:/1一处理交互式的流
```
`data://text/plain;base64,<要寫的代碼>` -> `data`傳入數據,`://text/plain`路徑,`;base64`解碼方法
`php源碼`

```php
<?

$file=$_GET["file"];
$text=$_GET["text"];
$password=$_GET["password"];
if(isset($text)&&(file_get_contents($text,'r')==="welcome to the zjctf"
  echo "<br><h1>".file_get_contents($text,"r")."</h1></br>"
  if(preg_match("/flag/"),$file){
    echo "Not now";
    exit();
  }else{
        class Flag{ //useless.php
      public $file;
      public function __tostring(){
          if(isset($this->file)){
              echo file_get_contents($this->file);
              echo"<br>";
          return("U R SO CLOSE !///COME ON PLZ");
          }
  }  
  $password = unserialize($password);
  echo $password

?>
```


|知識點||
|----|-----|
|data://|自PHP>=5.2.0起，可以使用data://数据流封装器，以传递相应格式的数据。通常可以用来执行PHP代码。一般需要用到base64编码传输|
|||
|||
