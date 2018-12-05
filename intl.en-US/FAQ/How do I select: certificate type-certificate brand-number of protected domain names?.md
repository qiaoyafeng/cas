# How do I select: certificate type-certificate brand-number of protected domain names? {#concept_ybd_vn5_ydb .concept}

## Certificate Type Selection {#section_ovm_vn5_ydb .section}

-   If your website is based on an individual \(I .e. no corporate business license \), you can only apply for free-type or DV-type digital certificates.
-   For general businesses, it is recommended to purchase digital certificates of Type OV and above. For financial and payment enterprises, it is recommended to purchase EV certificate.
-   If the mobile site or interface is called, it is recommended that you use certificates of Type OV and above.

**Note:** Symantec-branded ev-type certificates have Server IP restrictions. If your domain name has multiple hosts IP, and it is recommended that you purchase multiple digital certificates. If you also use one of Alibaba Cloud's other cloud products, select one of the certificates to upload to the corresponding cloud product.

## Brand Selection {#section_xxg_yn5_ydb .section}

-   The order of digital certificate brand compatibility from strong to weak: Symantec\> geotrust\> CFCA.
-   The mobile Web site or interface calls related apps, and it is recommended that you select the Symantec brand.

## Number of protected domain names {#section_rvm_vn5_ydb .section}

-   One domain name: this digital certificate can only be configured with one specific domain name.
-   Multiple Domain Names: this digital certificate can configure multiple specific domain names. These domain names can be either a top-level domain name or a non-top-level domain name, such as p1.taobao.com, p1.aliyun.com Etc.
-   Wildcard Domain Name: this digital certificate can be configured with a wildcard domain name. The wildcard domain name is typically in the form \* .aliyun.com.

    Wildcard domain names only support peer-to-peer matching, such as binding \* .aliyun.com A digital certificate for a wildcard domain name that supports, but does not support. If you need any support For the wildcard domain name digital certificate, you also need to purchase a \* wildcard Domain Name Certificate.


**Note:** 

-   In the digital certificate for the wildcard domain name, only the root domain name contains the domain name principal itself. For example:
    -   \*. Aliyun.com's wildcard domain name digital certificate contains aliyun.com.
    -   \* The wildcard domain name digital certificate for .p1.aliyun.com does not contain.
-   If the specific domain name is completed with the WWW domain name, the main domain name itself is included. For example:
    -   The digital certificate bound by the www.aliyun.com domain name contains aliyun.com.
    -   The digital certificate that is bound by the domain name does not contain the certificate.
-   Once your digital certificate is issued, you will not be able to modify domain name information, and so on.

