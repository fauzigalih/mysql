## How to create hostname with IP server
create hostname mysql with IP server and can connect in third party app

### Install MySQL
```
$ sudo apt-get update
``` <br>
```
$ sudo apt install mysql-server
``` <br>
```
$ sudo systemctl restart mysql
``` <br>
```
$ sudo mysql
``` <br>
```
mysql > ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
``` <br>
```
mysql > exit
``` <br>
```
$ sudo mysql_secure_installation
```

### Change config mysql
Edit file config and save on directory `/etc/mysql/mysql.conf.d/mysqld.cnf`
```
$ sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf
```
change this line:
`bind-address	= 127.0.0.1`

to this:
`bind-address	= 0.0.0.0`

### Create User Mysql and Grant User
Login with user root
```
$ mysql -u root -ppassword
```
Create user admins
```
mysql > CREATE USER 'admins'@'localhost' IDENTIFIED BY 'password';
``` <br>
```
mysql > CREATE USER 'admins'@'%' IDENTIFIED BY 'password';
```
Grant user admins to all database
```
mysql > GRANT ALL PRIVILEGES ON *.* TO 'admins'@'localhost' WITH GRANT OPTION;
``` <br>
```
mysql > GRANT ALL PRIVILEGES ON *.* TO 'admins'@'%' WITH GRANT OPTION;
``` <br>
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
![image](https://github.com/fauzigalih/mysql-host-name/assets/64176403/77b6f750-72cb-4d64-948c-683bc5e0448b)
![image](https://github.com/fauzigalih/mysql-host-name/assets/64176403/44bb8118-0f32-4c88-a8c4-976fdcb509e1)

Click button `Test Connection` 
if success, will display like this:

![image](https://github.com/fauzigalih/mysql-host-name/assets/64176403/6ec47ac5-7f97-4125-a42c-3bc9438eba7d)

### Yeayy,Finish....