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
Inbound: SSH:22 from bastion-sg only, TCP:3306 from app-tier-sg only
Outbound: HTTPS:443 to 0.0.0.0/0 (package downloads)
Reasoning: database-sg should only ever accept connections from bastion (for SSH management) and app-tier (for MySQL queries) and never directly from the internet or any other tier. This is the most locked-down group
in the whole architecture, since the database holds the most sensitive data.

Security group: app-tier-sg
inbound: TCP:8080 and SSH(22)
outbound: TCP(3306) and HTTPS(443)
reasoning:
8080 to have the communication between the database and the app tier internally only and the HTTPS(443) is for package downloads if needed. 

