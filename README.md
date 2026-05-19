# 4.Execution_of_NetworkCommands
## AIM :Use of Network commands in Real Time environment
## Software : Command Prompt And Network Protocol Analyzer
## Procedure: To do this EXPERIMENT- follows these steps:
<BR>
In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer 
<BR>
All commands related to Network configuration which includes how to switch to privilege mode
<BR>
and normal mode and how to configure router interface and how to save this configuration to
<BR>
flash memory or permanent memory.
<BR>
This commands includes
<BR>
• Configuring the Router commands
<BR>
• General Commands to configure network
<BR>
• Privileged Mode commands of a router 
<BR>
• Router Processes & Statistics
<BR>
• IP Commands
<BR>
• Other IP Commands e.g. show ip route etc.
<BR>

## PROGRAM:

```
import socket
import os

server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

host = "127.0.0.1"
port = 8000

server.bind((host, port))
server.listen(5)

print("Server waiting for connection...")

conn, addr = server.accept()
print("Connected to:", addr)

while True:
    data = conn.recv(1024).decode()

    if not data:
        break

    print("Command received:", data)

    result = os.popen(data).read()

    if result == "":
        result = "Command executed but no output"

    conn.send(result.encode())

conn.close()
server.close()

```

client:

```
import socket

client = socket.socket()
client.connect(("127.0.0.1", 8000))

print("Connected to server")

while True:

    print("\nAvailable Commands:")
    print("1. ping google.com")
    print("2. tracert google.com")
    print("3. nslookup google.com")
    print("4. netstat")
    print("5. exit")

    cmd = input("Enter network command: ")

    if cmd.lower() == "exit":
        break

    client.send(cmd.encode())

    result = client.recv(4096).decode()

    print("\nOutput:\n")
    print(result)

client.close()

```
## Output

<img width="801" height="571" alt="image" src="https://github.com/user-attachments/assets/041d902a-07c1-498c-83fa-1f6f6451c694" />


<img width="969" height="465" alt="image" src="https://github.com/user-attachments/assets/037b6fc0-e93c-4d4d-bd93-03ab6bfa3fca" />


<img width="859" height="369" alt="image" src="https://github.com/user-attachments/assets/9fdafeee-9ede-4502-89e9-8eed62fd7220" />


<img width="957" height="927" alt="image" src="https://github.com/user-attachments/assets/108956b5-44d2-43a4-84d2-8dd72ea803de" />


## Result
Thus Execution of Network commands Performed 
