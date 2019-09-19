# Deploy SSL certificates to Alibaba Cloud Products {#concept_akc_gkp_ydb .concept}

Verified and issued SSL certificates can be deployed to Alibaba Cloud products, such as CDN, SCDN, DCDN, and SLB services. This helps you improve your data access security when using Alibaba Cloud products.

## Procedure {#section_qhd_whg_5gb .section}

1.  Locate the target certificate on the **Issued** tab page, and then click **Deploy to Products** for the certificate.
2.  Select an Alibaba Cloud product from the drop-down list.
3.  In the right-side **Deploy Certificate to CDN/SLB** page, select the region where you want to deploy the certificate.

    **Note:** You need to select a region when deploying a certificate to SLB. The domain name bound to CDN must be the same as that bound to the certificate.

4.  Click **OK** to deploy the certificate to the cloud product.

If you set the CSR generation method to automatic when you apply for a digital certificate, your private keys are automatically saved by the system. If the CSR generation method is set to manual, you must upload your private keys so that you can deploy the certificate to Alibaba Cloud products.

**Note:** Private keys are in accordance with the certificates. Make sure that your uploaded private key files are correct. For more information about private keys, see [What is a public key and a private key](../../../../reseller.en-US/FAQ/SSL certificate concepts/What is a public key and a private key?.md#).

**Note:** You are not allowed to download the private key that you uploaded. Keep your original private key files safe.

