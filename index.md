## Intro

Some pentesting stuff about Windows/AD & Linux.


### Network Enumeration

Some commands about network enums.

```markdown
**nmap**

# Host Discovery 
`nmap -Pn -v <IP>/CIDR`
# TCP Scan
`sudo -sS -sC -sV -oA <FILENAME>.tcp <IP> -v`
# UDP Scan
`sudo -sU -sS -sC -sV -oA <NAME>.udp <IP> -v`

**masscan**

# Host Discovery 
`masscan <IP>/CIDR --rate=10000 --ports <portsToScan> (ex. 80,443,445)`


**Bold** and _Italic_ and `Code` text
```
