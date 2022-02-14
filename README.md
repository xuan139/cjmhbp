Server software list
1. Ubuntu 18.04  apt update 到最新
2. Nginx 或自带   参考安装过程，并为nodejs 3000 端口配置
3. Node&NMP ExpressJs PM2 框架 安装
4. Mysql Server 8 安装
5. https://certbot.eff.org/  for HTTPS 安装
6. domain name  for  HTTPS 申请
7. crontab for linux
8. crontab command : curl command :curl -X POST -H "Content-Type: application/json" -d @data.json http://139.155.80.163:3000/medicaljson  上传json文件

9. format of json
[
  {
    "machine_id": "M003",
    "patient_id": "Laolee",
    "timestamp": "2022-02-14 10:00:00",
    "hbp_data": "139/70/80"
  },
  {
    "machine_id": "M003",
    "patient_id": "Laolee",
    "timestamp": "2022-02-14 10:00:00",
    "hbp_data": "139/70/80"
  },
  {
    "machine_id": "M003",
    "patient_id": "Laolee",
    "timestamp": "2022-02-14 10:00:00",
    "hbp_data": "139/70/80"
  },
  {
    "machine_id": "M003",
    "patient_id": "Laolee",
    "timestamp": "2022-02-14 10:00:00",
    "hbp_data": "139/70/80"
  },
  {
    "machine_id": "M003",
    "patient_id": "Laolee",
    "timestamp": "2022-02-14 10:00:00",
    "hbp_data": "139/70/80"
  },
  {
    "machine_id": "M003",
    "patient_id": "Laolee",
    "timestamp": "2022-02-14 10:00:00",
    "hbp_data": "139/70/80"
  },
  {
    "machine_id": "M003",
    "patient_id": "LaoLee",
    "timestamp": "2022-02-14 10:02:00",
    "hbp_data": "145/80/80"
  }
]





MySQL install

1. 彻底删除以前的mysql 版本
“remove mysql from ubuntu 18.04 completely” Code Answer's
$ sudo apt-get remove --purge mysql-server mysql-client mysql-common -y.
$ sudo apt-get autoremove -y.
$ sudo apt-get autoclean.
$ sudo rm -rf /etc/mysql.
$ sudo find / -iname 'mysql*' -exec rm -rf {} \;

2. 安装

https://www.digitalocean.com/community/tutorials/how-to-install-mysql-on-ubuntu-18-04

3.修改初始root密码 Ubuntu 类似

https://blog.51cto.com/u_15473262/4880040


host     = localhost
user     = debian-sys-maint
password = 9C8BUVJ4rbEMhFDA
socket   = /var/run/mysqld/mysqld.sock
[mysql_upgrade]
host     = localhost
user     = debian-sys-maint
password = 9C8BUVJ4rbEMhFDA
socket   = /var/run/mysqld/mysqld.sock

4. mysql 8  在node下连接的问题
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '你的密码'; 

5. 修改配置文件 


sudo nano /etc/mysql/mysql.conf.d/mysqld.cnf

3.1 bind_address = 127.0.0.1 改为 0.0.0.0
3.2 解决// Access denied for user 'root'@'118.117.76.219' (using password: YES)

CREATE USER 'root'@'%' IDENTIFIED BY '1qa2ws#ED';
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%';
FLUSH PRIVILEGES;

6. 其他
启动mysql：
方式一：sudo /etc/init.d/mysql start
方式二：sudo service mysql start
停止mysql：
方式一：sudo /etc/init.d/mysql stop
方式二：sudo service mysql stop
重启mysql：
方式一：sudo/etc/init.d/mysql restart
方式二：sudo service mysql restart

NodeJs 安装

To install Node.js and npm from the NodeSource repository, follow these steps:

Enable the NodeSource repository by running the following curl command as a user with sudo privileges :

curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
The command will add the NodeSource signing key to your system, create an apt sources repository file, install all necessary packages and refresh the apt cache.

If you need to install another version, for example 14.x, just change setup_12.x with setup_14.x
Once the NodeSource repository is enabled, install Node.js and npm by typing:

sudo apt install nodejs
The nodejs package contains both the node and npm binaries.

Verify that the Node.js and npm were successfully installed by printing their versions:

node --version
v12.16.3
npm --version
6.14.4
Install ExpressJs 
Install PM2 

Nginx 安装
