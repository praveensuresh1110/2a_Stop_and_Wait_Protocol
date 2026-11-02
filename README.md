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
Client:
```
import socket

print("Client program started")

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

s.connect(('localhost', 9000))

print("Connected to server!")

while True:
    data = input("Enter frame: ")

    s.send(data.encode())

    if data.lower() == "exit":
        break

    ack = s.recv(1024).decode()

    print("Acknowledgement received:", ack)

s.close()
```
Server:
```
import socket

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

s.bind(('localhost', 9000))
s.listen(1)

print("Server is waiting for client...")

c, addr = s.accept()
print("Client connected:", addr)

while True:
    data = c.recv(1024).decode()

    if not data or data.lower() == "exit":
        print("Connection closed")
        break

    print("Received frame:", data)

    c.send("ACK".encode())
    print("Acknowledgement sent")

c.close()
s.close()
```
## OUTPUT
<img width="1917" height="1078" alt="Screenshot 2026-11-02 134111" src="https://github.com/user-attachments/assets/ce37482d-a785-4f68-9e9a-01176541e0b7" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
