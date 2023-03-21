

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
- after the scan is done - copy the microsoft vulnerability ID and check it under the github repo
![[Pasted image 20230321173621.png]]
- in here - we will download the exe not the .c - compilation will come later
- now all we have to do is to transfer the exe file over the target and execute it - but be careful because this does not take in consideration anti-virus detection
- now with our meterpreter session let's transfer the file to the target
check the temp directory and navigate into it and check it
![[Pasted image 20230321173813.png]]
![[Pasted image 20230321173828.png]]
- upload the executable with meterpreter
![[Pasted image 20230321173840.png]]
![[Pasted image 20230321173900.png]]
![[Pasted image 20230321173917.png]]
- if you execute the program it will prompt with what version of windows you want to use
![[Pasted image 20230321173925.png]]
- after this wait to complete
![[Pasted image 20230321173952.png]]
![[Pasted image 20230321174010.png]]

- Bypassing UAC with UACme
- check users in the system and the localgroup
![[Pasted image 20230321174909.png]]
- after checking the target with nmap you identify rejetto 2.3 - exploit it with msf to obtain a meterpreter session
![[Pasted image 20230321180220.png]]
- after perform the basic enumeration to check the OS, privileges, etc
![[Pasted image 20230321180304.png]]
![[Pasted image 20230321180328.png]]
- migrate to explorer to upgrade meterpreter to x64
![[Pasted image 20230321180349.png]]
- we see admin which is not administrator
![[Pasted image 20230321180408.png]]
- get the current privileges 
	- we identify very few but this does not mean that it can't run files like the administrator
![[Pasted image 20230321180423.png]]
- now to verify if this user is part of the administrator group - open a shell
![[Pasted image 20230321180609.png]]
- we see that admin is different from administrator
![[Pasted image 20230321180618.png]]
- we see that admin is part of the administrator group meaning that it can run programs with elevetad prives but it needs to bypass uac
![[Pasted image 20230321180632.png]]
- to check this
![[Pasted image 20230321180728.png]]
- now after all the checks let's look at uacme tool
![[Pasted image 20230321180830.png]]
- terminate the channel to be on the meterpreter session
- identify akagai64 on your system
![[Pasted image 20230321181146.png]]
- generate a meterpreter payload with msfvenom we transfer it to the target then we use the akagi   executable then execute the payload
- generate the payload with msfvenom
![[Pasted image 20230321181241.png]]
- next - setup the listener with msfconsole - multi_handler
![[Pasted image 20230321181333.png]]
- next - upload the backdoor file and access it - check the temp directory on the file - if is not there create one, if is move there
![[Pasted image 20230321181449.png]]
- now upload akagai - open a shell now
![[Pasted image 20230321181512.png]]
- check the files
![[Pasted image 20230321181525.png]]
- now we use the method or key 23 to run the executable 
![[Pasted image 20230321181614.png]]
- on the meterpreter session we have now privs on the same admin acc
![[Pasted image 20230321181641.png]]
![[Pasted image 20230321181652.png]]
- if we getprivs
![[Pasted image 20230321181707.png]]

- Access Token Impersonation 
	- The following privs are required for a successful impersonation attack:
![[Pasted image 20230321182537.png]]
- we will use the module incognito which is built-in in meterpreter
- use the target IP to identify ports with nmap - especially http port
![[Pasted image 20230321182821.png]]
- get a meterpreter session via the following module
![[Pasted image 20230321182852.png]]
- check sysinfo and migrate to the explorer process
![[Pasted image 20230321182919.png]]
![[Pasted image 20230321182927.png]]
- we don't have a privileged account - but we have SeImpersonatePrivilege
![[Pasted image 20230321182944.png]]

- load the incognito module now 
	- if the process dies - re-open it
![[Pasted image 20230321183013.png]]
- list user access tokens
![[Pasted image 20230321183045.png]]
![[Pasted image 20230321183051.png]]
- copy the administrator token
![[Pasted image 20230321183127.png]]
- you just elevated privs
![[Pasted image 20230321183135.png]]
![[Pasted image 20230321183154.png]]
- migrate now again to the explorer and check again
![[Pasted image 20230321183218.png]]
![[Pasted image 20230321183223.png]]

- Alternate Data Streams - hide malicious code in files
- navigate to temp
![[Pasted image 20230321183332.png]]
- open a cmd session and create a text file on Desktop
![[Pasted image 20230321183403.png]]
![[Pasted image 20230321183428.png]]
- the data stream is whenever you open a file - is the data stored in the data stream
![[Pasted image 20230321183446.png]]
- if you open properties - details - you will see the resource stream (metadata)
	- here we can hide some malicious payloads
![[Pasted image 20230321183517.png]]
- now to create another file and to hide something inside 
	- is not opening test.txt - is will open secret.txt
![[Pasted image 20230321183628.png]]
![[Pasted image 20230321183649.png]]
- if you list the content of Desktop you can also see that is 0 bytes
![[Pasted image 20230321183715.png]]
- open test.txt and put some data
![[Pasted image 20230321183729.png]]
- to access again the secret file
![[Pasted image 20230321183842.png]]
- we have now winPEAS on the target - we can use it to enumerate something from the target
![[Pasted image 20230321183907.png]]
- rename it to payload and place it to the temp direc
![[Pasted image 20230321183946.png]]
