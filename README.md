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
## PROGRAM - ARP:
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
```
SERVER: 
 
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

<img width="801" height="167" alt="image" src="https://github.com/user-attachments/assets/ef16fa1e-b1b1-4061-a1d0-5fee487d05b5" />

SERVER:

<img width="793" height="225" alt="image" src="https://github.com/user-attachments/assets/feaad6ee-9a2a-4c07-9728-2604ca761ec8" />


## PROGRAM - RARP:

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
```
SERVER: 
 
import socket 
s=socket.socket() 
s.connect(('localhost',9000)) 
while True: 
    ip=input("Enter MAC Address : ") 
    s.send(ip.encode()) 
    print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP:
CLIENT :
<img width="790" height="174" alt="image" src="https://github.com/user-attachments/assets/3ed87389-80d1-4151-ac63-8fecca7f7add" />

SERVER:
<img width="794" height="207" alt="image" src="https://github.com/user-attachments/assets/cbf8847a-effc-4f49-b987-b031cf7f4572" />


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
