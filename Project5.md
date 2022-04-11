# CLIENT-SERVER ARCHITECTURE WITH MYSQL

## 1 - Create and Configure two EC2 Instances in AWS

![EC2](PBL-5/EC2.png)

## 2 - Install mysql-server software on A (mysql server) and configure mysql

```bash
	sudo apt install mysql-server

	sudo mysql

	sudo vim /etc/mysql/mysql.conf.d/mysqld.cnf
```

![Server](PBL-5/s1.png)

![Server](PBL-5/s2.png)

![Server](PBL-5/s3.png)

![Server](PBL-5/s4.png)

## 3 - Open the MySQL port on the security group to allow remote access to the database

![Security](PBL-5/perm.png)

## 4 - Install mysql-client software on A (mysql client) connect to the server


```bash
	sudo apt install mysql-client

	sudo mysql -u test_user -p
```

![Client](PBL-5/c1.png)

![Client](PBL-5/c2.png)

![Client](PBL-5/c3.png)

