The Apache Web Sever is a free and open source web server used to server content like HTML, CSS and JavaScript and is often used in conjunction with Apache Tomcat as an application server to handle business logic and data processing.

#### Installing Apache 
Typically this package is part of the default repositories for most package managers such as apt and yum. 

This website has instructions for how to do this: https://httpd.apache.org/docs/2.4/install.html

``` CentOS/REHL
sudo yum install httpd -y
```

``` Ubuntu/Debian
sudo apt install apache2 -y
```

The application is installed as a service so you need to start the service using:

```
service httpd start
```

Then you can check the service is running by using:

```
service httpd status
```

You'll also have to add a rule in your system, if you have a firewall to allow http traffic.

By default the logs are stored here:

``` sh
/var/log/httpd/access_log

OR

/var/log/httpd/error_log
```

#### Default website location

``` sh
/var/www/html
```

#### Config files

``` sh
/etc/httpd/conf/httpd.conf
```

The conf file is where you can change:

- the port the website is listening on
- the root directory of the webpage
- the servername 
- the SSL and HTTPS configurations
- Where the logs are stored
- Virtual host information


#### Virtual Hosts
You can host multiple webpages from one web server by creating virtual hosts in the config file:

``` httpd.conf
<VirtualHost *:80>
	ServerName www.houses.com
	DocumentRoot /var/www/houses
</VirtualHost>
```

Note: Any changes you make to the httpd.conf file will be loaded once the service is restarted

```
service httpd restart
```

If you want to use multiple configuration files for the each website, you have to include the below in the original httpd.conf

```
Include conf/houses.conf
Include conf/oranges.conf
```