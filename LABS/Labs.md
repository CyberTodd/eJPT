
MySQL Recon: Basics

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


```

9.  Dump the schema of all databases from the server using suitable metasploit module?
10.  How many directories present in the /usr/share/metasploit-framework/data/wordlists/directory.txt, are writable? List the names.
11.  How many of sensitive files present in /usr/share/metasploit-framework/data/wordlists/sensitive_files.txt are readable? List the names.
12.  Find the system password hash for user "root".
13.  How many database users are present on the database server? Lists their names and password hashes.
14.  Check whether anonymous login is allowed on MySQL Server.
15.  Check whether “InteractiveClient” capability is supported on the MySQL server.
16.  Enumerate the users present on MySQL database server using mysql-users nmap script.
17.  List all databases stored on the MySQL Server using nmap script.
18.  Find the data directory used by mysql server using nmap script.
19.  Check whether File Privileges can be granted to non admin users using mysql_audi nmap script.
20.  Dump all user hashes using  nmap script.
21.  Find the number of records stored in table “authors” in database “books” stored on MySQL Server using mysql-query nmap script.