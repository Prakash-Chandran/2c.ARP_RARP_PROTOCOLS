# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP
```
CLIENT:

import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
 ip=c.recv(1024).decode()
 try:
 c.send(address[ip].encode())
 except KeyError:
 c.send("Not Found".encode())
```
SERVER:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
 ip=input("Enter logical Address : ")
 s.send(ip.encode())
 print("MAC Address",s.recv(1024).decode())
```

## OUPUT - ARP

CLIENT:

![2c ARP client](https://github.com/Prakash-Chandran/2c.ARP_RARP_PROTOCOLS/assets/147120899/2d1fe8a8-760c-4f4e-a340-baf2282f762e)

SERVER:

![2c ARP server](https://github.com/Prakash-Chandran/2c.ARP_RARP_PROTOCOLS/assets/147120899/d75bc271-0828-46f3-919e-799527436e4c)


## PROGRAM - RARP
```
CLIENT:

import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
 ip=c.recv(1024).decode()
 try:
 c.send(address[ip].encode())
 except KeyError:
 c.send("Not Found".encode())
```
SERVER:
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP
CLIENT :

![2c RARP client](https://github.com/Prakash-Chandran/2c.ARP_RARP_PROTOCOLS/assets/147120899/4da3b1ba-b6b5-4550-8c53-1c2fae6eb26d)


SERVER:

![2c RARP server](https://github.com/Prakash-Chandran/2c.ARP_RARP_PROTOCOLS/assets/147120899/72fc6783-dfb5-4d6f-80c4-b6192d1b6075)


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
