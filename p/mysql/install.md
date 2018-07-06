MySQL 安装
==========

MySQL 5.7+ 安装
---------------

### centos 6.8

```sh
wget dev.mysql.com/get/mysql-community-release-el6-5.noarch.rpm
sudo yum localinstall -y mysql-community-release-el6-5.noarch.rpm
sudo yum-config-manager --disable mysql55-community
sudo yum-config-manager --disable mysql56-community
sudo yum-config-manager --enable mysql57-community-dmr
sudo yum install -y mysql-community-devel
sudo yum install -y mysql-community-server
sudo yum install -y mysql-community-client
```

### ubuntu 18.04

```sh
sudo apt -y install mysql-server
```

MySQL 8 安装
------------

> 参见 [https://ken.io/note/centos-mysql8-setup](https://ken.io/note/centos-mysql8-setup)

### centos 6.8

```sh
wget https://dev.mysql.com/get/mysql80-community-release-el6-1.noarch.rpm
sudo rpm -ivh mysql80-community-release-el6-1.noarch.rpm
sudo yum install -y mysql-community-devel
sudo yum install -y mysql-community-server
sudo yum install -y mysql-community-client
```
