```python
import socket 

target_host = "127.0.0.1"
target_port = 9997

# create socket object
client = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

#connect client 
client.connect((target_host,target_port))

#send data
client.sendto(b"AAABBBCCC",(target_host,target_port))

#receive
data, addr = client.recvfrom(4096)

print(data.decode())
client.close()
```

socket.SOCK_DGRAM = 傳輸類型為UDP

`recvfrom()`函數接受數據

```GPT
连接性：

TCP是面向连接的协议，意味着在数据传输之前，必须先建立一个连接，然后才能进行数据传输。这个连接是可靠的，双方都会确认数据的接收。
UDP是无连接的协议，数据可以直接发送，不需要建立连接。UDP不提供连接确认或可靠性保证，因此数据可能会在传输过程中丢失或乱序。

可靠性：
TCP提供可靠性传输，确保数据按顺序到达，且不会丢失。如果数据包丢失或损坏，TCP会重新发送它们，直到接收方确认。

UDP不提供可靠性，因此数据包可能会丢失或到达的顺序可能与发送顺序不同。
这对于实时应用程序（如音频和视频流）可能是可接受的，因为它们更注重实时性而不是完整性。

流量控制：

TCP具有流量控制机制，以避免过多的数据被发送到网络，从而导致拥塞。它使用窗口大小来控制发送速率。
UDP不具备流量控制，发送方可以以最大速度发送数据，而不考虑网络的拥塞情况。
开销：

TCP需要更多的开销来维护连接状态、序号和确认，因此它在头部上会比UDP更大。
UDP的头部相对较小，因此在数据包大小方面更加高效。

应用场景：
TCP适用于需要可靠性和顺序传输的应用程序，如网页浏览、电子邮件、文件传输等。
UDP适用于需要低延迟、实时性的应用程序，如音频和视频流、在线游戏、DNS查询等。
总之，TCP和UDP都有其自己的用途，具体取决于应用程序的要求。
TCP适合对数据完整性和可靠性有要求的场景，而UDP适合对实时性要求较高，可以容忍一些数据丢失的场景。
网络应用程序通常会根据其需求选择使用其中之一或同时使用两者。



````
