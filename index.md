
## Intro

Some pentesting stuff about Windows/AD & Linux.


## Network Enumeration

Some stuff about network enums.

```markdown
nmap
----

# Host Discovery 
nmap -sn -v <IP>/CIDR
# 1000 most common TCP ports on an IP range
nmap -sV --open <IP>/CIDR
# TCP Scan
sudo -sS -sC -sV -oA <FILENAME>.tcp <IP> -v
# UDP Scan
sudo -sU -sS -sC -sV -oA <NAME>.udp <IP> -v
# 1000 most common UDP ports on an IP range
nmap -sU -sV --open <IP>/CIDR

 TIPS  
  - -p- : scan all ports
  - -Pn : to scan hosts on Windows hosts
  
  
masscan
-------

# Fast scan of a big subnet with selected open ports 
masscan <IP>/CIDR --rate=10000 --ports <portsToScan> (ex. 80,443,445)


```

## Windows / Active Directory 

Some stuff about Windows & AD pentesting.

```markdown
Network Analysis

# Responder 
responder -I <interface> -vrd

```
```markdown
Enumeration 

# No creds
- enum4linux -a -u "" -p "" <DC IP> 
- enum4linux -a -u "guest" -p "" <DC IP>
 
- smbclient -U '%' -L //<DC IP> 
- smbclient -U 'guest%' -L //
 
- nmap -n -sV --script "ldap* and not brute" -p 389 <DC IP>

# With Creds
- impacket-GetADUsers.py -all -dc-ip <DC IP> <domain>/username
- enum4linux -a -u <USER> -p <PASSWORD> <DC IP> 
 
# CrackMapExec
- crackmapexec smb <DC IP> -u <USER> -p <PASSWORD> --groups --local-groups --loggedon-users --rid-brute --sessions --users --shares --pass-pol > cme_enum.txt
 
```
```markdown
SMB 
# Explore Shares
impacket-smbclient '<USER>:<PASSWORd>'@<DC IP>
 
```

