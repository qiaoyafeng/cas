# New purchase upon expiration {#concept_bty_rfp_ydb .concept}

The validity period of an Alibaba Cloud SSL certificate is one or two years, depending on the type of the certificate. Once your SSL certificate expires, you need to purchase a new one.

## Payment {#section_nsc_vfp_ydb .section}

Post-payment is not accepted. You must pay first to activate the service.

To request a fee-based certificate, you must select the certificate type, the number of domain names, and the certificate brand. Then, you must pay for the certificate, enter the details for the certificate, and submit it for review. If your account balance is insufficient to cover the cost of the certificate, the follow-up operations will fail, and you will be unable to use Alibaba Cloud SSL Certificates Service.

## New purchase upon expiration {#section_osc_vfp_ydb .section}

SSL certificates cannot be renewed, and can only be purchased. Before your certificate expires, you need to log on to the Alibaba Cloud [SSL Certificates console](https://yundunnext.console.aliyun.com/?p=casnext#/overview/cn-hangzhou) to purchase and apply for a new certificate.

**Note:** Purchase the replacement certificate three to ten working days before certificate expiration so that the new certificate can be reviewed before the existing certificate expires.

**Note:** You need to re-bind the domain name for the new certificate.

## Procedure {#section_nqq_pdv_vgb .section}

1.  Log on to the [Alibaba Cloud SSL Certificates console](https://yundunnext.console.aliyun.com/?p=cas#/overview).
2.  Click **Purchase Certificate** in the upper-right corner to go to the certificate purchase page.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13562/155620414339080_en-US.png)

3.  Select the parameter values and complete payment.

    **Note:** If the brand and domain type of the new certificate are exactly the same as the previous certificate, the system automatically synchronizes the application information and review materials that were submitted previously. This will not shorten the duration of the review process.

4.  Apply for an SSL certificate and re-bind the domain name.
5.  Submit the material for review.
6.  Install the newly purchased certificate on your server to replace the certificate that is about to expire.

    **Note:** If you do not install the new certificate on your server, the HTTPS will become unavailable once the previous certificate expires.


