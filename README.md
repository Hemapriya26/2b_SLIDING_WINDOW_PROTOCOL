# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM

To write a python program to perform sliding window protocol

## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM

## Client:

```
import socket

s = socket.socket()

s.connect(('localhost', 8000))

while True:
    data = s.recv(1024).decode()

    if not data:
        break

    print(data)

    s.send("Acknowledgement received from client".encode())

s.close()
```

## Server:

```
import socket

s = socket.socket()

s.bind(('localhost', 8000))

s.listen(5)

c, addr = s.accept()

size = int(input("Enter number of frames to send : "))

l = list(range(size))

ws = int(input("Enter Window Size : "))

st = 0
i = 0

while True:
    while i < len(l):
        st = i + ws

        c.send(str(l[i:st]).encode())

        ack = c.recv(1024).decode()

        if ack:
            print(ack)
            i += ws

    break
```

## OUTPUT

<img width="1847" height="331" alt="image" src="https://github.com/user-attachments/assets/685797d4-97a8-416b-8711-3c3074e8e6ec" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
