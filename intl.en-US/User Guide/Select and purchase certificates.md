# Select and purchase certificates {#concept_k5n_hxn_yfb .concept}

On the Alibaba Cloud SSL certificate purchase page, you can select and purchase a certificate.

## Procedure {#section_cwd_lrp_yfb .section}

1.  Go to the [Alibaba Cloud SSL Certificate](http://icms.alibaba-inc.com/tasks/submitted/review/127219?version=447) purchase page.
2.  Select the target certificate configuration.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65312/155620463433353_en-US.png)

    For information about the certificate brand, type, and other items, see [SSL certificate configuration table](#section_e3v_wvp_yfb) in this document.

3.  Select the quantity and validity period of certificates.

    **Note:** For all certificate types, the validity period is up to two years. The following types of certificates are valid only for one year from the date of application approval and must be purchased and requested again upon expiration:

    -   GeoTrust**wildcard DV SSL**
    -   Symantec**free DV SSL**
    -   Symantec**wildcard DV SSL**
4.  After making the payment, you can apply for the certificate.

## SSL certificate configuration table {#section_e3v_wvp_yfb .section}

SSL certificate has three categories by review level:

-   OV SSL
-   EV SSL

According to quantity demand of protected domain, SSL certificate is classified into:

-   One domain name: One SSL certificate protects one domain, such as www.abc.com or login.abc.com.
-   Multiple domain names: One SSL certificate protects multiple domain names, such as protect www.abc.com, www.bcd.com and pay.efg.com at the same time.

|Certificate brand|Certificate type|Domain name type|Description|
|-----------------|----------------|----------------|-----------|
|GeoTrust|Professional OV SSL| -   One domain name with wildcards
-   One detailed domain name
-   Multiple detailed domain names

 |Provides encryption, strict identity verification for applicants, and credibility of trusted identity. The maximum number of domain names is 300. For example, the detailed subdomain names buy1.example.com, buy2.example.com, and next.buy.example2.com are counted as three domain names.

 |
|Advanced EV SSL| -   One domain name
-   Multiple domain names

 |Provides encryption, strictest identity verification for applicants, and the highest credibility of trusted identity, and enables the green address bar for the browser.|
|GlobalSign|Professional OV SSL|Wildcard domain name|Provides encryption, strict identity verification for applicants, and credibility of trusted identity.|
|CFCA|Professional OV SSL| -   Wildcard domain name
-   One domain name
-   Multiple domain names

 |Provides encryption, strict identity verification for applicants, and credibility of trusted identity.|
|Advanced EV SSL| |Provides encryption, strictest identity verification for applicants, and the highest credibility of trusted identity, and enables the green address bar for the browser.|
|Symantec|Professional OV SSL| -   Wildcard domain name
-   One domain name
-   Multiple domain names

 |Provides encryption, strict identity verification for applicants, and credibility of trusted identity.|
|Wildcard DV SSL|Wildcard domain name| |
|Enhanced OV SSL| -   One domain name
-   Multiple domain names

 |Provides website encryption, verifies organization registration information, and lists the organization name. After the organization information is validated, the certificate will be issued within three work days.|
|Advanced EV SSL| -   One domain name
-   Multiple domain names

 |Provides encryption, strictest identity verification for applicants, and the highest credibility of trusted identity, and enables the green address bar for the browser.|
|Enhanced EV SSL| -   One domain name
-   Multiple domain names

 |Provides website encryption and enables the green address bar for the browser to demonstrate enhanced trust in the organization information. After the organization information is validated, the certificate will be issued within seven work days.|
|Free DV SSL|One domain name|Provides free root certificate updates, integrates with the DigiCert PKI system, and is compatible with operating systems iOS 5.0 or later, Android 2.3.3 or later, JRE 1.6.5 or later, and Windows 7 or later. It can protect at most one detailed subdomain name and does not support wildcards. Up to 20 free certificates can be issued for each Alibaba Cloud account.|

