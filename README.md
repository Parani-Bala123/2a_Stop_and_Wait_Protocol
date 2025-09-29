# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
## client
```
import socket


host = '127.0.0.1'  
port = 5000          

server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server_socket.bind((host, port))
server_socket.listen(1)

print("Server is listening on", host, ":", port)
conn, addr = server_socket.accept()
print("Connection from:", addr)

while True:
    data = conn.recv(1024).decode()
    if not data:
        break
    print("Client:", data)
    message = input("Server: ")
    conn.send(message.encode())

conn.close()
```
## server
```
import socket


host = '127.0.0.1'   
port = 5000

client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client_socket.connect((host, port))

while True:
    message = input("Client: ")
    client_socket.send(message.encode())
    data = client_socket.recv(1024).decode()
    print("Server:", data)

client_socket.close()
```
## OUTPUT
<img width="1180" height="249" alt="image" src="https://github.com/user-attachments/assets/16af124c-6915-4f7a-b8a6-665bdb5630df" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
