# Recon

## nmap

```shell-session
# Nmap 7.94SVN scan initiated Sat Aug  3 22:46:48 2024 as: nmap -sT -sV -sC -p 21,22,53,1337,1883 -oN expose.txt 10.10.141.108
Nmap scan report for 10.10.141.108
Host is up (0.16s latency).

PORT     STATE SERVICE                 VERSION
21/tcp   open  ftp                     vsftpd 2.0.8 or later
|_ftp-anon: Anonymous FTP login allowed (FTP code 230)
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to ::ffff:10.13.57.25
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 1
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
22/tcp   open  ssh                     OpenSSH 8.2p1 Ubuntu 4ubuntu0.7 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 0a:74:ef:c2:b4:5b:fb:9d:2e:98:ff:4d:aa:c4:b6:a1 (RSA)
|   256 67:51:60:2e:22:57:8e:0b:84:71:83:9f:f5:f9:66:3c (ECDSA)
|_  256 83:ff:80:ee:0f:88:ab:6e:ca:98:93:2d:22:c5:7f:75 (ED25519)
53/tcp   open  domain                  ISC BIND 9.16.1 (Ubuntu Linux)
| dns-nsid: 
|_  bind.version: 9.16.1-Ubuntu
1337/tcp open  http                    Apache httpd 2.4.41 ((Ubuntu))
|_http-title: EXPOSED
|_http-server-header: Apache/2.4.41 (Ubuntu)
1883/tcp open  mosquitto version 1.6.9
| mqtt-subscribe: 
|   Topics and their most recent payloads: 
|     $SYS/broker/load/messages/sent/15min: 0.82
|     $SYS/broker/load/bytes/sent/15min: 27.50
|     $SYS/broker/bytes/sent: 1224
|     $SYS/broker/uptime: 3729 seconds
|     $SYS/broker/bytes/received: 89
|     $SYS/broker/load/messages/received/5min: 0.23
|     $SYS/broker/load/bytes/received/5min: 4.06
|     $SYS/broker/heap/maximum: 50416
|     $SYS/broker/load/messages/sent/1min: 0.91
|     $SYS/broker/load/bytes/sent/1min: 3.65
|     $SYS/broker/store/messages/bytes: 161
|     $SYS/broker/messages/sent: 35
|     $SYS/broker/version: mosquitto version 1.6.9
|     $SYS/broker/messages/received: 5
|     $SYS/broker/load/sockets/5min: 0.41
|     $SYS/broker/load/connections/15min: 0.11
|     $SYS/broker/load/connections/1min: 0.91
|     $SYS/broker/load/messages/received/15min: 0.16
|     $SYS/broker/load/sockets/15min: 0.18
|     $SYS/broker/load/publish/sent/5min: 0.27
|     $SYS/broker/load/messages/sent/5min: 0.45
|     $SYS/broker/load/bytes/received/15min: 2.77
|     $SYS/broker/load/bytes/sent/5min: 9.95
|     $SYS/broker/load/connections/5min: 0.21
|     $SYS/broker/load/sockets/1min: 1.83
|     $SYS/broker/load/messages/received/1min: 0.91
|_    $SYS/broker/load/bytes/received/1min: 16.45
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Sat Aug  3 22:47:10 2024 -- 1 IP address (1 host up) scanned in 22.13 seconds
```

## gobuster

```shell-session
┌──(kali㉿kali)-[~]
└─$ gobuster dir -u http://10.10.141.108:1337 -w /usr/share/wordlists/dirb/big.txt 
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.10.141.108:1337
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/dirb/big.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/.htaccess            (Status: 403) [Size: 280]
/.htpasswd            (Status: 403) [Size: 280]
/admin                (Status: 301) [Size: 321] [--> http://10.10.141.108:1337/admin/]
/admin_101            (Status: 301) [Size: 325] [--> http://10.10.141.108:1337/admin_101/]
/javascript           (Status: 301) [Size: 326] [--> http://10.10.141.108:1337/javascript/]
/phpmyadmin           (Status: 301) [Size: 326] [--> http://10.10.141.108:1337/phpmyadmin/]
/server-status        (Status: 403) [Size: 280]
Progress: 20469 / 20470 (100.00%)
===============================================================
Finished
===============================================================

```

## admin_101

![[Pasted image 20240803232900.png]]
