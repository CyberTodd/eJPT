

# 1. Assessment Methodologies

![[Pasted image 20230320114227.png]]








---
# 2. Host & Networking Auditing

![[Pasted image 20230320114242.png]]







---
# 3. Host & Network Penetration Testing

![[Pasted image 20230320114254.png]]







---
# 4. Web Application Penetration Testing

![[Pasted image 20230320114304.png]]





---
# Linux Shell Commands


- whatis // utility will display what a command does
![[Pasted image 20230320174752.png]]

- host command - to check IPs of URLs 
![[Pasted image 20230320174835.png]]

- To check some technologies on the site - whatweb utility
![[Pasted image 20230320175120.png]]
- whois - another utility that offers information about a website - especially server name, registrars,  update, creation dates, etc.
![[Pasted image 20230320175318.png]]
- there is also the web gui - whois is not that accurate just make sure to check with the terminal utility
![[Pasted image 20230320175502.png]]

- netcraft is an incredible website that offers information about an url - is a better whois version
![[Pasted image 20230320175650.png]]
- to enumerate DNS records
![[Pasted image 20230320175818.png]]
- another incredible tool to check dns records and other information
![[Pasted image 20230320175858.png]]
![[Pasted image 20230320175908.png]]

- httrack - to copy a web to your machine 
![[Pasted image 20230320175152.png]]

- identify WAF with wafw00f
![[Pasted image 20230320180033.png]]

- sublist3r is a tool used to enumerate subdomains of websites using OSINT
- if Google is blocking requests use a VPN to bypass this, otherwise use another SE
![[Pasted image 20230320180138.png]]

- for further OSINT check - use Google Dorks

- to check emails, names, subdomains, IPs, and URLs use also theHarvester
![[Pasted image 20230320180345.png]]

- dnsenum - enumerate dns
![[Pasted image 20230320180652.png]]
- fierce - is a scanner that helps locate non-contiguous IP space and hostnames against specific domains
![[Pasted image 20230320180846.png]]

- identify hosts on a network - arp-scan 
![[Pasted image 20230320181156.png]]

- check traffic on a network - wireshark

- SMB on port 139, 445 - is used to communicate over NetBIOS; SAMBA is the Linux implementation of the SMB protocol;
- 