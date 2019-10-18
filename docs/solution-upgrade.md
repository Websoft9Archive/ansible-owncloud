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

OwnCloud provides a very user-friendly upgrade (update) portal, which can complete the update of the main version and APP plug-in according to the update prompt of the system.

### Plugin Upgrade

1. After logging in to OwnCloud, see if there is an update notification in the upper right corner. if so, please click on the update entry in it.
  ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/owncloud/owncloud-updatenotify-websoft9.png)
2. After clicking on the update entry, enter the update interface.
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/owncloud/owncloud-updatelist-websoft9.png)
3. Click the "update" button and the system goes to "update" and wait patiently for the update
4. When all updates are completed, the update list shows "all apps are up to date"

> If there is a problem with the upgrade process, such as: unable to download the upgrade package/no read and write permissions, make sure that the network is connected/OwnCloud Directory has read and write permissions


#### Master Program Upgrade

1. Once have upgrade message "OwnCloud is available". Get more information on how to update.", you should upgrade it now
2. Go to 【Admin】>【Setting】
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/owncloud/owncloud-openupdater-websoft9.png)
3. Go to Updater<br />
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/owncloud/owncloud-updater-websoft9.png)
4. Click the button "Create a checkpoint" first
5. Click the button "Start"