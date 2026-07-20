Security Group: bastion-sg
inbound: 22 and my IP/32
outbound: SSH(22) to database, web-tier and app-tier.
reasoning: 
Only I should SSH in to bastion and noone else, That is why I specified my IP to it also bastion should have the access to all the instances. 

security group: web-tier-sg
inbound: HTTP:80, HTTPS:443 and SSH:22(bastion) from 0.0.0.0/0
outbound: TCP:8080, TCP:443 (proxy to app tier and package download from internet)
reasoning: web-tier is the customer facing side so should have open port to the internet (both HTTP and HTTPS), and also should be accessable by bastion in case config needed.


security group: database-sg
inbound: SSH:22 and TCP:3306 
outound: HTTPS:443 
reasoning:
database-sh should only allow bastion(SSH) and TCP:3306 for NySQL queries communication. Never be exposed to the internet.

Security group: app-tier-sg
inbound: TCP:8080 and SSH(22)
outbound: TCP(3306) and HTTPS(443)
reasoning:
8080 to have the communication between the database and the app tier internally only and the HTTPS(443) is for package downloads if needed. 

