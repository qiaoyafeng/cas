# Overview {#concept_dbr_gxn_yfb .concept}

This document provides an overview of operations on Alibaba Cloud SSL Certificates Service and the main modules of its console.

You can manage and perform operations on certificates in the Alibaba Cloud SSL Certificates console as follows:

-   Purchase SSL certificates
-   View SSL certificate status
-   Manage certificates:
    -   [Upload certificates](reseller.en-US/User Guide/Upload certificates.md#) to the console for unified management
    -   [Apply for certificates](reseller.en-US/User Guide/Apply for and validate certificates.md#) and withdraw certificate applications
    -   [Deploy issued certificates to Alibaba Cloud products](reseller.en-US/User Guide/Deploy issued certificates to Alibaba Cloud products.md#)
    -   Download issued certificates and [Install them in other types of servers](reseller.en-US/User Guide/Download and install SSL certificates/Install SSL certificates in Tomcat servers/Install .pfx SSL certificates.md#)
    -   Delete/[Revoke certificates](reseller.en-US/User Guide/Revoke certificates.md#)
-   Renew the certificates that will expire

## Console layout mode {#section_xt3_yrr_yfb .section}

The Alibaba Cloud SSL Certificates console supports two layout modes. You can click either of the layout icons at the top of the console to select the desired layout mode.

![0](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65311/156586128933494_en-US.png)

All operations in this document are based on the **card view**.

-   Card view

    ![2](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65311/156586129044712_en-US.jpg)

-   List view

    ![3](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65311/156586129044713_en-US.jpg)


## Purchase SSL certificates {#section_mkl_1zn_yfb .section}

On the SSL Certificates page, click **Purchase Certificate** in the upper-right corner. For more information, see [Select and purchase certificates](reseller.en-US/User Guide/Select and purchase certificates.md#).

![4](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65311/156586129033282_en-US.png)

Multiple types of SSL certificates are available. For more information, see [Features](../../../../reseller.en-US/Product Introduction/Features.md#).

## View SSL certificate status {#section_jpr_1zn_yfb .section}

You can view the status of your certificate on the SSL Certificates page.

![5](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65311/156586129033287_en-US.png)

The certificate statuses are as follows:

-   **Ordered:** The certificate has been paid for and can be used upon application and review.
    -   Paid
    -   Pending Verification
    -   Revoked
-   **Issued:** The certificate has been issued upon payment, application, and review. You can deploy the certificate to the target Alibaba Cloud product or download or delete it.
    -   Expired: The certificate has expired and you need to purchase and apply for a new one to ensure website security.

## Manage certificates {#section_lfs_1zn_yfb .section}

You can manage certificates and deploy them to Alibaba Cloud products on the SSL Certificates page. You can view certificate status and validity, upload other certificates to the SSL certificate console, and delete/revoke SSL certificates.

-   **Upload certificates to the console for unified management:** You can upload other types of certificates to the console for deployment to Alibaba Cloud products or unified management.

    ![6](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65311/156586129033311_en-US.png)

-   **Apply for certificates and withdraw certificate applications:** You can apply for a purchased certificate or withdraw certificate applications.

    **Note:** Applications cannot be withdrawn after the certificate is issued.

-   **Deploy to cloud products:** You can deploy issued certificates to Alibaba Cloud products.

    ![8](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65311/156586129033316_en-US.png)

    **Note:** At present, your certificates can be deployed to CDN and SLB.

-   **Download certificates:** You can download issued certificates and install them in your web server.

    ![9](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65311/156586129033344_en-US.png)

-   **Delete/revoke certificates:** You can delete or revoke certificates that have been issued and are no longer in use.

    ![10](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65311/156586129033346_en-US.png)

    **Note:** Deleted certificates cannot be restored, so proceed with caution.

    **Note:** We will refund full payment to you if you revoke a certificate within 30 days after it is issued. However, any revocation after 30 days is non-refundable.


