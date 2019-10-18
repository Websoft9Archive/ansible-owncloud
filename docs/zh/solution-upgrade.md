# 更新升级

网站技术日新月异，**更新升级**是维护工作之一，长时间不升级的程序，就如长时间不维护的建筑物一样，会加速老化、功能逐渐缺失直至无法使用。  

这里注意更新与升级这两词的差异（[延伸阅读](https://support.websoft9.com/docs/faq/zh/tech-upgrade.html#更新-vs-升级)），例如：  

- 操作系统打个补丁常称之为**更新**，Ubuntu16.04 变更为 Ubuntu18.04，称之为**升级**
- MySQL5.6.25-->MySQL5.6.30 常称之为**更新**，MySQL5.6->MySQL5.7 称之为**升级**

ownCloud 完整的更新升级包括：系统级更新（操作系统和运行环境）和 ownCloud 程序升级两种类型

## 系统级更新

运行一条更新命令，即可完成系统级更新：

``` shell
#For Centos&Redhat
yum update -y

#For Ubuntu&Debian
apt update && apt upgrade -y
```
> 本部署包已预配置一个用于自动更新的计划任务。如果希望去掉自动更新，请删除对应的Cron


## ownCloud 升级

以下升级步骤是官方升级文档的简化：

1. 备份 ownCloud 程序和数据库文件，下载到本地
2. [下载](https://www.opencart.com/index.php?route=cms/download)最新的 ownCloud 程序
3. 使用 SFTP 登录服务器，上传新的代码，覆盖原来的文件
4. 将本地备份的 ownCloud 根目录下的 `config.php` 文件和 `admin/config.php` 重新上传到服务器
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/opencart/Opencart-update001-websoft9.png)  
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/opencart/Opencart-update002-websoft9.png) 
5. 浏览器访问：*http://域名/install* 开始升级
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/opencart/Opencart-update003-websoft9.png)  
6. 升级成功提示 
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/opencart/Opencart-update004-websoft9.png)  

参考官方升级文档：[Upgrading](https://docs.opencart.com/en-gb/upgrading/)