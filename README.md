# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
1) Server:
```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)

print("Waiting for connection...")
conn, addr = s.accept()
print("Connected to", addr)

while True:
    data = conn.recv(1024).decode()
    if not data:
        break

    print("Frame received:", data)
    conn.send("ACK".encode())

conn.close()
```

2) Client:
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

n = int(input("Enter number of frames: "))

for i in range(n):
    msg = input("Enter frame: ")
    s.send(msg.encode())

    ack = s.recv(1024).decode()
    print("Received:", ack)

s.close()
``` 
## OUTPUT
1) Server:
<img width="1858" height="779" alt="Screenshot 2026-05-15 134804" src="https://github.com/user-attachments/assets/ce37acf2-41be-462d-a328-c8f0e00ff477" />

2) Client:
<img width="1336" height="609" alt="Screenshot 2026-05-15 140204" src="https://github.com/user-attachments/assets/a3b80295-3c83-49f8-8a89-4ecb8ff7806b" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
