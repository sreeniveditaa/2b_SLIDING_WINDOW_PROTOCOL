# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
# DATE :
## AIM

To write a python program for implementation of sliding window protocol.

## ALGORITHM:

1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
   
## PROGRAM

Client
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
st=0
i=0
while True:
    while(i<len(l)):
        st+=s
        c.send(str(l[i:st]).encode())
        ack=c.recv(1024).decode()
        if ack:
            print(ack)
            i+=s
```
Server

```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement received from the server".encode())

```

## OUPUT

Client

![{FDC6E212-16C4-464F-94AA-679346DF463D}](https://github.com/user-attachments/assets/4d4ef297-0cdd-4004-8048-4b9ece8f4ddf)


Server 

![{26D8463D-92D8-4EF9-95BE-1599489B1994}](https://github.com/user-attachments/assets/7d2cf2e3-226a-400a-b126-04950f4faa98)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
