# Footprinting & Scanning - Lab 2
1.  Identify the port running a Bind DNS server.
```
nmap [ip] -p 1-250 
nmap [ip] -p 177 -A
nmap [ip] -p 1-250 -sU

```

3.  Identify the port running a TFTP server.
```
nmap [ip] -p 134 -sUV --script=discovery 

tftp [ip] 134

status
```

5.  Identify the port running the SNMP server.
```
nmap [ip] -p 134,177,234 -sUV
```

---
# Windows Recon: SMB Nmap Scripts

The following username and password may be used to access the service:

| Username | Password | | administrator | smbserver_771 |

1.  Identify SMB Protocol Dialects
```
nmap [ip] -p 445 --script smb-protocols
```

3.  Find SMB security level information
```
nmap [ip] -p 445 --script smb-security-mode
```

5.  Enumerate active sessions, shares, Windows users, domains, services, etc.
```
// active sessions
nmap [ip] -p 445 --script smb-enum-sessions

nmap [ip] -p 445 --script smb-enum-sessions --script-args smbusername=administrator,smbpassword=smbserver_771

// shares
nmap [ip] -p 445 --script smb-enum-shares  
nmap [ip] -p 445 --script smb-enum-shares --script-args smbusername=administrator,smbpassword=smbserver_771

// users
nmap [ip] -p 445 --script smb-enum-users --script-args smbusername=administrator,smbpassword=smbserver_771

// server stats
nmap [ip] -p 445 --script smb-server-stats --script-args smbusername=administrator,smbpassword=smbserver_771

// domains
nmap [ip] -p 445 --script smb-enum-domains --script-args smbusername=administrator,smbpassword=smbserver_771

nmap [ip] -p 445 --script smb-enum-groups --script-args smbusername=administrator,smbpassword=smbserver_771

// services
nmap [ip] -p 445 --script smb-enum-services --script-args smbusername=administrator,smbpassword=smbserver_771

// other
nmap [ip] -p 445 --script smb-enum-shares,smb-ls --script-args smbusername=administrator,smbpassword=smbserver_771
```

---
# Samba Recon: Basics

1.  Find the default tcp ports used by smbd.
```
nmap [ip] -p- -T3

nmap [ip] -p 139,445 -sCV
```

3.  Find the default udp ports used by nmbd.
```
nmap [ip] --top-ports 25 -sU --open
```

5.  What is the workgroup name of samba server?
```
nmap [ip] --top-ports 25 -sUV --open
```

7.  Find the exact version of samba server by using appropriate nmap script.
```
nmap [ip] -p 445 --script smb-os-discovery
```

9.  Find the exact version of samba server by using smb_version metasploit module.
```
msfconsole - use auxiliary/scanner/smb/smb_version
```

11.  What is the NetBIOS computer name of samba server? Use appropriate nmap scripts.
```
nmap [ip] -p 445 --script smb-os-discovery
```

13.  Find the NetBIOS computer name of samba server using nmblookup
```
nmblookup -A [ip] - connect to the <20>SAMBA

```

15.  Using smbclient determine whether anonymous connection (null session)  is allowed on the samba server or not.
```
smbclient -L [ip] -N - when you see ICP$ with a null session maybe you can connect to it
```

17.  Using rpcclient determine whether anonymous connection (null session) is allowed on the samba server or not.
```
rpcclient -U "" -N "" [ip] - and check if you can connect
```

---
# Samba Recon: Basics II

1.  Find the OS version of samba server using rpcclient.
```
nmap [ip] -p- -T3

nmap [ip] -p 139,445 -sV -T3

rpcclient -U "" -N [ip]

after connection - srvinfo
```

3.  Find the OS version of samba server using enum4Linux.
```
enum4linux -o [ip]
```

5.  Find the server description of samba server using smbclient.
```
smbclient -L [ip] -N 
```

7.  Is NT LM 0.12 (SMBv1) dialects supported by the samba server? Use appropriate nmap script.
```
nmap [ip] -p 445 --script smb-protocols
```

9.  Is SMB2 protocol supported by the samba server? Use smb2 metasploit module.
```
msfconsole - use auxiliary/scanner/smb/smb2
```

11.  List all users that exists on the samba server  using appropriate nmap script.
```
nmap [ip] -p 445 --script smb-enum-users
```

15.  List all users that exists on the samba server  using enum4Linux.
```
enum4linux -U [ip]
```

17.  List all users that exists on the samba server  using rpcclient.
```
rpcclient -U "" -N [ip]

enumdomusers
```

19.  Find SID of user “admin” using rpcclient.
```
rpcclient 

lookupnames admin
```
---
# Samba Recon: Basic III

1.  List all available shares on the samba server using Nmap script.
```
nmap [ip] -p 445 --script smb-enum-shares
```

3.  List all available shares on the samba server using smb_enumshares Metasploit module.
```
msfconsole - use auxiliary/scanner/smb/smb_enumshares
```

4.  List all available shares on the samba server using enum4Linux.
```
enum4Linux -S [ip]
```

5.  List all available shares on the samba server using smbclient.
```
smbclient -L [ip] -N
```

6.  Find domain groups that exist on the samba server by using enum4Linux.
```
enum4linux -G [ip]
```

7.  Find domain groups that exist on the samba server by using rpcclient.
```
rpcclient -U "" -N [ip]

enumdomgroups
```

8.  Is samba server configured for printing?
```
enum4linux -i [ip]
```

9.  How many directories are present inside share “public”?
```
smbclient //[ip]/Public -N

smb - help
ls
cd secret 
ls
get flag
exit
cat flag
```
---
# Samba Recon: Dictionary Attack
1.  What is the password of user “jane” required to access share “jane”? Use smb_login metasploit module with password wordlist /usr/share/wordlists/metasploit/unix_passwords.txt
```
msfconsole - use auxiliary/scanner/smb/smb_login
```

3.  What is the password of user “admin” required to access share “admin”? Use hydra with password wordlist: /usr/share/wordlists/rockyou.txt
```
hydra -l admin -P /path file/ [ip] smb<-protocol
```

4.  Which share is read only? Use smbmap with credentials obtained in question 2.
```
smbmap -H [ip] -u admin -p password1
```

5.  Is share “jane” browseable? Use credentials obtained from the 1st question.
```
smbclient -L [ip] -U jane 
password: abc123

smbclient //[ip]/jane -U jane
password: abc123
```

6.  Fetch the flag from share “admin”
```
smbclient //[ip]/admin -U admin
password: password1
cd hidden
get flab.tar.gz
exit
ls
tar -xf flag.tar.gz
ls
cat flag
```

7.  List the named pipes available over SMB on the samba server? Use  pipe_auditor metasploit module with credentials obtained from question 2.
```
msfconsole - use auxiliary/scanner/smb/pipe_auditor
set smbuser admin
set smbpass password1
set rhosts [ip]
run
```

8.  List sid of Unix users shawn, jane, nancy and admin respectively by performing RID cycling  using enum4Linux with credentials obtained in question 2.
``` 
enum4linux -r -u "admin" -p "password1" [ip] 
```
---
# ProFTP Recon: Basics

1.  What is the version of FTP server?
```
nmap [ip]

nmap [ip] -p 21 -sV -O

ftp [ip]
Name: try nothing
Password: try nothing
if failed - bye

ftp again with proper user and password
help to check the commands
```

3.  Use the username dictionary /usr/share/metasploit-framework/data/wordlists/common_users.txt and password dictionary /usr/share/metasploit-framework/data/wordlists/unix_passwords.txt to check if any of these credentials work on the system. List all found credentials.
```
hydra -L /path -P /path [ip] ftp<-protocol
```

4.  Find the password of user “sysadmin” using nmap script.
```
nmap [ip] -p 21 --script ftp-brute --script-args userdb=/root/users<- file created by us
```
---
# VSFTPD Recon: Basics
1.  Find the version of vsftpd server.
```
nmap [ip] 
nmap [ip] -p 21 -sV
```

3.  Check whether anonymous login is allowed on the ftp server using nmap script.
```
nmap [ip] -p 21 --script ftp-anon

ftp [ip]
Name: anonymous
Password: [ENTER]
```
---
# SSH Recon: Basic

1.  What is the version of SSH server.
```
nmap [ip]

nmap [ip] -p 22 -sV -O

ssh root@[ip]
continue -> yes
enter the password: -you have 3 chances-
```

3.  Fetch the banner using netcat and check the version of SSH server.
```
netcat - nc [ip] 22
```

5.  Fetch pre-login SSH banner.
```
nmap [ip] -p 22 --script ssh2-enum-algos
```

7.  How many “encryption_algorithms” are supported by the SSH server.
```
nmap [ip] -p 22 --script ssh2-enum-algos
```

9.  What is the ssh-rsa host key being used by the SSH server.
```
nmap [ip] -p 22 --script ssh-hostkey --script-args ssh_hostkey=full
```

11.  Which authentication method is being used by the SSH server for user “student”.
```
nmap [ip] -p 22 --script ssh-auth-methods --script-args="ssh.user=student"

ssh student@[ip]
whoami
```

13.  Which authentication method is being used by the SSH server for user “admin”.
```
nmap [ip] -p 22 --script ssh-auth-methods --script-args="ssh.user=admin"
```
---
# SSH Recon: Dictionary Attack

1.  Find the password of user “student” using hydra.
```
nmap [ip]

nmap [ip] -p 22 -sV

gzip -d /usr/share/wordlists/rockyou.txt.gz

hydra -l student -P /usr/share/wordlists/rock
```

3.  Find the password of user “administrator” use appropriate Nmap scripts with password dictionary: /usr/share/nmap/nselib/data/passwords.lst
```



nmap [ip] -p 22 --script s
```

5.  Find the password of user “root” using ssh_login Metasploit module with userpass dictionary: /usr/share/wordlists/metasploit/root_userpass.txt
```

```

7.  What is the message of the day? (Printed after the user logs in to the SSH server).
```

```

---
# MySQL Recon: Basics

1.  What is the version of MySQL server?
```
nmap [ip] -sV -sC
```
- MySQL 5.5.62-0ubuntu0.14.04.1

3.  What command is used to connect to remote MySQL database?
```
mysql -u [username] -h [ip] -p
```

5.  How many databases are present on the database server?
```
show databases;
```

7.  How many records are present in table “authors”? This table is present inside the “books” database.
```
use books;

select * from authors;
```

9.  Dump the schema of all databases from the server using suitable metasploit module?
```
auxiliary(scanner/mysql/mysql_schemadump) // also provides a .txt file with it;
```

11.  How many directories present in the /usr/share/metasploit-framework/data/wordlists/directory.txt, are writable? List the names.
```
auxiliary(scanner/mysql/mysql_writable_dirs)

```

13.  How many of sensitive files present in /usr/share/metasploit-framework/data/wordlists/sensitive_files.txt are readable? List the names.
```
auxiliary(scanner/mysql/mysql_file_enum)

```

15.  Find the system password hash for user "root".
```
mysql -u root -h [id]
select load_file('/etc/shadow');
```

17.  How many database users are present on the database server? Lists their names and password hashes.
```
auxiliary(scanner/mysql/mysql_hashdump)
```

19.  Check whether anonymous login is allowed on MySQL Server.
```
mysql -h 192.82.22.3

nmap [ip] -p 3306 --script=mysql-empty-password
```

21.  Check whether “InteractiveClient” capability is supported on the MySQL server.
```
nmap 192.12.132.3 -p 3306 --script=mysql-info
```

23.  Enumerate the users present on MySQL database server using mysql-users nmap script.
```
nmap 192.12.132.3 -p 3306 --script=mysql-users --script-args="mysqluser=root,mysqlpass=''"
```

25.  List all databases stored on the MySQL Server using nmap script.
```
nmap 192.12.132.3 -p 3306 --script=mysql-databases --script-args="mysqluser=root,mysqlpass=''"
```

27.  Find the data directory used by mysql server using nmap script.
```
nmap 192.12.132.3 -p 3306 --script=mysql-variables --script-args="mysqluser=root,mysqlpass=''"
```

29.  Check whether File Privileges can be granted to non admin users using mysql_audi nmap script.
```
nmap 192.12.132.3 -p 3306 --script=mysql-audit --script-args="mysql-audit.username=root,mysql-audit.password='',mysql-audit.filename='/usr/share/nmap/nselib/data/mysql-cis.audit'"
```
31.  Dump all user hashes using  nmap script.
```
nmap --script mysql-dump-hashes --script-args='username=root,password=""' -p 3306 192.12.132.3
```
33.  Find the number of records stored in table “authors” in database “books” stored on MySQL Server using mysql-query nmap script.
```
nmap --script mysql-query --script-args="query ='select * from books.authors;',username='root',password=''" -p 3306 192.12.132.3
```