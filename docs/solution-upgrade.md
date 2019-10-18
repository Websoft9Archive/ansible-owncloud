# Update & Upgrade

Updates and upgrades are one of the maintenance tasks for sytem. Programs that are not upgraded for a long time, like buildings that are not maintained for a long time, will accelerate aging and gradually lose functionality until they are unavailable.

You should know the differences between the terms **Update** and **Upgrade**([Extended reading](https://support.websoft9.com/docs/faq/tech-upgrade.html#update-vs-upgrade))
- Operating system patching is **Update**, Ubuntu16.04 to Ubuntu18.04 is **Upgrade**
- MySQL5.6.25 to MySQL5.6.30 is **Update**, MySQL5.6 to MySQL5.7 is **Upgrade**

For ownCloud maintenance, focus on the following two Update & Upgrade jobs

- Sytem update(Operating System and Running Environment) 
- ownCloud upgrade 

## System Update

Run an update command to complete the system update:

``` shell
#For Centos&Redhat
yum update -y

#For Ubuntu&Debian
apt update && apt upgrade -y
```
> This deployment package is preconfigured with a scheduled task for automatic updates. If you want to remove the automatic update, please delete the corresponding Cron

## ownCloud Upgrade

ownCloud provide two methond for Upgrade: ownCloud backend online upgrade and Composer command upgrade  

Below is the step for upgrade online:

## ownCloud Upgrade

The following upgrade steps are a simplification of the official upgrade documentation:

1. Backup ownCloud source code and database, and download them to local computer
2. [Download](https://www.opencart.com/index.php?route=cms/download) the latest version of ownCloud and unzip it
3. Use SFTP to log in Server, upload latest ownCloud source code and cover the old
4. Upload the `config.php` and `admin/config.php` in the ownCloud root directory of backup to Server
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/opencart/Opencart-update001-websoft9.png)  
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/opencart/Opencart-update002-websoft9.png) 
5. Visit *http://域名/install* to start upgrade
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/opencart/Opencart-update003-websoft9.png)  
6. Upgrading successfully
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/opencart/Opencart-update004-websoft9.png)  

> More upgrade details please refer to: [ownCloud Upgrading](https://docs.opencart.com/en-gb/upgrading/)