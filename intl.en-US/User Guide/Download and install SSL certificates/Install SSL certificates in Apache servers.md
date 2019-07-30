# Install SSL certificates in Apache servers {#concept_zsp_d1x_yfb .concept}

This topic describes how to download an SSL certificate from the Alibaba Cloud SSL Certificates console and install it in your Apache server.

## Prerequisites {#section_xdh_4qb_1gb .section}

Select **Automatic** for CSR Generation when applying for the certificate.

In this example, **domain name** is the certificate name, **domain name\_public.cert** is the certificate file name, **domain name\_chain.cert** is the certificate chain file, and **domain name.key** is the certificate ket file.

## Procedure {#section_ydh_4qb_1gb .section}

1.  Log on to[Alibaba Cloud SSL Certificates console](https://yundunnext.console.aliyun.com/?p=casnext#/overview/cn-hangzhou).
2.  On the **SSL Certificates** page, locate the target SSL certificate and click **Download** in the lower-right corner.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/66001/156446700339177_en-US.jpg)

3.  In the **Download Certificate** dialog box, locate the row that contains the certificate whose Server Type is Apache, and click **Download** in the **Actions** column to download the package to your local host.
4.  Decompress the certificate package.

    The following three files are extracted:

    -   Certificate file \(suffixed with .crt or of .crt file format\)
    -   Certificate chain file \(suffixed with .crt or of .crt file format\)
    -   Key file \(suffixed with .key or of .key file format\)
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/66001/156446700433689_en-US.png)

    **Note:** The **.crt** certificate file is a Base64-encoded text file and you can modify its extension to **.pem** as needed.

    For more information about the certificate format, see [What are the formats of mainstream digital certificates?](https://www.alibabacloud.com/help/faq-detail/42214.htm)

5.  Create a /cert directory in the **Apache installation directory**, and copy the downloaded certificate file, certificate chain file, and key file to the /cert directory.

    **Note:** If you have selected **Manual** for CSR Generation when applying for the certificate, save the key file you created manually to the /cert directory.

6.  Open Apache installation directory/conf/httpd.conf. In the httpd.conf file, find the following parameters and configure them:

    ```
    #LoadModule ssl_module modules/mod_ssl.so   
    #Delete the configuration statement annotator "#" at the beginning of the line. If it is not found, check if the OpenSSL plug-in has been compiled.
    #Include conf/extra/httpd-ssl.conf   
    #Delete the configuration statement annotator "#" at the beginning of the line.
    						
    ```

7.  Save the httpd.conf file and exit.
8.  Open Apache installation directory/conf/extra/httpd-ssl.conf. In the httpd-ssl.conf file, find the following parameters and configure them:

    **Note:** Depending on the operating system, the http-ssl.conf file may be stored in the conf.d/ssl.conf directory.

    ```
    
    SSLProtocol all -SSLv2 -SSLv3    
    # Add supported SSL protocols and remove the insecure ones.
    SSLCipherSuite HIGH:! RC4:! MD5:! aNULL:! eNULL:! NULL:! DH:! EDH:! EXP:+MEDIUM    
    # Use this cipher suite.
    SSLHonorCipherOrder on
    SSLCertificateFile cert/domain name_public.crt    
    # Replace domain name_public.crt with the name of your certificate.
    SSLCertificateKeyFile cert/domain name.key    
    # Replace domain name.key with the name of your private key file.
    SSLCertificateChainFile cert/domain name_chain.crt   
    # Delete the annotator "#" (if any) at the beginning of the certificate chain.
    ```

9.  Save the configuration in thehttpd-ssl.conf file.
10. Go to the /bin directory in the Apache installation directory to restart the Apache server.
    1.  In Apache /bin directory, execute the following command to stop Apache server:

        ```
        apachectl -k stop
        ```

    2.  In Apache bin directory, execute the following command to start Apache server:

        ```
        apachectl -k start
        ```


References:

-   [Install SSL certificates in Tomcat servers](intl.en-US/User Guide/Download and install SSL certificates/Install SSL certificates in Tomcat servers/Install .pfx SSL certificates.md#)
-   [Deploy SSL certificate on Ubuntu Apache2](../../../../intl.en-US/Best Practices/Deploy SSL certificate on Ubuntu Apache2.md#)
-   [How do I deploy the issued certificate in Apache server](../../../../intl.en-US/FAQ/FAQ/How do I deploy the issued certificate in Apache server.md#)
-   [Install SSL certificates in Nginx/Tengine servers](intl.en-US/User Guide/Download and install SSL certificates/Install SSL certificates in Nginx__Tengine servers.md#)
-   [Install SSL certificates in IIS servers](intl.en-US/User Guide/Download and install SSL certificates/Install SSL certificates in IIS servers.md#)
-   [Deploy SSL certificates on Tomcat 8.5 or Tomcat 9.0 running CentOS](../../../../intl.en-US/Best Practices/Deploy SSL certificates on Tomcat 8.5 or Tomcat 9.0 running CentOS.md#)
-   [An SSL certificate is configured by the jetty server](../../../../intl.en-US/FAQ/FAQ/An SSL certificate is configured by the jetty server.md#)

