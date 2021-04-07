# 初始化安装

在云服务器上部署 ownCloud 预装包之后，请参考下面的步骤快速入门。

## 准备

1. 在云控制台获取您的 **服务器公网IP地址** 
2. 在云控制台安全组中，检查 **Inbound（入）规则** 下的 **TCP:80** 和 **TCP:9002** 端口是否开启
3. 若想用域名访问 ownCloud，请先到 **域名控制台** 完成一个域名解析

## ownCloud 安装向导

1. 使用本地电脑的 Chrome 或 Firefox 浏览器访问网址：*http://域名* 或 *http://Internet IP*, 就进入引导首页

2. 系统首先要求设置一个管理员账号，请设置好并牢记之，然后点击【Storage&Database】
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/owncloud/owncloud-installsetadmin-websoft9.png)

3. 选择 OwnCloud 的数据库存储方式，建议选择【MySQL】    
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/owncloud/owncloud-installdb001-websoft9.png)

4. 填写 MySQL 数据库连接信息（[不知道账号密码？](/zh/stack-accounts.html#mysql)）  
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/owncloud/owncloud-installdb002-websoft9.jpg)

5. 点击【Flish Setup】，完成安装，获得安装成功的提示，开始体验后台
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/owncloud/owncloud-installcomplete-websoft9.png)

6. [设置文档预览与编辑](/zh/solution-more.md#owncloud-文件预览与编辑)功能（非必要）

> 需要了解更多 ownCloud 的使用，请参考官方文档：[ownCloud admin_manual](https://doc.owncloud.org/server/admin_manual/)

## 常见问题

#### 浏览器打开IP地址，无法访问 ownCloud（白屏没有结果）？

您的服务器对应的安全组80端口没有开启（入规则），导致浏览器无法访问到服务器的任何内容

#### 本部署包采用的哪个数据库来存储 ownCloud 数据？

是MySQL

#### 是否可以采用云厂商提供的 RDS 来存储 ownCloud 数据？

可以

#### ownCloud 是否支持采用对象存储作为网盘使用？

支持，但需要额外配置
