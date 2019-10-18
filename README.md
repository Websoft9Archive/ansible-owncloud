# ownCloud

此项目是用Ansible编写的ownCloud自动安装程序。执行完 cwnCloud 的 ansible 脚本后，再执行 ansible-documentserver 脚本。

## 环境要求

### 基础环境要求

ownCloud官方对于环境的要求为：https://doc.owncloud.org/server/10.2/admin_manual/installation/system_requirements.html

~~~
Database
MySQL or MariaDB 5.5+
Oracle 11g
PostgreSQL 9 (versions 10 and above are not yet supported)
SQLite

Web server
Apache 2.4 with prefork and mod_php
PHP Runtime
7.0, 7.1, and 7.2
~~~

基于官方的要求，本程序仅适用于Websoft9的基础环境，包括：

* LAMP
* LNMP（暂时不支持）

本程序在php7.0,mysql5.6下测试运行正常

### 操作系统要求

* CentOS7.X
* Ubuntu（暂时不支持）

### 服务器配置要求

* 建议最低配置1核1G
cc

## 版本

通过下载地址控制版本

## 文档

参考：https://support.websoft9.com/docs/owncloud