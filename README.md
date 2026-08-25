# 3b.CREATION FOR CHAT USING TCP SOCKETS
## AIM
To write a python program for creating Chat using TCP Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.
## PROGRAM
## Server.py
```
import socket
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
host = '127.0.0.1'
port = 5000
server_socket.bind((host, port))
server_socket.listen(1)
print("Waiting for client connection...")
client_socket, addr = server_socket.accept()
print("Connected to:", addr)
while True:
    client_message = client_socket.recv(1024).decode()
    if not client_message:
        break
    print("Client:", client_message)
    if client_message.lower() == "bye":
        break
    message = input("Server: ")
    client_socket.send(message.encode())
    if message.lower() == "bye":
        break
client_socket.close()
server_socket.close()
print("Connection closed.") 
```

## Client.py
```
import socket
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
host = '127.0.0.1'
port = 5000
client_socket.connect((host, port))
print("Connected to server")
while True:
    message = input("Client: ")
    client_socket.send(message.encode())
    if message.lower() == "bye":
        break
    server_message = client_socket.recv(1024).decode()
    if not server_message:
        break
    print("Server:", server_message)
    if server_message.lower() == "bye":
        break
client_socket.close()
print("Connection closed.") 
```
## OUPUT

<img width="1920" height="1080" alt="Screenshot 2026-08-25 140557" src="https://github.com/user-attachments/assets/76bf6817-6281-4450-9468-2399c2f5e3f8" /> <br> 

<img width="1920" height="1080" alt="Screenshot 2026-08-25 140620" src="https://github.com/user-attachments/assets/427c1ace-6314-4783-bb28-e7163fdec504" />

## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
