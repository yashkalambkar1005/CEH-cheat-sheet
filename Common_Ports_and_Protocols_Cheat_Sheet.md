# Common Ports and Protocols Cheat Sheet

## Page 1

PROTOCOL / SERVICE NAME TCP PORT UDP PORT Arbitrary Protocol Node 2002
--- FTP (File Transfer Protocol) 21 --- SSH (Secure Shell) 22 --- Telnet
Terminal Connection 23 --- SMTP (Simple Mail Transfer Protocol) 25 ---
DNS (Domain Name System) 53 53 HTTP (Hypertext Transfer Protocol) 80 ---
Kerberos-sec Authentication Layer 88 --- POP3 (Post Office Protocol v3)
110 --- RPC (Remote Procedure Call) 135 --- SMB (NetBIOS Session
Protocol) 139 --- LDAP (Lightweight Directory Access Protocol) 389 ---
HTTPS (Hypertext Transfer Protocol Secure) 443 --- SMB (Server Message
Block Core) 445 --- Modbus (Industrial Communication Interface) 502 ---
LDAPS (LDAP over SSL/TLS) 636 --- POP3 Encrypted (Secure Mailbox Access)
995 --- MSSQL (Microsoft SQL Server Database Engine) 1433 --- SNMP
(Simple Network Management Protocol) --- 161, 162 MQTT (IoT & OT
Messaging Broker) 1833 --- NFS (Network File System) 2049 --- Microsoft
ADGC (Active Directory Global Catalog) 3268, 3269 --- MySQL Database
Engine Listener 3306 --- RDP (Remote Desktop Protocol) 3389 --- njRAT
Default Backdoor Listener 5553 --- Networking & Remote Login Protocols
Master Sheet Page 3

## Page 2

PROTOCOL / SERVICE NAME TCP PORT UDP PORT ADB (Android Debug Bridge
Network Link) 5555 --- Default Port of Portable Python HTTP Server 8000
--- Proxy / WAMP Default Web Server Instance 8080 --- RAT Ports (Remote
Access Trojans) 9871, 6703 --- 2. REMOTE LOGIN & CONNECTION COMMANDS
Utilize these standardized interactive terminal execution lines to
directly connect with target services over active interfaces: Networking
& Remote Login Protocols Master Sheet Page 4

## Page 3

FTP (File Transfer Protocol) ftp `<ip>`{=html} SSH (Secure Shell
Terminal) ssh user@`<ip>`{=html} Telnet Connection (Custom Port) telnet
`<ip>`{=html} `<port>`{=html} SMB Client (Share Enumeration & Mounting)
smbclient //`<ip>`{=html}/`<share>`{=html} RDP Client (XFreerdp Terminal
Link) xfreerdp /v:`<ip>`{=html} MySQL Interactive Console Login mysql -h
`<ip>`{=html} -u user -p ADB (Android Debug Bridge Connection) adb
connect `<ip>`{=html}:5555 Networking & Remote Login Protocols Master
Sheet Page 5
