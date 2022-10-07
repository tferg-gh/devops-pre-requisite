#### Install
```shell
sudo yum install -y mariadb-server
```

#### Configure
```shell
vim /etc/my.cnf
```

#### Start
```shell
sudo systemctl start mariadb
```

#### Enable
```shell
sudo systemctl enable mariadb
```

#### Create firewall rule
``` shell
sudo firewall-cmd --permanent --zone=public --add-port=3306/tcp
sudo firewall-cmd --reload
```

[[firewalld]]
[[MySQL]]

#### Databases
```shell
/var/lib/mysql # by default
```

#### Logs
``` shell
/var/log/mariadb/mariadb.log
```

#### Login
``` shell
mysql -u root -p # root user password blank
```

#### Create user
``` sql
CREATE USER 'ecomuser'@'localhost' IDENTIFIED BY 'ecompassword';
```

#### List users
```sql
select * from mysql.user
```

#### Grant permissions
```sql
GRANT ALL PRIVILEGES ON *.* TO 'ecomuser'@'localhost';
FLUSH PRIVILEGES;
```

#### Create db
``` sql
CREATE DATABASE ecomdb;
```

### List dbs
``` sql
SHOW DATABASES;
```

#### Run script
``` shell
mysql < script.sql
```

