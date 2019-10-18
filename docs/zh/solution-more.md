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
     DocumentRoot "/data/wwwroot/owncloud"
     ...
     
   #### ownCloud(LNMP) bind domain #### 

     server {
      listen 80;
      server_name owncloud.example.com; # 修改成您的实际域名
     ...

   ```
3. 保存配置文件，[重启服务](/zh/admin-services.html#apache)

## ownCloud 更换域名

如果 ownCloud 需要更换域名，具体操作如下：

1. 完成新的域名解析和域名绑定
2. 修改 [OwnCloud 配置文件](/zh/stack-components.html#owncloud)中的域名值
   ```
   'overwrite.cli.url' => 'owncloud.yourdomain.com', # 修改为新域名
   ```
2. [重启 PHP-FPM 服务](/zh/admin-services.html#php-fpm)后生效

## ownCloud 设置语言

登录owncloud，在后台 【Personal】>【General】中设置语言

![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/owncloud/owncloud-zh-websoft9.png)

## ownCloud 安装扩展

Owncloud [Marketplace](https://marketplace.owncloud.com/) 包含大量的扩展（也叫apps），下面介绍如何安装它们

1. 访问 [Marketplace](https://marketplace.owncloud.com/) ，搜索所需的应用（以 OwnBackup 为例）
![](https://libs.websoft9.com/Websoft9/DocsPicture/en/owncloud/owncloud-searchapps-websoft9.jpg)
2. 下载并解压
3. 上传到 ownCloud 应用目录：*data/wwwroot/owncloud/apps*
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/owncloud/owncloud-ftp-websoft9.png)
4. 启用 OwnBackup
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/owncloud/owncloud-enableapps-websoft9.png)

> 除了下载安装之外，也可以通过 ownCloud 后台在线安装 Marketplace 应用

### ownCloud 集成 LDAP

当企业网盘与多个人使用的时候，用户需要与内部域控集成，以保证用户可以通过Windows账号集成。

OwnCloud提供了 LDAP 集成工具，具体参考官方方案：*[User Authentication with LDAP](https://doc.owncloud.org/server/admin_manual/configuration/user/user_auth_ldap.html)*

### ownCloud 命令行工具-OCC

OCC命令是OwnCloud的命令行界面。您可以使用OCC执行许多常见的服务器操作，例如安装和升级OwnCloud，管理用户，加密，密码，LDAP设置等。

## ownCloud 连接外部存储

ownCloud 支持多种流行的企业存储服务，具体使用步骤如下：

1. 登录 ownCloud 后台，安装 **External storage support** 扩展
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/owncloud/owncloud-enablestorage-websoft9.png)

2. 打开：【Admin】>【Add storage】>【External Storage】，选择一个外部存储服务
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/owncloud/owncloud-enablestorage002-websoft9.png)

3. 根据实际情况进行设置
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/owncloud/owncloud-auth_mechanism-websoft9.png)

更多详情参考官方文档：[External Storage](https://doc.owncloud.org/server/admin_manual/configuration/files/external_storage/index.html)

## ownCloud 数据转移

ownCloud 的程序和数据文件默认均存在系统盘，你要转移到数据盘（或对象存储），步骤如下：

### 转移到数据盘

1. 在服务器所在的云平台上购买数据盘，并**挂载**到 OwnCloud 服务器
2. 使用 SFTP 工具连接服务器，停止服务
   ```
   systemctl stop httpd
   ```
3. 新建一个 */data/wwwroot/owncloud2* 文件夹
4. 初始化数据盘，并将数据盘 **mount** 到新建的 *owncloud2* 文件夹
5. 将 */data/wwwroot/owncloud* 下的数据全部拷贝到 */data/wwwroot/owncloud2*  
6. 修改 OwnCloud [虚拟主机配置文件](/zh/stack-components.html#apache) 的路径
7. 启动服务后生效
   ```
   systemctl start httpd
   ```

### 转移到对象存储

1. 在服务器所在的云平台上购买对象存储，新建一个 **bucket**
2. 使用 SFTP 工具连接服务器，停止服务
   ```
   systemctl stop httpd
   ```
3. 新建一个 */data/wwwroot/owncloud2* 文件夹
4. 将对象存储的 bucket **mount** 到新建的 *owncloud2* 文件夹
5. 将 */data/wwwroot/owncloud* 下的数据全部拷贝到 */data/wwwroot/owncloud2*  
6. 修改 OwnCloud [虚拟主机配置文件](/zh/stack-components.html#apache) 的路径
7. 启动服务后生效
   ```
   systemctl start httpd
   ```
8. 设置对象存储开机自动挂载（不同云平台操作不同）

> 以上两种数据转移方案中，**mount** 操作对新手来说是几乎是不可能独立完成的任务。另外，如果转移的数据超过10G，会存在拷贝失败的风险

## ownCloud 文件预览与编辑

ownCloud 自身是不能对 Office 文件进行预览或编辑的，需要集成外部的 Office 文档编辑和预览服务才可以具备这样的功能。  

Websoft9 提供的 ownCloud 部署包内置了 OnlyOffice Document Server(Docker版) ，此软件可以用于给 OwnCloud 提供文档预览与编辑服务，具体设置步骤如下：

1. 开启服务器安全组的 8080 端口
2. 登录到 OwnCloud ，单击左上角进入【Market】页面
	![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/owncloud/owncloud-preview-1-websoft9.png)
3. 找到【ONLYOFFICE】插件，安装它
4. 安装完成后，找到**设置**页面，对 ONLYOFFICE 进行如图所示的设置
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/owncloud/owncloud-preview-2-websoft9.png)
   > 图中涂抹处应修改为**服务器公网IP**
5. 返回到首页，刷新或重新登录，然后单击 Office 文件即可在线预览和编辑。