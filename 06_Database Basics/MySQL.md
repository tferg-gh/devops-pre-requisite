A popular SQL Database. Used by websites like Facebook & Google & Youtube. There are two additions, a community addition which is free and a number of commercial editions for enterprise.

#### Downloading MySQL
https://dev.mysql.com/downloads/

```
curl -OL https://dev.mysql.com/get/mysql80-community-release-el8-4.noarch.rpm
```

[[curl]]

#### Installing MySQL
Add the repository
```
rpm -ivh mysql80-community-release-el8-4.noarch.rpm
```

Then

```
yum install mysql-server
```

#### Starting MySQL
MySQL is installed as a service so to start it use:
```
service mysqld start
```

To check the status of the service use:
```
service mysqld status
```

This is the simplest form of installing a MySQL database. In a production environment you would be making users and groups and other steps that will be contained in the installation documentation. 

#### Default Install location
```
/var/lib/mysql
```

#### Checking Logs
Logs are stored here:
```
cat /var/log/mysqld.log
```
You can see the version here and the port it listens on which by default is 3306

#### Connecting to the database
The logs contain temporary password for root user.
```
mysql -u root -pP4ssW0rd!
```
*Notice how there is no space between the -p and the password itself*

#### Change the default password
```MySQL
ALTER USER 'root'@'localhost' IDENTIFIED BY 'MyNewPassw0rd!';
```
*You cannot run any other commands until you've done this*

You can also do this running the mysql_secure_installation shell script

#### Show databases
```MySQL
SHOW DATABASES;
```
A single instance can host multiple databases

#### Default Databases
```
information_schema
mysql
performance_schema
sys
```
These are system databases used to run mysql

#### Create a database 
```MySQL
CREATE DATABASE school;
```

#### Switching databases
You can only work on one database at a time and have to use this to select a database
```MySQL
USE school;
```

#### Creating a table
```MySQL
CREATE TABLE persons (
	Name varchar(255),
	Age int,
	Location varchar(255)
):
```
*Notice how you have to specify the name and data type for the column*

#### Show tables
``` MySQL
SHOW TABLES;
```

#### Insert data into a table
```MySQL
INSERT INTO persons values ("John Doe",45,"New York");
```
The values correspond to each column

#### View data
```MySQL
SELECT * FROM persons;
```

#### Create Users
```MySQL
CREATE USER 'john'@'localhost' IDENTIFIED BY 'MyNewPass4!';
```

@'localhost' means that this user can only connect to the database while on the localhost machine. 

#### Remote Users
``` MySQL
CREATE USER 'john'@'192.168.1.10' IDENTIFIED BY 'MyNewPass4!';
```
 OR
 ``` MySQL
CREATE USER 'john'@'%' IDENTIFIED BY 'MyNewPass4!';
```
The '%' means all systems, not just an IP address

#### Permissions / Privileges
```MySql
GRANT <PERMISSION>, <PERMSSION> ON <DB.TABLE> TO 'john'@'%';
```

![[Pasted image 20220608133146.png]]

Use a * to indicate all databases or all tables in a database

```Mysql
GRANT ALL PRIVILEGES ON *.* TO 'john'@'%';
```

#### View a users permissions
```mysql
SHOW GRANTS FROM 'john'@'localhost';
```

