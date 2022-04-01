

Some pentesting stuff about Windows/AD & Linux.

Useful links
------------
- Wordlists : https://github.com/danielmiessler/SecLists
- PrivEsc : https://github.com/carlospolop/PEASS-ng
- PrivEsc : https://gtfobins.github.io/
- Reverse Shells : https://www.revshells.com

## Network Enumeration

Some stuff about network enums.

```markdown
nmap
----

# Host Discovery 
nmap -sn -v <IP>/CIDR
 
# TCP Scan
nmap -sS -sC -sV -oA <FILENAME>.tcp <IP> -v
 
# 1000 most common TCP ports on an IP range
nmap -sV --open <IP>/CIDR
 
# UDP Scan
nmap -sU -sS -sC -sV -oA <FILENAME>.udp <IP> -v
 
# 1000 most common UDP ports on an IP range
nmap -sU -sV --open <IP>/CIDR

 TIPS  
  - -p- : scan all ports
  - -Pn : to scan ports on Windows hosts
  
  
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

## Web Application
```markdown
Enumeration 

# dirsearch
- dirsearch -u <URL> -r
- dirb <URL> -r /usr/share/wordlists/dirb/common.txt
 
 
# wordpress
- wpscan --url <URL> (-e u : to enumerate WP users)


#
 
 
#
 

# Crypto
- ./testssl.sh -oA <filename> <URI>

 
# Reverse Shell
- Spawn a tty shell : python -c 'import pty; pty.spawn("/bin/sh")'

 ```

