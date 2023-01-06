# linux server configuration
## Open port
```
sudo kill `sudo lsof -t -i:44066`
```
```
sudo iptables -I INPUT -p tcp --dport 5151 -j ACCEPT
```
## Firewall
```
sudo firewall-cmd --add-port 5050/tcp
```
```
sudo firewall-cmd --list-ports
```
## Install and config mysql:
```
sudo apt-get install mysql-server
```
```
ps -A|grep mysql
```
```
sudo pkill mysql
```
```
ps -A|grep mysqld
```
```
sudo pkill mysqld
```
```
sudo service mysql start
```
```
sudo mysql
```
mysql> ```SET GLOBAL validate_password.length = 4;```

mysql> ```SET GLOBAL validate_password.policy=LOW;```

mysql> ```ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password by 'root@sql*123456789';```

mysql> ```CREATE DATABASE mydb;```

## Install and config mongodb:
```
sudo apt remove --autoremove mongodb-org
```
```
sudo rm /etc/apt/sources.list.d/mongodb*.list
```
```
sudo apt update
```
```
echo "deb http://security.ubuntu.com/ubuntu focal-security main" | sudo tee /etc/apt/sources.list.d/focal-security.list
```
```
sudo apt-get update
```
```
sudo apt-get install libssl1.1
```
```
add new key:
```
```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 4B7C549A058F8B6B
```
```
add new repository:
```
```
echo "deb [arch=amd64] http://repo.mongodb.org/apt/ubuntu bionic/mongodb-org/4.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.2.list
```
```
sudo apt update
```
```
sudo apt install mongodb-org
```
```
systemctl enable mongod.service
```
```
systemctl start mongod.service
```
```
mongo --version
```
```
systemctl status mongod.service 
```
## Work as root
```
sudo -s
```
