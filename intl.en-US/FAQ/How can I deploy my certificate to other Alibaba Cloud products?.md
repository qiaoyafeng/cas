# How can I deploy my certificate to other Alibaba Cloud products? {#concept_lkz_rt5_ydb .concept}

## Push to other Alibaba Cloud products {#section_n4h_st5_ydb .section}

You can use the Push function to push an issued certificate to other Alibaba Cloud products with one-click deployment.

Currently, supported Alibaba Cloud products include CDN, Web Application Firewall, Anti-DDoS Pro IP, and Server Load Balancer.

If any problems occur when attempting to push a certificate, see [FAQs for pushing certificates to cloud products](intl.en-US/FAQ/FAQ about pushing certificates to cloud products.md#).

**Note:** Before pushing a certificate to other Alibaba Cloud products, verify that those products have been purchased for the intended account and that corresponding cloud product services have been activated for the domains added to the certificate. Otherwise, the push function may not work.

## Download and configure the certificate to other products {#section_q4h_st5_ydb .section}

Follow these steps to first download the certificate locally, and then to deploy your digital certificate to other products:

1.  Log on to the [Alibaba Cloud Certificates Service console](https://yundun.console.aliyun.com/?p=cas#/)[Alibaba Cloud Certificates Service console](https://partners-intl.console.aliyun.com/#/cas).
2.  In the My Certificates list, select the issued certificate and click **Download**.
3.  Select **Nginx/Tengine**, and click **Download certificate for Nginx** to download the certificate in PEM format.
4.  Once the certificate is successfully downloaded, you must upload and configure the certificate in the console of the corresponding cloud product.

