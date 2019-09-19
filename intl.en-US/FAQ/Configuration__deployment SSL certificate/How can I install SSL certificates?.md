# How can I install SSL certificates? {#concept_95505_zh .concept}

In the Alibaba Cloud Certificates console, you can download and install SSL certificates of the NGINX , Apache , Tomcat , IIS , or other type and install them on corresponding servers.

You can extract the following files from different types of certificate packages:

-   The .key file is a private key file, which is not available if you did not select Automatic for CSR Generation when applying for SSL certificates. Save the private key file.
-   The .crt file is a certificate file. It usually contains two parts. On an Apache server, the certificate file is divided into the \_public.crt \(certificate\) file and the \_chain.crt \(certificate chain or intermediate certificate\) file.
-   The .pem file is a certificate file. It usually contains two parts. The NGINX certificate uses the extension file, which is the same as the .crt file in the Alibaba Cloud SSL certificate.

    **Note:** The **.crt** certificate file is a Base64-encoded text file and you can modify its extension to .pem as needed.

-   The .pfx file is applicable to the Tomcat and IIS servers. Each time the certificate is downloaded, a new password is generated, which is valid only for the current certificate. To update the certificate file, you need to update the password.

**Note:** If certificates are used for Alibaba Cloud services, we recommend that you download certificates for Nginx.

## Install SSL certificates on common servers {#section_898_ju5_c1t .section}

-   [Install SSL certificates in Tomcat servers](../../../../reseller.en-US/User Guide/Download and install SSL certificates/Install SSL certificates in Tomcat servers/Install .pfx SSL certificates.md#)
-   [How do I deploy the issued certificate in Apache server](reseller.en-US/FAQ/Configuration__deployment SSL certificate/How do I deploy the issued certificate in Apache server.md#)
-   [Deploy SSL certificate on Ubuntu Apache2](../../../../reseller.en-US/Best Practices/Deploy SSL certificate on Ubuntu Apache2.md#)
-   [How do I deploy the issued certificate in Apache server](reseller.en-US/FAQ/Configuration__deployment SSL certificate/How do I deploy the issued certificate in Apache server.md#)
-   [Install SSL certificates in Nginx/Tengine servers](../../../../reseller.en-US/User Guide/Download and install SSL certificates/Install SSL certificates in Nginx__Tengine servers.md#)
-   [Install SSL certificates in IIS servers](../../../../reseller.en-US/User Guide/Download and install SSL certificates/Install SSL certificates in IIS servers.md#)
-   [Deploy SSL certificates on Tomcat 8.5 or Tomcat 9.0 running CentOS](../../../../reseller.en-US/Best Practices/Deploy SSL certificates on Tomcat 8.5 or Tomcat 9.0 running CentOS.md#)
-   [An SSL certificate is configured by the jetty server](reseller.en-US/FAQ/Configuration__deployment SSL certificate/An SSL certificate is configured by the jetty server.md#)

