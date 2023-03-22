

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
- rename it to payload and place it to the temp directory and navigate there
![[Pasted image 20230321183946.png]]
![[Pasted image 20230321184010.png]]
- now we use a legitimate text file in which we place the payload
![[Pasted image 20230321184054.png]]
![[Pasted image 20230321184119.png]]
- now we open notepad to make windowslogs as legitimate as possible (for a real attack)
- we can now even delete payload because we place it inside the resource stream of windowslog.txt file
![[Pasted image 20230321184230.png]]
- to start the executable payload 
	- we have an error - but we have to create a symbolic link 
![[Pasted image 20230321184252.png]]
![[Pasted image 20230321184316.png]]
- but we need an elevated session - do the same command after 
![[Pasted image 20230321184459.png]]
![[Pasted image 20230321184408.png]]
![[Pasted image 20230321184518.png]]

- Search for passwords in Windows configuration files
- generate a meterperter payload with msfvenom
![[Pasted image 20230321193548.png]]
- now setup a simple server with python to host the payload
![[Pasted image 20230321193609.png]]
- after we download the payload.exe file onto the target system by accessing the webserver hosted on the Kali system on port 80 - so how do we transfer it?
- open the victim cmd
![[Pasted image 20230321193810.png]]
- utilize certutil that's built in on windows to download files form a webserver
![[Pasted image 20230321193855.png]]
- now close the server and open msfconsole and open the handler and after run the payload.exe
![[Pasted image 20230321193924.png]]
![[Pasted image 20230321193941.png]]
- search file on windows
![[Pasted image 20230321194000.png]]
- check it manually the unattend.xml
![[Pasted image 20230321194026.png]]
- now we download the file on our machine
![[Pasted image 20230321194102.png]]
![[Pasted image 20230321194048.png]]
- after we cat unattend.xml we have the autologon - we have the password of administrator encoded in base64
![[Pasted image 20230321194156.png]]
- create a file with vim to paste the password and use the base64 tool that comes with Linux
![[Pasted image 20230321194236.png]]
![[Pasted image 20230321194241.png]]
![[Pasted image 20230321194423.png]]
![[Pasted image 20230321194429.png]]

- Dumping Hashes With Mimikatz
- The SAM database is a database file on Windows systems that stores hashed user passwords - mimikatz can be used to extract hashes from the lsass.exe process memory where hashes are cached
- perform a nmap and service version detection on the target IP
- use the msf module to exploit BadBlue to obtain a meterpreter session
![[Pasted image 20230321215123.png]]
- after the meterpreter check more info about the system
![[Pasted image 20230321215235.png]]
![[Pasted image 20230321215239.png]]
- we have access as a administrator user
![[Pasted image 20230321215257.png]]
- by migrating to the lsass process we have authority privs
![[Pasted image 20230321215303.png]]
![[Pasted image 20230321215318.png]]
![[Pasted image 20230321215330.png]]
- kiwi module is a meterpreter extension - mimikatz
![[Pasted image 20230321215426.png]]
- if you now open the help menu for meterpreter you have at the bottom the kiwi commands
![[Pasted image 20230321215507.png]]
![[Pasted image 20230321215512.png]]
- retrieve all credentials 
![[Pasted image 20230321215534.png]]
![[Pasted image 20230321215547.png]]
- check all NTLM hashes within the system - we also have the syskey 
![[Pasted image 20230321215621.png]]
- navigate to temp
![[Pasted image 20230321215727.png]]
![[Pasted image 20230321215733.png]]
- upload to the tarket mimikatz
![[Pasted image 20230321215754.png]]
- open a shell session then
![[Pasted image 20230321215804.png]]
![[Pasted image 20230321215808.png]]
- execute mimikatz now on the target
![[Pasted image 20230321215820.png]]
- the first thing check for the appropriate privs - 20 ok means that we are good to extract hashes 
![[Pasted image 20230321215837.png]]
![[Pasted image 20230321215909.png]]

- Pass-The-Hash technique is used to capture or harvest NTLM hashes or clear-text passwords
![[Pasted image 20230321220024.png]]
- obtain a meterpreter session via badblue_passthru - after perform some enumeration on the target
![[Pasted image 20230321220145.png]]
![[Pasted image 20230321220148.png]]
![[Pasted image 20230321220155.png]]
- lsa_dump_sam to get administrator NTLM hash - and paste it in a file - you also get the same things with mimikatz.exe
![[Pasted image 20230321220206.png]]
![[Pasted image 20230321220231.png]]
![[Pasted image 20230321220242.png]]
- you also get the NTLM hash with hashdump - this is also needed - the LM hash - it is required by the metasploit psexec module - then put it in the background
![[Pasted image 20230321220335.png]]
- paste all the hash because you might get errors otherwise
![[Pasted image 20230321220456.png]]
![[Pasted image 20230321220517.png]]
- we also need to configure the target and Native target
![[Pasted image 20230321220525.png]]
![[Pasted image 20230321220607.png]]
![[Pasted image 20230321220550.png]]
![[Pasted image 20230321220648.png]]
![[Pasted image 20230321220701.png]]
![[Pasted image 20230321220709.png]]

- another way to go around if we only have the NTLM hash and the user name - crackmapexec
![[Pasted image 20230321220851.png]]
![[Pasted image 20230321220901.png]]
- now you can execute some commands on the system
![[Pasted image 20230321220924.png]]

--- 
- Frequently Exploited Linux Services 
- Apache Web Server - TCP ports 80/443
- SSH - TCP port 22
- FTP - TCP port 21
- SAMBA - TCP port 445

- Linux Privilege Escalation
- Linux Kernel Exploits
- typical Linux systems that host web servers you will see this user
	- is not part of any group of a Linux system
![[Pasted image 20230321221410.png]]
- to check this open a shell session
![[Pasted image 20230321221451.png]]
- also list out all the users on the system
![[Pasted image 20230321221508.png]]
- now terminate the channel - and the script is 
![[Pasted image 20230321221604.png]]
- utilise the quick download option - after that transferit to the target system
![[Pasted image 20230321221622.png]]
- navigate on the target on the temp directory
![[Pasted image 20230321221657.png]]
![[Pasted image 20230321221712.png]]
- open a shell session to execute the script - offer execute permissions
![[Pasted image 20230321221737.png]]
- you can also see the execute permission that was granted
![[Pasted image 20230321221811.png]]
- execute it now - it will enumerate a list of exploits that the specific kernel version is vulnerable
![[Pasted image 20230321221841.png]]
- the most important information for kernel exploitation is here - also the kernel version and architecture
![[Pasted image 20230321221927.png]]
- we will use dirtycow - download it - you need gcc package to compile C files
![[Pasted image 20230321222106.png]]
![[Pasted image 20230321222134.png]]
![[Pasted image 20230321222153.png]]
- rename the exploit to dirty.c
![[Pasted image 20230321222225.png]]
![[Pasted image 20230321222246.png]]
- check the compile code is you need to use a file like this
![[Pasted image 20230321222238.png]]
- now to compile let's use the above command
	- if no errors are displayed it means that it was compiled - we will transfer to the target and see if it works if not we need to compile the C code on the target system
![[Pasted image 20230321222330.png]]
- terminate channel and go back to meterpreter - upload the dirtry
![[Pasted image 20230321222425.png]]
![[Pasted image 20230321222435.png]]
- is not working meaning that it was not compiled on our system - let's upload it to the target
![[Pasted image 20230321222449.png]]
![[Pasted image 20230321222517.png]]
![[Pasted image 20230321222531.png]]
![[Pasted image 20230321222538.png]]
- successfully connected to the target
![[Pasted image 20230321222612.png]]


- Exploit Misconfigured Cron Jobs
- we have access on a system as student
![[Pasted image 20230322144537.png]]
- identify cron jobs for our specific user
![[Pasted image 20230322144632.png]]
- inside the home/student directory we have a file - to demonstrate cron jobs - we can see that is owned by the root user and any other account on the system does not have permissions to change or execute it
![[Pasted image 20230322144719.png]]
![[Pasted image 20230322144723.png]]
- we know the directory where is stored and we know the file name - let's use the utility grep to look for all occurences of the path of the file - navigate to root of the system
![[Pasted image 20230322144916.png]]
- we find a shell script copy under usr/local/share - and the occurence of the string tells that the file is copied in tmp/message
![[Pasted image 20230322144931.png]]
- try to cat the message under tmp
![[Pasted image 20230322145032.png]]
- check the permission of the shell scripts - we can see that is owned by the root acc - but under permission every acc has read, write and execute permissions
![[Pasted image 20230322145059.png]]
- now we want to use this shell script with additional code to escalate our privs
- now if we check the copy shell we can see that it uses a bash shell - it copies the message from home/student to tmp/message - then it modifies the permissions of the message under the tmp directory
![[Pasted image 20230322145210.png]]
![[Pasted image 20230322145219.png]]
- we don't have any text editor in the lab but we can also use something ingenious - we will use the printf command
![[Pasted image 20230322145409.png]]
- we cat it
![[Pasted image 20230322145419.png]]
- now if we wait a couple of minutes we can check the users that are part of the sudoers group
	- the cron job was run and we can use the student account to run everything with root privs
![[Pasted image 20230322145520.png]]
- let's switch to the root user
![[Pasted image 20230322145620.png]]

- Exploiting SUID Binaries
- another lab with permissions in the system with a student account
- we see 2 binaries greetings and welcome - we see that every user can execute them but we also can see the s permission under welcome binary - that means that SUID permission is granted
![[Pasted image 20230322145727.png]]
- we now try to execute the greetings binary but we have permission denied, we have access to welcome however
![[Pasted image 20230322150340.png]]
- we can use the file command to check welcome file type
![[Pasted image 20230322150415.png]]
- try to identify now some strings within the binary
![[Pasted image 20230322150936.png]]
- we can see that it's calling an external binary - what if we modify greetings binary to execute a command like bash? - because the welcome has privileged executions will also execute greetings even if we can't - remove now the greetings binary and we can create another one
	- is a bash binary within greetings
![[Pasted image 20230322151114.png]]
- now if we try again to execute welcome we see that it will execute greetings - and also we have root privileges also
![[Pasted image 20230322151153.png]]

- Dumping Linux Password Hashes
![[Pasted image 20230322151414.png]]
- we see on our target the service and also we check for that vulnerability
![[Pasted image 20230322151620.png]]
- we see that we have a msf module
![[Pasted image 20230322151637.png]]
![[Pasted image 20230322151642.png]]
![[Pasted image 20230322151657.png]]
- obtain a bash session
![[Pasted image 20230322151707.png]]
![[Pasted image 20230322151722.png]]
- upgrade the session to a meterpreter session
- even if we get an error check sessions
![[Pasted image 20230322151738.png]]
![[Pasted image 20230322151759.png]]
![[Pasted image 20230322151805.png]]
![[Pasted image 20230322151813.png]]
- display the content of the shadow file
![[Pasted image 20230322151838.png]]
- run hashdump module from msf
![[Pasted image 20230322151929.png]]
![[Pasted image 20230322151944.png]]

---
- Generating Payloads with msfvenom 
- check the payloads that you can generate with msfvenom
![[Pasted image 20230322153124.png]]
- staged payload 
![[Pasted image 20230322155809.png]]
- unstaged payload 
![[Pasted image 20230322155818.png]]
- to generate a specific payload 
![[Pasted image 20230322160129.png]]
![[Pasted image 20230322160147.png]]
- now let's generate a 64bit payload 
![[Pasted image 20230322160317.png]]
- list of formats you can create your payload to
![[Pasted image 20230322160449.png]]
- generate a staged meterpreter payload for Linux - we don't need to provide any extension because the binary can directly be executed 
	- the most important information when we create a payload is the type of the payload and within it make sure you specify the target system and maybe the architecture also
![[Pasted image 20230322161229.png]]
![[Pasted image 20230322161319.png]]
- now we can execute it - but we need to create a listener first because otherwise nothing will happen
![[Pasted image 20230322161408.png]]
- to transfering them on the target we will send first the Windows payload
- set a simple server withing the directory
![[Pasted image 20230322161537.png]]
![[Pasted image 20230322161551.png]]
- now let's create the handler from the target system - so open a new tab with msf
![[Pasted image 20230322161707.png]]
- we need to configure the default payload - with what we generated
![[Pasted image 20230322161738.png]]
- first let's do it for windows
![[Pasted image 20230322161842.png]]
- set the lhost and lport then run
![[Pasted image 20230322161900.png]]
- now that the handler is listening - go to the windows 7 system - navigate to the hosted server 
![[Pasted image 20230322161929.png]]
- click on the payload and download it
![[Pasted image 20230322161941.png]]
- run it
![[Pasted image 20230322161947.png]]
- now check the handler 
![[Pasted image 20230322161956.png]]
- you can do the same for a Linux system
- set the payload to linux now in the multi handler - then run
![[Pasted image 20230322162110.png]]
- execute the payload
![[Pasted image 20230322162123.png]]
![[Pasted image 20230322162137.png]]

- Encoding payloads with msfvenom
- get a list of encoders - based on system and system architecture
![[Pasted image 20230322182245.png]]
- to generate a Windows then Linux payloads and to encoded with shikata_ga_nai
- windows payload and encoded
![[Pasted image 20230322182446.png]]
- in the output, after generation of the payload - you can see the iterations - the more iterations the higher the success rate to bypass the anti-virus 
![[Pasted image 20230322182655.png]]
![[Pasted image 20230322182718.png]]
- below you can see the encodedx86 iterated 10 times
![[Pasted image 20230322182848.png]]
- now for a linux payload 
![[Pasted image 20230322182916.png]]
![[Pasted image 20230322182922.png]]
![[Pasted image 20230322183048.png]]
- let's now test the windows payload - open a server with the python module
![[Pasted image 20230322183116.png]]
- now on the windows workstation let's create the listener on our linux machine
![[Pasted image 20230322183142.png]]
- then on the windows system - access the python server and save the payload 
![[Pasted image 20230322183159.png]]
![[Pasted image 20230322183213.png]]
- check now the handler
![[Pasted image 20230322183224.png]]

- Injecting Payloads Into Windows Portable Executables
- WinRAR worked really well
![[Pasted image 20230322183814.png]]
- download the 32bit executable
![[Pasted image 20230322183843.png]]
- now generate the payload - after the -x flag you specify the actual portable executable that you want to inject your payload - then where you what to save your final executable - in our case is under Desktop/Windows_Payloads/winrar.exe 
![[Pasted image 20230322183937.png]]
![[Pasted image 20230322184052.png]]
- we create a sucessfully payload that we can transfer to the target
![[Pasted image 20230322184111.png]]
- create on the Linux machine the python server and setup the multi handler
![[Pasted image 20230322184145.png]]
![[Pasted image 20230322184200.png]]
- on the windows system we can see on the server the payload
![[Pasted image 20230322184216.png]]
- we download it - one mistake that we did is that we did not specify the -k flag to maintain the normal functionality of the winrar executable
![[Pasted image 20230322184222.png]]
![[Pasted image 20230322184306.png]]
![[Pasted image 20230322184351.png]]
![[Pasted image 20230322184335.png]]
- now after access - once establishing access to a system through a client side attack - do the following to migrate the payload into another process
![[Pasted image 20230322184511.png]]
- let's create another payload with the -k flag to maintain the normal function of the winrar executable
![[Pasted image 20230322184640.png]]
- now it will fail because this technique is not used anymore because the anti-virus detects it - you can test with other executables to see it you succeed
![[Pasted image 20230322184723.png]]

- if you want to download with a utility that windows has by default use certutil to download files form a server
![[Pasted image 20230322185039.png]]
![[Pasted image 20230322185055.png]]
![[Pasted image 20230322185100.png]]
![[Pasted image 20230322185112.png]]
![[Pasted image 20230322185120.png]]

- upgrade command shells to meterpreter shells
- we gain access to a typical command shell
![[Pasted image 20230322185603.png]]
- we can upgrade it to a bash session
![[Pasted image 20230322185620.png]]
![[Pasted image 20230322185629.png]]
- put it in the background - now let's upgrade this session to meterpreter
![[Pasted image 20230322185717.png]]
![[Pasted image 20230322185730.png]]
- also you can upgrade a shell session with the -u flag - it will use the same module as above but automated
![[Pasted image 20230322185812.png]]
![[Pasted image 20230322185831.png]]

- Windows Post Exploitation Modules
