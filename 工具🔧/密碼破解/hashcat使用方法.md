```
生成密碼本
crunch <length_start> <length_end> <key_word> -o <file>

EX：crunch 5 8 abcde -o pw.txt
```

```
加密演算法
$1  = MD5 hashing algorithm.
$2  = Blowfish Algorithm.
$2a = eksblowfish Algorithm
$5  = SHA-256 Algorithm
$6  = SHA-512 Algorithm
```

`hashcat -m 1800 <shadow_file> <dict>`  #/etc/shadow多數放這裡

`hashcat -m 1800 -a 3 <shadow_file> ?l?l?l?l --force`

-m : hash type(1800是sha512)

-a : attack mode 

      3 : 代表Brute-force模式
      0 : single 模式
      1 : 單字組合模式
      
暴力格式

      ?l：表示小寫字母，a~z
      ?u：表示大寫字母，A~Z
      ?h：代表16進位大寫，即0123456789ABCDEF
      ?H：代表16進位小寫，即0123456789abcdef
      ?s：特殊的ASCII符號，即!”#$%&’()*+,-./:;<=>?@[]^_`{|}~
      ?a：表示所有字元
      ?b：0x00 - 0xff

`https://hashcat.net/wiki/doku.php?id=hashcat` hashcat官網
