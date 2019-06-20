# What to do if Domain Name authentication fails to push to Alibaba Cloud DNS? {#concept_k4j_xq5_ydb .concept}

## Issue Description {#section_er8_0cy_tww .section}

Your domain name is hosted in the cloud Resolution Service of Ali cloud, you authorize the Certificate Services system to automatically complete the domain name configuration, but the domain name authorization authentication configuration failed to push.

## Solutions {#section_ou1_38z_9mx .section}

**Note:** Verify that your domain name is hosted in the cloud Resolution Service in ALI cloud. If your domain name is hosted at a different domain name resolution service provider, certificate Services failed to complete domain name authorization authentication configuration push.

If you confirm that your domain name is successfully hosted in the Ali cloud Resolution Service, and the domain name authorization authentication configuration failed to push, you need to manually configure domain name authorization to the Ali cloud domain name resolution service. For domain name authorization authentication configuration, refer to [how to configure domain name authorization authentication](reseller.en-US/FAQ/FAQ/How do I configure domain name authorization?.md#).

 **To manually configure domain name authorization verification steps** 

1.  Log in to [Ali cloud domain name management system](https://netcn.console.aliyun.com/core/domain/tclist).
2.  Select the domain name that you want to configure, and click **Configure**.
3.  On the **Configure** page, click **Add Record**, adds a TXT parsing record based on the requirements of the domain name authorization authentication configuration.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13592/15610402364244_en-US.png)

    **Note:** If a cname record exists in your domain name resolution, temporarily remove the cname record, otherwise, you will not be able to pass domain name authorization verification. After the digital certificate is issued, you can delete the added TXT record and re-Add Cname records. If the cname record cannot be deleted, verify the domain name authorization via file authentication.

4.  After the DNS resolution takes effect, check the domain name authorization authentication configuration in SSL Certificate Console.

