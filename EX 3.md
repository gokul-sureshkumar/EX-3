# EX-3 IMPLEMENTATION OF SLIDING WINDOW PROTOCOL

DATE :


AIM :
```
To write a python program to perform sliding window protocol
```
ALGORITHM :
```
1.Start the program.
2.Get the frame size from the user
3.To create the frame based on the user request.
4.To send frames to server from the client side.
5.If your frames reach the server it will send ACK signal to client otherwise it will send NACKsignal to client.
6.Stop the program.
```

PROGRAM :
## Client Program:
``` python
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
## Server Program:
``` python 

import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recived from the server".encode())
```
OUTPUT :
## Server Output:
![image](https://github.com/gokul-sureshkumar/EX-3/assets/121148715/5316854e-5d91-4b2b-b6d9-cd75200fad23)
## Client Output:
![image](https://github.com/gokul-sureshkumar/EX-3/assets/121148715/4ac6bf4f-9edc-4461-a96a-303d89e1a7ad)



RESULT:
```
Thus, python program to perform stop and wait protocol And Sliding Window Protocol was successfully executed.
```

