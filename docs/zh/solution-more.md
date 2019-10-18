# 更多...

下面每一个方案，都经过实践证明行之有效，希望能够对你有帮助

## 域名绑定

绑定域名的前置条件是：已经完成域名解析（登录域名控制台，增加一个A记录指向服务器公网IP）  

完成域名解析后，从服务器安全和后续维护考量，需要完成**域名绑定**：

ownCloud 域名绑定操作步骤：

1. 使用 SFTP 工具登录云服务器
2. 修改 [虚拟机主机配置文件](/zh/stack-components.html#apache)，将其中的域名相关的值
   ```text
   #### ownCloud(LAMP) bind domain #### 

     <VirtualHost *:80>
     ServerName  www.mydomain.com # 修改成您的实际域名
     DocumentRoot "/data/wwwroot/opencart"
     ...
     
   #### ownCloud(LNMP) bind domain #### 

     server {
      listen 80;
      server_name opencart.example.com; # 修改成您的实际域名
     ...

   ```
3. 保存配置文件，[重启服务](/zh/admin-services.html#apache)

## ownCloud 更换域名

如果 ownCloud 需要更换域名，具体操作如下：

1. 完成新的 **域名解析和域名绑定**
2. 修改 ownCloud 根目录下的配置文件 `config.php`
   ```
   // HTTP
   define('HTTP_SERVER', 'http://example.com/');
   // HTTPS
   define('HTTPS_SERVER', 'https://example.com/');
   ```
3. 修改 ownCloud 后台目录下的配置文件 `admin/config.php`
   ```
   // HTTP
   define('HTTP_SERVER', 'http://www.example.com/admin/');
   define('HTTP_CATALOG', 'http://www.example.com/');
   // HTTPS
   define('HTTPS_SERVER', 'http://www.example.com/admin/');
   define('HTTPS_CATALOG', 'http://www.example.com/');
   ```
3. [重启 PHP-FPM 服务](/zh/admin-services.html#php-fpm)后生效

## ownCloud vQmod

ownCloud 2.0 使用vQmod机制安装扩展，需提前安装并启用vQmod，具体如下：

1. [下载vQmod](https://github.com/vqmod/vqmod)
2. Go to Extensions > Installer，上传下载的 vqmod.zip 文件
3. Go to Extensions > Extensions > Modules > Integrated VQmod to install and then edit to enable this module


## ownCloud 重置密码

如果忘记了管理员密码，又没有配置好 SMTP 导致无法通过邮箱找回密码，怎么办？

1. 首先使用 [phpMyAdmin 登录 MySQL](/zh/admin-mysql.html)
2. 找到您的 ownCloud 数据库，打开SQL命令操作窗口
3. 运行如下命令
   ```
   //下面是将用户名 admin 的后台管理员密码重置为 123456，请根据实际情况调整命令
   UPDATE oc\_user SET password = md5('123456'), salt = '' WHERE username = 'admin';
   ```

## ownCloud Extension

ownCloud 提供了大量的扩展发布在 Marketplace 上，下面是具体的安装扩展步骤：

1. 在 Marketplace 上下载扩展
2. 登录 ownCloud 后台，依次打开：【Extensions】>【Installer】
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/opencart/opencart-installex-websoft9.png)
3. 上传扩展文件
4. 等待安装完成


## ownCloud 语言包

在ownCloud中增加一个新的语言（以中文包为例），主要有三个步骤：

1. 到 [ownCloud Marketplace](https://www.opencart.com/index.php?route=marketplace/extension/info&extension_id=19126&filter_category_id=2&page=8)下载中文语言包（请注意版本）；
2. 将下载好的语言包解压出来，会得到一个名为 upload 的文件夹，内有 admin 和 catalog 两个文件夹分别为后台和前台的文件夹；
3. 使用 SFTP 软件将前后台中文包分别上传到服务器：
   ```
   admin->language->zh_cn 文件夹 上传到  ```/data/wwwroot/opencart/admin/language``` 目录下
   catalog->language->zh-cn 文件夹 上传到 ```/data/wwwroot/opencart/catalog/language``` 目录下
   ```
4. 登录 ownCloud，打开【System】>【localization】>【languages】，增加一个语言并填写配置信息
	![websoft9](https://libs.websoft9.com/Websoft9/DocsPicture/zh/opencart/opencart-language-1-websoft9.png)

5. 店铺前后台分别选择所需的语言：【System】>【Settings】，其中Language 为前台默认语言，Administration Language 为后台默认语言
	   ![websoft9](https://libs.websoft9.com/Websoft9/DocsPicture/zh/opencart/opencart-language-2-websoft9.png)

6. 刷新前后台页面，系统显示新的语言

## ownCloud 目录说明

```
|–.htaccess 网址改写控制档(SEO urls)
|–config.php 系统配置文件
|–php.ini php 设定
|–download 下载类商品存放位置(由程控,非直接复制档案至此)
|–image 图片文件
|–system 框架核心

|–admin 后台
|–config.php 系统配置文件
|–|–M: adminmodel
|–|–V: adminview
|–|–C: admincontroller
|–|–L: adminlanguage

|–catalog 前台
|–|–M: catalogmodel
|–|–V: catalogview
|–|–C: catalogcontroller
|–|–L: cataloglanguage
```