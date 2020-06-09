# OP

## Install  

```bash
# 下载并安装MySQL官方的 Yum Repository
# wget -i -c http://dev.mysql.com/get/mysql57-community-release-el7-10.noarch.rpm
# yum -y install mysql57-community-release-el7-10.noarch.rpm

## 安装MySQL
# yum -y install mysql-community-server

## 初始化
$ mysql_install_db --user=root --datadir=/var/lib/mysql/

## 启动
$ nohup mysqld --defaults-file=/etc/my.cnf --user=root --datadir=/var/lib/mysql/ &

## 初始root密码
# cat /root/.mysql_secret
# Password set for user 'root@localhost' at 2019-05-31 06:59:19
doBAb38xSm<I

## root 登录
$ mysql -u root -p
## 输入密码

## 修改密码
mysql> ALTER USER 'root'@'localhost' IDENTIFIED BY 'root';

## 如果设置密码失败，可能是有密码设置的规范

## 授权 
mysql> grant all on *.* to root@'%' identified by 'root';
``` 



