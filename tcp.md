```pythons
import socket 

target_host = "www.google.com"
target_port = 80

# create socket object
client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

#connect client 
client.connect((target_host,target_port))

#send data
client.send(b"GET / HTTP/1.1\r\nHost: google.com\r\n\r\n")

#receive
response = client.recv(4096)

print(response.decode())
client.close()
```
# 1. AF_INET = IPv4 或 主機名 ， SOCK_STERAM = TCP 客戶端 -> 連接客戶端
# 2. 發送bytes類型的數據
# 3. 收，print，關客戶端
