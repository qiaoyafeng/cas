# How do I deploy the issued certificate in Apache server {#concept_ccz_hcv_ydb .concept}

You can deploy certificates from Alibaba Cloud Certificates Service to various web service servers using the method as you may, for other certificates. However, if the certificate contains a certificate chain, it must be deployed in the Apache server using the following steps.

## Step 1: Check whether your digital certificate contains a certificate chain {#section_y4j_3cv_ydb .section}

Use a text editor tool to open your certificate file \(for example, mycert.pem\) and check whether the certificate contains a certificate chain. If you see three `BEGIN  CERTIFICATE` segments in the certificate file, they indicate that your certificate file contains a certificate chain.

**Note:** If you certificate file does not contain a certificate chain, skip the following steps in this document. Deploy your certificate directly on the Apache server.

```

-----BEGIN CERTIFICATE-----
xxxxxx...
-----END CERTIFICATE-----


-----BEGIN CERTIFICATE-----
xxxxxx...
-----END CERTIFICATE-----

-----BEGIN CERTIFICATE-----
xxxxxx...
-----END CERTIFICATE-----
```

## Step 2: Extract certificate chain {#section_epj_3cv_ydb .section}

To extract a certificate chain from your certificate file, open the certificate file and copy the last two segments of certificate information \(namely, the last two `-----BEGIN CERTIFICATE-----` segments\) to a separate text file, and save that text file as mycert\_chain.pem.

## Step 3: Rename file {#section_fpj_3cv_ydb .section}

Rename the original certificate file to mycert.pem. You now have two PEM files, the original certificate file mycert.pem and the certificate chain file mycert\_chain.pem.

## Step 4: Deploy certificate in Apache server {#section_gpj_3cv_ydb .section}

Perform the following configuration in the Apache configuration file.

```

...
SSLEngine On 
SSLCertificateFile conf/ssl.crt/mycert.pem 
SSLCertificateKeyFile conf/ssl.key/mycert.key 
SSLCertificateChainFile conf/ssl.crt/mycert_chain.pem 
...
```

