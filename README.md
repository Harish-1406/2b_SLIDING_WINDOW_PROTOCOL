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
server.py
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter window size : "))
st=0
i=0
while True:
    while(i<len(l)):
        st+=s
        c.send(str(l[i:st]).encode())
        ack=c.recv(1024).decode()
        if ack:
            print(ack)
            i+=5
```

client.py

```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recived from the server".encode())
```

## OUPUT
![Screenshot 2025-03-20 104415](https://github.com/user-attachments/assets/43542601-a9f4-4e9c-bcc6-4142d6b9dd1f)
![Screenshot 2025-03-20 104435](https://github.com/user-attachments/assets/2b4f4dc3-197a-4ef8-859e-e5013292645d)
![Screenshot 2025-03-20 104443](https://github.com/user-attachments/assets/0252517d-754d-4f01-a9a9-dc053bab62b9)





## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
