
1. What is the IP address of the host running WordPress?
	- 192.168.100.50 - nmap scan and manual investigation

2. How many hosts on the DMZ network are running Windows?
	- 4 - nmap 

3. What version of MySQL is running on the system hosting a Drupal site?
	- MySQL 5.5.5 - nmap

4. How many hosts on the DMZ network are running a database server?
	- 1 - nmap and manual investigation

5. What version of Windows is running on the host running WordPress?
	- Windows Server 2012 R2 - nmap
6. What time does a working day start at Syntex?
	- 9:30 - manual investigation
7. What is the email of the admin user on the Drupal site?
	- admin@syntex.com - manual work
8. What version of Drupal is running on the Drupal site?
	- Connect with ssh dbadmin@192.168.100.52
	- Check in /var/www/html/drupal/CHANGELOG.txt
9. How many systems on the target network have FTP servers with anonymous access enabled?
	- 2 - nmap
10. What is the IP address of the FTP server that contains a file called updates.txt?
	- 192.168.100.52 - nmap - ftp
11. What type of vulnerability can be exploited on the Drupal site?
	- Command Injection
12. What type of vulnerability can be exploited to elevate your privileges on the Linux host running Drupal?
	- Vulnerable Service
13. What type of vulnerability can be exploited on the WordPress site to obtain a reverse shell?
	- Arbitrary File Upload
14. What is the subnet of the internal network?
	- 192.168.0.0/24
15. Which one of the following meterpreter commands can be used to add a network route?
	- autoroute
16. One of the Linux servers in the internal network is running a vulnerable service. What port is the vulnerable service running on?
	- 80
17. What is the password of the "Administrator" user on WINSERVER-03?
	- hydra smb with rockyou.txt
18. A target system has a user account called "lawrence". What is the password for this account?
	- computadora
19. What is the password of the user account "mary" on WINSERVER-03?
	- hotmama
20. What host within the DMZ network can be exploited via command injection.
	- WINSERVER-03
21. What is the CVSS V3.x rating for the Drupalgeddon2 vulnerability?
	- 9.8
22. What file can be used to identify the version of Drupal running on a webserver?
	- changelog.txt
23. What is the password for the "admin" user account on WordPress?
	- superman
24. What WordPress file stores the database configuration?
	- wp-config.php
25. What version of WordPress is running on WINSERVER-01?
	- 5.9.3
26. What host on the DMZ network is running a database server on port 3307?
	- 192.168.100.50
27. What is the root password of the MySQL database on the server running Drupal?
	- 
28. What is the version of the Linux kernel running on the system hosting the Drupal site?
	- 5.13.0
29. What host in the DMZ network is running a web server with WebDAV enabled?
	- 192.168.100.51
30. What user account is a member of the local administrators group on WINSERVER-03?
	- admin
31. Which one of the following user accounts is present on WINSERVER-02?
	- steven
32. How many HotFixes are installed on WINSERVER-01?
	- 220
33. The server hosting Drupal contains the file /home/auditor/flag.txt. What is the value of the flag?
	- 
34. What Windows utility can be used to download files from a remote web server?
	- certutil
35. What is the value of the flag C:\Users\Administrator\flag.txt on WINSERVER-03?
	- 