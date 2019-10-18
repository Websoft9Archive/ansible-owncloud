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
     ServerName opencart.mydomain.com # modify it for you
     DocumentRoot "/data/wwwroot/ownCloud"
     ...
     
   #### ownCloud (LEMP) bind domain #### 

     server {
      listen 80;
      server_name    opencart.example.com; # modify it for you
     ...

   ```
3. Save it and restart [Web Service](/admin-services.md#apache)


## ownCloud change domain

You can change the domain of ownCloud by the following steps:

1. Complete the new **Domain resolution and Domain binding**
2. Modify the ownCloud configuration `config.php` in the root directory
   ```
   // HTTP
   define('HTTP_SERVER', 'http://example.com/');
   // HTTPS
   define('HTTPS_SERVER', 'https://example.com/');
   ```
3. Modify the ownCloud configuration `admin/config.php` in the root directory
   ```
   // HTTP
   define('HTTP_SERVER', 'http://www.example.com/admin/');
   define('HTTP_CATALOG', 'http://www.example.com/');
   // HTTPS
   define('HTTPS_SERVER', 'http://www.example.com/admin/');
   define('HTTPS_CATALOG', 'http://www.example.com/');
   ```
3. [Restart PHP-FPM Service](/admin-services.html#php-fpm)

## ownCloud vQmod

ownCloud 2.0 using **vQmod** for installing extensions, so you need to install and enable vQmod:

1. [Download vQmod](https://github.com/vqmod/vqmod)
2. Go to Extensions > Installer, upload **vqmod.zip**
3. Go to Extensions > Extensions > Modules > Integrated VQmod to install and then edit to enable this module


## ownCloud reset password

If you have forgotten the administrator password of ownCloud and can not reset by email, this solution is useful for you:

1. Use [phpMyAdmin](/admin-mysql.html) to log in MySQL
2. Find the database of ownCloud, open the command windows of SQL
3. Run below command
   ```
   //set the username admin's password to 123456, you can modify this command yourself
   UPDATE oc\_user SET password = md5('123456'), salt = '' WHERE username = 'admin';
   ```

## ownCloud Extension

ownCloud have 13000+ extention published on the Marketplace, how to insatll them?

1. Find the extension you want to used on Marketplace and download it
2. Log in ownCloud console, open:【Extensions】>【Installer】
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/opencart/opencart-installex-websoft9.png)
3. Upload your extension compressed file
4. Installing it


## ownCloud language

Enable a new language package in ownCloud have the following steps(e.g Chinese lanuage)

1. Go to [ownCloud Marketplace](https://www.opencart.com/index.php?route=marketplace/extension/info&extension_id=19126&filter_category_id=2&page=8), download suitable lanuage package
2. Unzip package, you can see a folder name `upload` that includes two folder `admin`, `catalog`
3. Use SFTP to upload them to your Server
   ```
   admin->language->zh_cn  to  ```/data/wwwroot/opencart/admin/language``` 
   catalog->language->zh-cn to ```/data/wwwroot/opencart/catalog/language```
   ```
4. Log in ownCloud, go to【System】>【localization】>【languages】, add new language and configure it
	![websoft9](https://libs.websoft9.com/Websoft9/DocsPicture/zh/opencart/opencart-language-1-websoft9.png)

5. Enable language both for catalog and admin: open 【System】>【Settings】, the 【Language】 for catalog, 【Administration Language】for admin
	   ![websoft9](https://libs.websoft9.com/Websoft9/DocsPicture/zh/opencart/opencart-language-2-websoft9.png)

6. Refresh ownCloud, display the new language