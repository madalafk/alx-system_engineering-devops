0x09. Web infrastructure design
DevOps             |      SysAdmin                         |        web infrastructure
Tasks
0. Simple web stack
A lot of websites are powered by simple web infrastructure, a lot of time it is composed of a single server with a LAMP stack.
On a whiteboard, design a one server web infrastructure that hosts the website that is reachable via www.foobar.com. Start your explanation by having a user wanting to access your website.
Requirements:
•	You must use:
o	1 server
o	1 web server (Nginx)
o	1 application server
o	1 application files (your code base)
o	1 database (MySQL)
o	1 domain name foobar.com configured with a www record that points to your server IP 8.8.8.8
•	You must be able to explain some specifics about this infrastructure:
o	What is a server
o	What is the role of the domain name
o	What type of DNS record www is in www.foobar.com
o	What is the role of the web server
o	What is the role of the application server
o	What is the role of the database
o	What is the server using to communicate with the computer of the user requesting the website
•	You must be able to explain what the issues are with this infrastructure:
o	SPOF
o	Downtime when maintenance needed (like deploying new code web server needs to be restarted)
o	Cannot scale if too much incoming traffic
Please, remember that everything must be written in English to further your technical ability in a variety of settings.


1. Distributed web infrastructure
On a whiteboard, design a three server web infrastructure that hosts the website www.foobar.com.
Requirements:
•	You must add:
o	2 servers
o	1 web server (Nginx)
o	1 application server
o	1 load-balancer (HAproxy)
o	1 set of application files (your code base)
o	1 database (MySQL)
•	You must be able to explain some specifics about this infrastructure:
o	For every additional element, why you are adding it
o	What distribution algorithm your load balancer is configured with and how it works
o	Is your load-balancer enabling an Active-Active or Active-Passive setup, explain the difference between both
o	How a database Primary-Replica (Master-Slave) cluster works
o	What is the difference between the Primary node and the Replica node in regard to the application
•	You must be able to explain what the issues are with this infrastructure:
o	Where are SPOF
o	Security issues (no firewall, no HTTPS)
o	No monitoring
Please, remember that everything must be written in English to further your technical ability in a variety of settings.

 2. Secured and monitored web infrastructure
On a whiteboard, design a three server web infrastructure that hosts the website www.foobar.com, it must be secured, serve encrypted traffic, and be monitored.
Requirements:
•	You must add:
o	3 firewalls
o	1 SSL certificate to serve www.foobar.com over HTTPS
o	3 monitoring clients (data collector for Sumologic or other monitoring services)
•	You must be able to explain some specifics about this infrastructure:
o	For every additional element, why you are adding it
o	What are firewalls for
o	Why is the traffic served over HTTPS
o	What monitoring is used for
o	How the monitoring tool is collecting data
o	Explain what to do if you want to monitor your web server QPS
•	You must be able to explain what the issues are with this infrastructure:
o	Why terminating SSL at the load balancer level is an issue
o	Why having only one MySQL server capable of accepting writes is an issue
o	Why having servers with all the same components (database, web server and application server) might be a problem
Please, remember that everything must be written in English to further your technical ability in a variety of settings.



3. Scale up
Requirements:
•	You must add:
o	1 server
o	1 load-balancer (HAproxy) configured as cluster with the other one
o	Split components (web server, application server, database) with their own server
•	You must be able to explain some specifics about this infrastructure:
o	For every additional element, why you are adding it
Please, remember that everything must be written in English to further your technical ability in a variety of settings.

