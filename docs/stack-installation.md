# Initial Installation

If you have completed the ownCloud deployment on Cloud Platform, the following steps is for you to start use it quikly

## Preparation

1. Get the **Internet IP** on your Cloud Platform
2. Check you **[Inbound of Security Group Rule](https://support.websoft9.com/docs/faq/tech-instance.html)** of Cloud Console to ensure the TCP:80 is allowed
3. Make a domain resolution on your DNS Console if you want to use domain for ownCloud

## ownCloud Installation Wizard

1. Using local Chrome or Firefox to visit the URL *https://domain* or *https://Internet IP*, start to install    
2. You need to set administrator account, then 【Storage&Database】
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/owncloud/owncloud-installsetadmin-websoft9.png)
3. Suggest you select **MySQL** for your database    
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/owncloud/owncloud-installdb001-websoft9.png)
4. Configure the MySQL database connection([Don't know password?](/stack-accounts.html#mysql))  
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/owncloud/owncloud-installdb002-websoft9.jpg)
5. Click 【Flish Setup】, it has been installed successfully.
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/zh/owncloud/owncloud-installcomplete-websoft9.png)

> Refer to [ownCloud admin_manual](https://doc.owncloud.org/server/admin_manual/) to get more details

## Q&A

#### I can't visit the start page of ownCloud?

Your TCP:80 of Security Group Rules is not allowed so there no response from Chrome or Firefox

#### Which database does this ownCloud package use?

MySQL

#### Can I use Cloud database for ownCloud?

Yes

#### Can I use Object storage for ownCloud?

Yes, but the configuration is very sufficient