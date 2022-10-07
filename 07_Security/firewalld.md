#### Install
``` Shell
sudo yum install firewalld -y
```

#### Check Version
```shell
sudo firewall-cmd --version
```

#### Check Status
```shell
sudo service firewalld status
```

#### Start/Stop Service
```shell
sudo service firewalld start/stop
```

#### Enable Service
``` shell
sudo systemctl enable firewalld # launch on startup
```

#### Reload Service
``` shell
sudo service firewalld reload # required to apply changes
```

#### List rules
```shell
sudo firewalld-cmd --list-all
```

#### Config File
``` dir
/etc/firewalld/firewalld.conf
```

#### Enable Rejection Logging
```shell
LogDenied=all # set in /etc/firewalld/firewalld.conf
```

#### Redirect rejection logs
``` Shell
sudo vim /etc/rsyslog.d/firewalld-droppd.conf # create the file
```

``` shell
# add this to firewalld-droppd.conf
:msg,contains,"_DROP" /var/log/firewalld-droppd.log
:msg,contains,"_REJECT" /var/log/firewalld-droppd.log
& stop
```

``` shell
# restart service
sudo service rsyslog reload
```

#### Monitor rejections
``` shell
sudo tail -f /var/log/firewalld-droppd.log
```

#### Add rule
``` shell
sudo firewall-cmd --permanent --zone=public --add-port=3306/tcp
sudo firewall-cmd --reload # must reload for rules to take affect
```

[[Install-Mariadb]]


