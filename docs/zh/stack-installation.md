# 初始化安装

在云服务器上部署 ownCloud 预装包之后，请参考下面的步骤快速入门。

## 准备

1. 在云控制台获取您的 **服务器公网IP地址** 
2. 在云控制台安全组中，检查 **Inbound（入）规则** 下的 **TCP:80** 端口是否开启
3. 若想用域名访问 ownCloud，请先到 **域名控制台** 完成一个域名解析

## ownCloud 安装向导

1. 使用本地电脑的 Chrome 或 Firefox 浏览器访问网址：*http://域名* 或 *http://Internet IP*, 就进入引导首页
2. 进入安装界面，同意安装协议
   ![oc1](https://libs.websoft9.com/Websoft9/DocsPicture/en/opencart/oc1.png)  
3. 通过环境检测后，进入下一步  
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/opencart/oc2.png)
3. 填写数据库信息（[不知道账号密码？](/zh/stack-accounts.html#mysql)）并设置后台管理账号
   ![oc1](https://libs.websoft9.com/Websoft9/DocsPicture/en/opencart/oc3.png)
4. 安装成功后，系统提示“删除安装目录”
   ![oc1](https://libs.websoft9.com/Websoft9/DocsPicture/en/opencart/oc4.png)
5. 请记得通过SFTP工具删除安装目录（*/data/wwwroot/opencart/install*）
6. 安装成功，可以分别体验商城前台和后台

> 需要了解更多 ownCloud 的使用，请参考官方文档：[ownCloud Docs](http://docs.opencart.com)

## 常见问题

#### 浏览器打开IP地址，无法访问 ownCloud（白屏没有结果）？

您的服务器对应的安全组80端口没有开启（入规则），导致浏览器无法访问到服务器的任何内容

#### 本部署包采用的哪个数据库来存储 ownCloud 数据？

是MySQL

#### 是否可以采用云厂商提供的 RDS 来存储 ownCloud 数据？

可以