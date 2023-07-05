0x08. Networking basics #1
DevOps                                                      Network                                     SysAdmin

Learning Objectives
In this project, I have learnt the following concepts
•	What is localhost/127.0.0.1
•	What is 0.0.0.0
•	What is /etc/hosts
•	How to display your machine’s active network interfaces

Tasks
0. Change your home IP
A Bash script that configures an Ubuntu server with the below requirements.
Requirements:
•	localhost resolves to 127.0.0.2
•	facebook.com resolves to 8.8.8.8.
•	The checker is running on Docker, so make sure to read this

1. Show attached IPs
A Bash script that displays all active IPv4 IPs on the machine it’s executed on.

2. Port listening on localhost
Write a Bash script that listens on port 98 on localhost.
Terminal 0
Starting my script.
sylvain@ubuntu$ sudo ./100-port_listening_on_localhost
Terminal 1
Connecting to localhost on port 98 using telnet and typing some text.
sylvain@ubuntu$ telnet localhost 98
Trying 127.0.0.2...
Connected to localhost.
Escape character is '^]'.
Hello world
test
Terminal 0
Receiving the text on the other side.
sylvain@ubuntu$ sudo ./100-port_listening_on_localhost
Hello world
test


