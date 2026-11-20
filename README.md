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

## CLIENT

```
import socket

client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

client.connect(('localhost', 12345))

print("Connected to server!")

while True:
    msg = input("Client: ")
    client.send(msg.encode())

    if msg.lower() == "exit":
        break

    reply = client.recv(1024).decode()
    print("Server:", reply)

    if reply.lower() == "exit":
        break

client.close()
```
## SERVER

```
import socket

server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

server.bind(('localhost', 12345))

server.listen(1)
print("Server is waiting for client...")

conn, addr = server.accept()
print("Client connected!")

while True:
    msg = conn.recv(1024).decode()

    if msg.lower() == "exit":
        print("Client disconnected")
        break

    print("Client:", msg)

    reply = input("Server: ")
    conn.send(reply.encode())

    if reply.lower() == "exit":
        break

conn.close()
server.close()
```

## OUPUT
<img width="680" height="165" alt="Screenshot 2026-11-20 101958" src="https://github.com/user-attachments/assets/24f3681b-c78b-4b5d-aba3-962a4c8733a1" />

<img width="548" height="138" alt="Screenshot 2026-11-20 101946" src="https://github.com/user-attachments/assets/b195b1a3-d619-421d-bfda-423408d8db57" />


## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
