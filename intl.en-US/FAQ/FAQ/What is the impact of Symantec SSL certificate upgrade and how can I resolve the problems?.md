# What is the impact of Symantec SSL certificate upgrade and how can I resolve the problems? {#concept_f2n_3bh_d2b .concept}

From mid-October, 2018, Google Chrome no longer trusts some Symantec and GeoTrust SSL certificates. Therefore, Symantec has published a root certificate upgrade plan for Google Chrome. To ensure compatibility with Google Chrome, we recommend that you replace your Symantec SSL certificates based on this document.

## Affected scope {#section_ycg_2ch_d2b .section}

Symantec SSL certificates of the following time ranges will be affected by the Symantec root certificate upgrade plan and need to be replaced before the specified date.

-   SSL certificates that were issued before June 1, 2016 and will expire after March 18, 2018

    You need to replace the certificates before March 18, 2018 and deploy new certificates.

-   SSL certificates that were issued after June 1, 2016 and will expire after September 13, 2018

    You need to replace the certificates before September 13, 2018 and deploy new certificates.


**Note:** According to Symantec, Symantec has applied a new certificate issuance system since December 1, 2017 and the SSL certificates issued after December 1, 2017 are compatible with Google Chrome.

Symantec SSL certificates of the following time ranges will not be affected by the root certificate upgrade plan:

-   SSL certificates that were issued before June 1, 2016 and will expire before March 2018
-   SSL certificates that were issued after June 1, 2016 and will expire before September 2018

## Certificate replacement service {#section_fhl_xgh_d2b .section}

Since June 2018, Alibaba Cloud has enabled a replacement and upgrade service for affected Symantec SSL certificates.

-   For affected OV or EV SSL certificates, reviewers from Certificate Authority will confirm information with you by phone and then issue new SSL certificates to you.

    **Note:** If you find orders for OV or EV SSL certificates in Verifying state in the , wait for the notice from Certificate Authority. Carefully read the confirmation email from Certificate Authority and then click **Agree** or **Approve**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/14803/15610402966352_en-US.png)

-   For affected DV SSL certificates, Alibaba Cloud personnel will submit an application for certificate reissuance. You need to complete domain verification as prompted in the .

    **Note:** If your orders for DV SSL certificates meet the following conditions, the system will automatically add DNS records for domain verification.

    -   Domain verification has been completed through DNS.
    -   The domain name bound to the certificate is managed by Alibaba Cloud DNS.
    -   The SSL Certificates Service system has been authorized to add DNS records automatically.
    ![](images/6322_en-US.png)


![](images/6321_en-US.png)

