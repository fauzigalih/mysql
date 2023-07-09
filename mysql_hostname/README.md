## How to create hostname with IP server
create hostname mysql with IP server and can connect in third party app

### Install MySQL
```
$ sudo apt-get update
```
```
$ sudo apt install mysql-server
``` 
```
$ sudo systemctl restart mysql
``` 
```
$ sudo mysql
``` 
```
mysql > ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
``` 
```
mysql > exit
``` 
```
$ sudo mysql_secure_installation
```

### Change config mysql
Edit file config and save on directory `/etc/mysql/mysql.conf.d/mysqld.cnf`
```
$ sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf
```
change this line: <br>
`bind-address	= 127.0.0.1`

to this: <br>
`bind-address	= 0.0.0.0`

### Create User Mysql and Grant User
Login with user root
```
$ mysql -u root -ppassword
```
Create user admins
```
mysql > CREATE USER 'admins'@'localhost' IDENTIFIED BY 'password';
```
```
mysql > CREATE USER 'admins'@'%' IDENTIFIED BY 'password';
```
Grant user admins to all database
```
mysql > GRANT ALL PRIVILEGES ON *.* TO 'admins'@'localhost' WITH GRANT OPTION;
```
```
mysql > GRANT ALL PRIVILEGES ON *.* TO 'admins'@'%' WITH GRANT OPTION;
```
```
mysql > FLUSH PRIVILEGES;
```

### Create Database
Create database with username admins
```
mysql > CREATE DATABASE company;
```

## Hostname MySQL
Hostname  : 192.168.8.100 (IP Server) <br>
Username  : admins <br>
Password  : password <br>
Database  : company<br>

## Connect database with third party (DBeaver)
<img width="667" alt="image" src="https://github.com/fauzigalih/mysql/assets/64176403/47b796e2-f2c2-404c-8d28-32c349dc4841">
<img width="671" alt="image" src="https://github.com/fauzigalih/mysql/assets/64176403/1e627827-a652-4d5a-9ab6-91817cdeaa59">


Click button `Test Connection` 
if success, will display like this:

<img width="422" alt="image" src="https://github.com/fauzigalih/mysql/assets/64176403/3cba1ec8-0377-4f39-80d8-fa56fa05dccc">


### Yeayy,Finish....
