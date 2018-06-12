# Step 1: Select a certificate {#concept_um3_fkp_ydb .concept}

1.  Go to the [Alibaba Cloud Certificates Service purchase page](https://common-buy-intl.aliyun.com/?commodityCode=cas_intl#/buy).

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13566/4188_en-US.png)

2.  Select the digital certificate and make the payment to enter the certificate configuration process.

## Certificate type {#section_psf_vmp_ydb .section}

In conjunction with qualified Certificate Authorities \(CAs\), Alibaba Cloud provides the following options to configure your digital certificates:

-   **SSL Professional**: A type of OV SSL \(Organization Validation SSL\) certificate. Details of an SSL Professional certificate include: SSL \).
    -   The CA verifies domain ownership and organization identity.
    -   The requester’s business name is displayed in the certificate.
    -   The certificate provides strong encryption for communication links.
    -   The certificate supports up to 100 domains.
-   **SSL Advanced**: A type of EV SSL \(Extended Validation SSL\) certificate. Details of an SSL Advanced certificate include:
    -   The CA strictly verifies domain ownership and organization identity.
    -   A green address bar is displayed for this certificate in most browsers \(the Safari browser has some exceptions\).
    -   The requester’s organization identity details are displayed in the certificate.
    -   The certificate provides strong encryption for communication links.
    -   The certificate supports up to 100 domains.

## Certificate brand \(CA provider\) {#section_vsf_vmp_ydb .section}

Alibaba Cloud works with the following CA to issue digital certificates:

**Entrust**: Entrust is the world’s leading public key infrastructure provider. It has built a trusted virtual environment that facilitates communication, around the world. Entrust offers trust services to websites, software developers, and individual entrepreneurs, including the issuance of SSL server certificate, in more than 60 countries.

## Domain protection {#section_xsf_vmp_ydb .section}

Before purchasing a digital certificate, you must determine the type and number of domains you want to secure with the certificate. You can secure single or multiple domains, or wildcard domains.

-   Single domain: Your digital certificate can only protect one domain \(for example, buy.example.com\) and does not support wildcards.
-   Multiple domains: Your digital certificate can protect multiple domains \(for example, buy1.example.com and buy2.example.com\) though the maximum number of domains varies according to the certificate type. Generally, up to 100 domains can be secured. You can select on the basis of the **Number of domains** option, however, the wildcard domains are not supported.
-   Wildcard domains: Your digital certificate can protect an extensive domain with a wildcard. Certificates for securing multiple wildcard subdomains are currently unavailable. For example, with the wildcard domain, \*.example.com, you can protect domains such as a1.example.com and a2.example.com, but not a1.sport.example.com or a2.thanks.example.com.

**Note:** Alibaba Cloud verifies the number and type of domains you select when you enter the domain information. If you select to protect multiple domains, you must submit all selected domains at the same time.

## Certificate validity period {#section_zsf_vmp_ydb .section}

Every digital certificate has a validity period.

-   The maximum validity period of SSL Professional certificates is three years.
-   The maximum validity period of SSL Advanced certificates is two years.

