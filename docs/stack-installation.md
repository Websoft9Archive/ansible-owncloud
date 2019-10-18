# Initial Installation

If you have completed the ownCloud deployment on Cloud Platform, the following steps is for you to start use it quikly

## Preparation

1. Get the **Internet IP** on your Cloud Platform
2. Check you **[Inbound of Security Group Rule](https://support.websoft9.com/docs/faq/tech-instance.html)** of Cloud Console to ensure the TCP:80 is allowed
3. Make a domain resolution on your DNS Console if you want to use domain for ownCloud

## ownCloud Installation Wizard

1. Using local Chrome or Firefox to visit the URL *https://domain* or *https://Internet IP*, start to install    
2. Agree license, Click "Continue"
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/opencart/oc1.png)
3. Verify the environment and go to next step  
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/opencart/oc2.png)
4. Database connection configuration, you can use the MySQL in this Server([Don's know password?](/stack-accounts.html#mysql)), and you can use other database services
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/opencart/oc3.png)
5. When the installation is completed,it will go the following interface
   ![](https://libs.websoft9.com/Websoft9/DocsPicture/en/opencart/oc4.png)
6. Please delete */data/wwwroot/opencart/install* folder.
7. You can use ownCloud now

> Refer to [ownCloud Docs](https://docs.opencart.com/) to get more details

## Q&A

#### I can't visit the start page of ownCloud?

Your TCP:80 of Security Group Rules is not allowed so there no response from Chrome or Firefox

#### Which database does this ownCloud package use?

MySQL

#### Can I use Cloud database for ownCloud?

Yes