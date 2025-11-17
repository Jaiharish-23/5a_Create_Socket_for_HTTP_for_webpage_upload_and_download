# 5a_Create_Socket_for_HTTP_for_webpage_upload_and_download
## AIM :
To write a PYTHON program for socket for HTTP for web page upload and download
## Algorithm

1.Start the program.
<BR>
2.Get the frame size from the user
<BR>
3.To create the frame based on the user request.
<BR>
4.To send frames to server from the client side.
<BR>
5.If your frames reach the server it will send ACK signal to client otherwise it will send NACK signal to client.
<BR>
6.Stop the program
<BR>
## Program 
```python
import socket

host = "example.com"
port = 80

request = (
    "POST /upload HTTP/1.1\r\n"
    f"Host: {host}\r\n"
    "Content-Length: 11\r\n"
    "Connection: close\r\n\r\n"
    "Hello World"
)

# --- RAW SOCKET SEND ---
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect((host, port))
s.sendall(request.encode())

response = b""
while True:
    data = s.recv(4096)
    if not data:
        break
    response += data
s.close()

# --- PRINT EXACT OUTPUT ---
print("Content-Length:", len(response))
print(response.decode(errors="ignore"))

```
## OUTPUT

<img width="970" height="454" alt="image" src="https://github.com/user-attachments/assets/89a7d7f6-61ce-474c-8bac-f2daef683f48" />


## Result
Thus the socket for HTTP for web page upload and download created and Executed
