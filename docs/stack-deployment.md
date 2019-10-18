# Deployment

**Deployment is to copy the ownCloud pre-packaged online to your Cloud Server**. For example, after the user subscribe ownCloud on the Cloud Platform, the Platform will automatically copy the ownCloud to the corresponding Cloud Server.

- If ownCloud has been deployed, go to [Initial Installation](/zh/stack-installation.md) to complete the operation.
- If ownCloud is not deployed, you need to deploy ownCloud to your cloud server first.

We offer two deployment ownCloud scenarios (the deployment results are the same):

## Deploy by Image

**Deploy by Image** means starting instance from ownCloud images. **ownCloud Image** provide OS and software environment needed for ownCloud.

For users with experience with cloud servers, Deploy by Image equated with "one-click deployment". 

Websoft9 published [ownCloud image](https://apps.websoft9.com/opencart) on Cloud Platform, three methods for your deployment:

* When **Create New Instance** , select the ownCloud image as the system boot template.
* When **Subscribe ownCloud** on Marketplace, the system will promote you to create a new instance for this image at the same time.
* When **Re-install OS** for you instance, you can replace the existing image with a ownCloud image.

## Deploy by Script

**Deploy by Script** means running a script on your cloud instance to pull the pre-packages online to your instance and configure it at the same time.

Websoft9 provide the [ownCloud ansbile automation script](https://github.com/Websoft9/ansible-opencart) on Github. If you are familiar with Ansible, you can deploy the ownCloud to the instance automaticly.

## Comparison

Although the results of the **deploy by image** are consistent with the results of **deploy by script**, what is the difference between the two deployment methods?

Suggest you read the document [Deploy by Image vs Deploy by Script](https://support.websoft9.com/docs/faq/bz-product.html#deployment-comparison)