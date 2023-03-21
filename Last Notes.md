

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
- Frequently Exploited Windows Services:
	- Microsoft IIS TCP 80/ 443 - WebDAV TCP 80/ 443
	- SMB/CIFS TCP 445
	- RDP TCP 3389
	- WinRM TCP 5986/ 443

- IIS is a proprietary extensible web server software developed by Microsoft - supported executable files: .asp, .aspx, .config, .php
- WebDAV is a set of extensions to the HTTP protocol which allow users to collaboratively edit and manage files on remote web servers - it runs on top of IIS
	- to connect to a webdav server you need legitimate credentials when you jump into the /webdav/ directory - use hydra to brute the creds
	- davtest is checking if webdav was configured for a server and also you can login with it
- for example here we see that is opened but it will fail because we need to insert creds
![[Pasted image 20230320214305.png]]
- here davtest will tell us what kind of files we can upload on the webdav server
![[Pasted image 20230320214339.png]]
- here .asp is the most important 
![[Pasted image 20230320214437.png]]
- now with cadaver we can upload our webshell.asp
![[Pasted image 20230320214500.png]]
![[Pasted image 20230320214512.png]]
- it will then provide with a pseudo-shell
![[Pasted image 20230320214528.png]]
- if successful - check the webdav uploaded file
![[Pasted image 20230320214615.png]]
- after you run it in the web, you will get a webshell
![[Pasted image 20230320214715.png]]
- webdav with msfconsole
	- generate the payload with msfvenom - after generation check it - use the default 32-bit payload
![[Pasted image 20230320214935.png]]
- now with cadaver upload it
![[Pasted image 20230320215027.png]]
![[Pasted image 20230320215039.png]]
- now before execution we need to setup a listener with msf
![[Pasted image 20230320215122.png]]
![[Pasted image 20230320215147.png]]
- after this execute it on the target
![[Pasted image 20230320215200.png]]
![[Pasted image 20230320215207.png]]
- to automate this process use the exploit iis_webdav_upload_asp
![[Pasted image 20230320215316.png]]
- specify the directory and then use a custom name 
![[Pasted image 20230320215337.png]]

- SMB with psexec - is a lightweight telnet-replacement developed by Microsoft that allows you to execute processes on remote windows systems using any user's creds - is similar to RDP, but instead of a gui we send commends in the cmd
![[Pasted image 20230321170813.png]]
- xfreerdp for Linux to authenticate with rdp - you need credentials
![[Pasted image 20230321170934.png]]

- WinRM exploitation default port 5985 - to check for if winrm is running use crackmapexec
	- this will brute force the winrm
![[Pasted image 20230321171213.png]]
- we can see that winrm is running because is can see wsman which is the winrm implementation 
![[Pasted image 20230321171300.png]]
![[Pasted image 20230321171322.png]]
- to get a shell version on winrm use evil-winrm.rb
![[Pasted image 20230321171411.png]]

- Windows Privilege Escalation - Kernel Exploitation
- after you have access to the target system
![[Pasted image 20230321172058.png]]
- check privileges
![[Pasted image 20230321172124.png]]
- now start to check for kernel vulnerabilities - but before try the msf simple command to try to get an elevated session
![[Pasted image 20230321172242.png]]
- now let's use the module that checks for all vulnerabilities 
![[Pasted image 20230321172321.png]]
- set the session then run
- after that we identified multiple vulnerabilities among which we use the next one
![[Pasted image 20230321172538.png]]
- set session and lport
![[Pasted image 20230321172548.png]]
- for vulnerabilities always check for the specific windows that you're using
![[Pasted image 20230321172644.png]]

- now for a manual privilege escalation
- switch to the initial meterpreter session that's unprivileged and then we check windows-exploit-suggester tool - you have to clone the tool then update the db
- in the meterpreter open a shell to have a Windows prompt
	- the information under systeminfo copy it under a new file - it contains a list of hotfixes that were installed and those will be use by our tool
![[Pasted image 20230321172906.png]]
![[Pasted image 20230321172957.png]]
- now terminate the shell and have the meterpreter session - open a new tab to create the vim file and paste everything that you copied from the systeminfo
![[Pasted image 20230321173100.png]]
![[Pasted image 20230321173110.png]]
- now navigate to the directory where you cloned the windows-exploit-suggester tool
![[Pasted image 20230321173141.png]]
- update the db 
![[Pasted image 20230321173211.png]]
- now run the latest db and the file you created - the top ones are most successful
![[Pasted image 20230321173249.png]]
