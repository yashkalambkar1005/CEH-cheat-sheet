# Common Ports and Protocols Cheat Sheet

## Common Ports

  Protocol / Service                      TCP        UDP
  ------------------------------ ------------ ----------
  Arbitrary Protocol Node                2002        ---
  FTP (File Transfer Protocol)             21        ---
  SSH (Secure Shell)                       22        ---
  Telnet                                   23        ---
  SMTP                                     25        ---
  DNS                                      53         53
  HTTP                                     80        ---
  Kerberos                                 88        ---
  POP3                                    110        ---
  RPC                                     135        ---
  SMB (NetBIOS)                           139        ---
  LDAP                                    389        ---
  HTTPS                                   443        ---
  SMB                                     445        ---
  Modbus                                  502        ---
  LDAPS                                   636        ---
  POP3S                                   995        ---
  MSSQL(sql Server)                      1433        ---
  SNMP                                    ---   161, 162
  MQTT                                   1883        ---
  NFS                                    2049        ---
  Microsoft ADGC                   3268, 3269        ---
  MySQL                                  3306        ---
  RDP                                    3389        ---
  njRAT                                  5553        ---
  ADB                                    5555        ---
  Python HTTP Server                     8000        ---
  WAMP / Proxy                           8080        ---
  RAT Ports                        9871, 6703        ---

## Remote Login & Connection Commands

``` bash
ftp <ip>
ssh user@<ip>
telnet <ip> <port>
smbclient //<ip>/<share>
xfreerdp /v:<ip>
mysql -h <ip> -u user -p
adb connect <ip>:5555
```
