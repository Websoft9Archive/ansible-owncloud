# More

Each of the following solutions has been proven to be effective and we hope to be helpful to you.

## Domain binding

The precondition for **Domain binding** is have completed the **Domain resolution** for ownCloud Instance.

From the perspective of server security and subsequent maintenance considerations, the **Domain Binding** step cannot be omitted.

ownCloud domain name binding steps:

1. Connect your Cloud Server
2. Modify [vhost configuration file](/stack-components.md#apache), change the domain name item for you
   ```text
   #### ownCloud (LAMP) bind domain #### 

     <VirtualHost *:80>
     ServerName owncloud.mydomain.com # modify it for you
     DocumentRoot "/data/wwwroot/ownCloud"
     ...
     
   #### ownCloud (LEMP) bind domain #### 

     server {
      listen 80;
      server_name    owncloud.example.com; # modify it for you
     ...

   ```
3. Save it and restart [Web Service](/admin-services.md#apache)


## ownCloud change domain

You can change the domain of ownCloud by the following steps:

1. Complete the new **Domain resolution and Domain binding**
2. Modify [ownCloud configuration file](/stack-components.html#owncloud)
   ```
   'overwrite.cli.url' => 'owncloud.yourdomain.com', # Set it to your new domain
   ```
3. [Restart PHP-FPM service](/admin-services.html#php-fpm)

## ownCloud language

Log in owncloud, go to【Personal】>【General】 and set your language

![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/owncloud/owncloud-zh-websoft9.png)

## ownCloud install apps

Owncloud [Marketplace](https://marketplace.owncloud.com/) have lots of extensions(apps), the following is the step for installing apps

1. Visit [Marketplace](https://marketplace.owncloud.com/), find the app you want to use(e.g OwnBackup)
![](https://libs.websoft9.com/Websoft9/DocsPicture/en/owncloud/owncloud-searchapps-websoft9.jpg)
2. Download and unzip it
3. Upload it to your ownCloud's apps directory: *data/wwwroot/owncloud/apps*
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/owncloud/owncloud-ftp-websoft9.png)
4. Enable OwnBackup
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/owncloud/owncloud-enableapps-websoft9.png)

> You can install Marketplace's apps online from the ownCloud console also

### ownCloud LDAP

Refer to *[User Authentication with LDAP](https://doc.owncloud.org/server/admin_manual/configuration/user/user_auth_ldap.html)*

### ownCloud CLI-OCC

ownCloud's occ command (ownCloud console) is ownCloud's command-line interface. You can perform many common server operations with occ, such as installing and upgrading ownCloud, manage users, encryption, passwords, LDAP setting, and more.

## ownCloud external storage

The External Storage Support application enables you to mount external storage services and devices as secondary ownCloud storage devices. You may also allow users to mount their own external storage services.

1. Log in ownCloud console, install **External storage support** application
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/owncloud/owncloud-enablestorage-websoft9.png)

2. Open【Admin】>【Add storage】>【External Storage】, select an external storage service
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/owncloud/owncloud-enablestorage002-websoft9.png)

3. Set it
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/owncloud/owncloud-auth_mechanism-websoft9.png)

More details please refer to [External Storage](https://doc.owncloud.org/server/admin_manual/configuration/files/external_storage/index.html)

## ownCloud transfer

ownCloud source code and data is in system disk by default, you can transfer them to data disk or  Object storage:

### to data disk

1. Purchase a data disk from Cloud Platform, then **attach** it to ownCloud Server
2. Use SFTP tool to connect Server and stop service
   ```
   systemctl stop httpd
   ```
3. Create a new folder */data/wwwroot/owncloud2* 
4. Initialize data disk, and **mount** it to *owncloud2* folder
5. Copy all files in */data/wwwroot/owncloud* to */data/wwwroot/owncloud2*  
6. Modify the OwnCloud directory in  [vhost configuration file](/zh/stack-components.html#apache) 
7. Start the service
   ```
   systemctl start httpd
   ```

### to Object storage

1. Purchase Object storage from Cloud Platform, then create a new **bucket**
2. Use SFTP tool to connect Server and stop service
   ```
   systemctl stop httpd
   ```
3. Create a new folder */data/wwwroot/owncloud2* 
4. Then **mount** it to *owncloud2* folder
5. Copy all files in */data/wwwroot/owncloud* to */data/wwwroot/owncloud2*  
6. Modify the OwnCloud directory in  [vhost configuration file](/zh/stack-components.html#apache) 
7. Start the service
   ```
   systemctl start httpd
   ```
8. Set the object storage to boot automatically (different cloud platform operations)

> The **mount** command is very difficult for user, and there is a risk of copy failure if the data is exceed 10G

## ownCloud preview and edit

ownCloud can't preview and edit Office document itself, you need to integrate document Server service for ownCloud to implement this function:

1. Enable the **TCP:8080** port on **[Inbound of Security Group Rule](https://support.websoft9.com/docs/faq/tech-instance.html)**
2. Log in to OwnCloud console, go to 【Market】page
	![](https://libs.websoft9.com/Websoft9/DocsPicture/en/owncloud/owncloud-preview-1-websoft9.png)
3. Find the application【ONLYOFFICE】 and install it
4. Set the 【ONLYOFFICE】
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/owncloud/owncloud-preview-2-websoft9.png)
   > The smear in the figure should be modified to **Internet IP**
5. Refresh the ownCloud, test the preview and edit function of documentation