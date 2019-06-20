# FAQ about pushing certificates to cloud products {#concept_x2f_spp_ydb .concept}

Digital certificates purchased from Alibaba Cloud Certificates Service can be pushed to Alibaba Cloud products like Web Application Firewall \(WAF\), Anti-DDoS Pro, CDN, and Server Load Balancer with a single click.

Do not push your certificate to any products or services that you have not purchased. Because these products or services cannot recognize the domain name associated with your certificate. The push process may fail.

**Note:** But, Server Load Balance is an exception to this restriction. The push process can be successful even if the service is not enabled.

## When a certificate has been successfully pushed to a cloud product, does that mean the HTTPS service works properly for the cloud product? {#section_ryq_spp_ydb .section}

No. You still need to configure some parameters in the cloud product console. Additionally, make sure that your origin server is appropriately prepared for HTTPS support.

For the required parameter settings for each cloud product, see the corresponding configuration documents.

## Why I do not find my domains when pushing the certificates to CDN? {#section_syq_spp_ydb .section}

When pushing a digital certificate to CDN, the certificate service first checks if the domains available in CDN match those in the certificate. One reason for the failure is that you have not configured or enabled the domains associated with the certificate in the CDN console. 

Go to the CDN console to add the domains associated with your certificate, and then enable them.

**Note:** The certificate service can only find appropriately working domains when querying the domain list in the CDN console.

## When a digital certificate is pushed to Server Load Balance, to which regions is it pushed? {#section_vyq_spp_ydb .section}

The certificate service pushes a copy of the certificate to all regions. Canceling the push removes the pushed copies from the respective regions.

After the certificate is pushed to Server Load Balance in various regions, select your Server Load Balance instance from the **Server Load Balancer console** \> **Instance Management**and then click **Manage**. On the Listener page, click **Add Listener**, and then configure the listener details with the certificate selected.

**Note:** Make sure that the selected certificate and the added domains are matched.

