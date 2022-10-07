#### Install packages
``` sh
sudo yum install -y httpd php php-mysql
```

#### Create firewall rule
[[Install-Mariadb#Create firewall rule]]
``` sh
sudo firewall-cmd --permanent --zone=public --add-port=80/tcp
sudo firewall-cmd --reload 
```

#### Configure website
[[apache-httpd#Config files]]
``` sh
sudo sed -i 's/index.html/index.php/g' /etc/httpd/conf/httpd.conf # update httpd.conf to use .php instead of .html
```

#### Start/Enable Service
```sh
sudo systemctl start httpd
sudo systemctl enable httpd
sudo systemctl restart httpd # in case it was already running pre-change
```

#### Test website
``` sh
curl http://localhost | grep -i title
```

#### Update index.php
``` sh
sudo sed -i 's/172.20.1.101/localhost/g' /var/www/html/index.php

# Updating this line to point to database on localhost
$link = mysqli_connect('172.20.1.101', 'ecomuser', 'ecompassword', 'ecomdb');
```

