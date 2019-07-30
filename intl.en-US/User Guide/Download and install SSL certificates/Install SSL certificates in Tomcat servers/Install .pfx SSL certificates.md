# Install .pfx SSL certificates {#concept_omf_lxn_yfb .concept}

This topic describes how to install the downloaded SSL certificate in your Tomcat server. Tomcat supports both .pfx and .jks certificates. You can install a .pfx or .jks certificate based on your Tomcat version.

## Prerequisites {#section_csz_fkx_yfb .section}

You selected **Automatic** for CSR Generation when applying for the certificate.

If you selected **Manual** for CSR Generation when applying for the certificate, no certificate file is generated. You have to download the .crt certificate whose Server Type is **Other**, and then run the OpenSSL command to convert the certificate to .pfx format.

In this example, the certificate name is **domain name**, and the certificate file is named **domain name.pfx**.

## Procedure {#section_ygk_xhx_yfb .section}

1.  Log on to the Alibaba Cloud SSL Certificates console.
2.  On the **SSL Certificates** page, locate the target SSL certificate and click **Download** in the lower-right corner.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/66242/156447348933499_en-US.png)

3.  In the **Download Certificate** dialog box, locate the row that contains the certificate whose Server Type is Tomcat, and click **Download** in the **Actions** column to download the package to your local host.
4.  Decompress the package.

    The following two files are extracted:

    -   Certificate file \(suffixed with .pfx or of .pfx file format\)
    -   Key file \(suffixed with .txt or of .txt file format\)
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65316/156447348933514_en-US.png)

    **Note:** Each time the certificate is downloaded, a new password is generated, which is valid only for the current certificate. To update the certificate file, you also need to update the matching key file.

5.  In the **Tomcat** directory, create **cert** directory. Copy the downloaded certificate and password file to the **cert** directory.
6.  Open **Tomcat installation directory** \> **conf** \> **server.xml**. In the **server.xml** file, add the following attributes \(you can modify the port attribute as needed\):

    ```
    <Connector port="8443"
        protocol="HTTP/1.1"
        SSLEnabled="true"
        scheme="https"
        secure="true"
        keystoreFile="domain name.pfx"   #keystoreFile indicates the path of your certificate file. Replace domain name with the name of your certificate file.
        keystoreType="PKCS12"
        keystorePass="Certificate password"   #Replace the certificate password with the content in your key file.
        clientAuth="false"
        SSLProtocol="TLSv1+TLSv1.1+TLSv1.2"
        ciphers="TLS_RSA_WITH_AES_128_CBC_SHA,TLS_RSA_WITH_AES_256_CBC_SHA,TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA,TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256,TLS_RSA_WITH_AES_128_CBC_SHA256,TLS_RSA_WITH_AES_256_CBC_SHA256"/>
    ```

7.  Save the configuration in the server.xml file.
8.  （optional）Configure web.xml file to force HTTP jump to HTTPS.

    ```
    #All the following content behind </welcome-file-list>：
    <login-config>  
        <!-- Authorization setting for SSL -->  
        <auth-method>CLIENT-CERT</auth-method>  
        <realm-name>Client Cert Users-only Area</realm-name>  
    </login-config>  
    <security-constraint>  
        <!-- Authorization setting for SSL -->  
        <web-resource-collection >  
            <web-resource-name >SSL</web-resource-name>  
            <url-pattern>/*</url-pattern>  
        </web-resource-collection>  
        <user-data-constraint>  
            <transport-guarantee>CONFIDENTIAL</transport-guarantee>  
        </user-data-constraint>  
    </security-constraint>
    ```

9.  Restart Tomcat.

References:

-   [Install SSL certificates in Apache servers](reseller.en-US/User Guide/Download and install SSL certificates/Install SSL certificates in Apache servers.md#)
-   [Deploy SSL certificate on Ubuntu Apache2](../../../../reseller.en-US/Best Practices/Deploy SSL certificate on Ubuntu Apache2.md#)
-   [How do I deploy the issued certificate in Apache server](../../../../reseller.en-US/FAQ/FAQ/How do I deploy the issued certificate in Apache server.md#)
-   [Install SSL certificates in Nginx/Tengine servers](reseller.en-US/User Guide/Download and install SSL certificates/Install SSL certificates in Nginx__Tengine servers.md#)
-   [Install SSL certificates in IIS servers](reseller.en-US/User Guide/Download and install SSL certificates/Install SSL certificates in IIS servers.md#)
-   [Deploy SSL certificates on Tomcat 8.5 or Tomcat 9.0 running CentOS](../../../../reseller.en-US/Best Practices/Deploy SSL certificates on Tomcat 8.5 or Tomcat 9.0 running CentOS.md#)
-   [An SSL certificate is configured by the jetty server](../../../../reseller.en-US/FAQ/FAQ/An SSL certificate is configured by the jetty server.md#)

