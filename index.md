
## Intro

Some pentesting stuff about Windows/AD & Linux.


### Network Enumeration

Some stuff about network enums.

```markdown
nmap

# Host Discovery 
nmap -Pn -v <IP>/CIDR
# 1000 most common TCP ports on an IP range
nmap -sV --open <IP>/CIDR
# TCP Scan
sudo -sS -sC -sV -oA <FILENAME>.tcp <IP> -v
# UDP Scan
sudo -sU -sS -sC -sV -oA <NAME>.udp <IP> -v
# 1000 most common UDP ports on an IP range
nmap -sU -sV --open <IP>/CIDR

masscan

# Fast scan of a big subnet with selected open ports 
masscan <IP>/CIDR --rate=10000 --ports <portsToScan> (ex. 80,443,445)


```

### Windows / Active Directory 

Some stuff about Windows & AD pentesting.

```markdown
Network Analysis

# Responder 

# Basic mode
responder -I <interface> -vrd
# Active mode
sudo -sU -sS -sC -sV -oA <NAME>.udp <IP> -v



```
