# Deploy SSL certificates on Tomcat 8.5 or Tomcat 9.0 running CentOS {#concept_i2b_cdb_mgb .concept}

This topic describes how to deploy SSL certificates on Tomcat 8.5 or Tomcat 9.0 running CentOS.

## Test environment {#section_m3b_x3j_kgb .section}

Operating system: CentOS 7.6, 64-bit

Web server: Tomcat 8.5 or Tomcat 9.0

**Note:** JDK environment variables must be installed on the Tomcat server first. You can view the recommended JDK compatible configuration on the Tomcat official website.

## Prerequisites {#section_dp2_hk2_kgb .section}

-   You have downloaded the Tomcat server certificate from the Alibaba Cloud SSL Certificates console. The Tomcat server certificate includes the PFX format certificate file and TXT format password file.
-   You have added DNS records for the domain name that is bound to your SSL certificate, pointing the domain name to the IP address of the Tomcat server.

    Run the ping www.yourdomain.com command after the domain name resolution is configured. If the IP address of the Tomcat server is returned, the resolution is successful.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/105838/156447326038731_en-US.png)


## Procedure {#section_b2p_3k2_kgb .section}

1.  Decompress the Tomcat server certificate.

    **Note:** A new password file is generated each time you download the certificate. The password is valid only for the downloaded certificate. If you want to update the certificate, you must update the password at the same time.

2.  Create the **cert** directory under the **Tomcat** installation directory and copy the downloaded certificate and password files to the **cert** directory.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/105838/156447326138747_en-US.png)

3.  Open Tomcat/conf/server.xml, locate the following parameters in the server.xml file, and modify these parameters.

    ``` {#codeblock_qgn_szz_08o}
    <Connector port="8080" protocol="HTTP/1.1"
                   connectionTimeout="20000"
                   redirectPort="8443" />
    
     #Locate the preceding parameters, remove the <! - - and - -> annotation symbols, and modify the parameters as follows:
     <Connector port="80" protocol="HTTP/1.1"
     #Set Connector port to 80.
                   connectionTimeout="20000"
                   redirectPort="443" />   
                   #Set redirectPort to the SSL default port 443 to redirect HTTP requests to HTTPS requests.
    ```

    ``` {#codeblock_h39_8i9_5ba}
    
    
        <Connector port="8443"
              protocol="org.apache.coyote.http11.Http11NioProtocol"
              maxThreads="150"
              SSLEnabled="true">
            <SSLHostConfig>
                <Certificate       certificateKeystoreFile="cert/keystore.pfx"
                 certificateKeystorePassword="XXXXXXX"
                             certificateKeystoreType="PKCS12" />
    
        #Locate the preceding parameters, remove the <! - - and - -> annotation symbols, and modify the parameters as follows:
        <Connector port="443"
        #Change the default Tomcat HTTPS port Connector port from 8443 to 443. Port 8443 cannot be directly accessed through the domain name. Therefore, you must append a port number to the domain name. Port 443 is the default HTTPS port. You can directly access it through the domain name without the need to append a port number to the domain name.
              protocol="org.apache.coyote.http11.Http11NioProtocol"
              #Connector port in file server.xml has two modes: NIO and APR. In this deployment, the NIO mode is used. The protocol="org.apache.coyote.http11.Http11NioProtocol" setting specifies the NIO mode.
              maxThreads="150"
              SSLEnabled="true">
            <SSLHostConfig>
                <Certificate       certificateKeystoreFile="/usr/local/tomcat/cert/Certificate Domain Name.pfx"
                 #The certificateKeystoreFile parameter specifies the path of the certificate file. Use your certificate path and file name to replace Certificate Domain Name.pfx, for example, certificateKeystoreFile="/usr/local/tomcat/cert/abc.com.pfx".
                 certificateKeystorePassword="password"
                 #The certificateKeystorePassword parameter specifies the password for the SSL certificate. Use your certificate password in pfx-password.txt to replace it, for example, certificateKeystorePassword="bMNML1Df".
                 certificateKeystoreType="PKCS12" />
                 #When the certificate type is PFX, set certificateKeystoreType to PKCS12.
    					
    ```

    ``` {#codeblock_ik4_cyy_xu9}
    <Connector port="8009" protocol="AJP/1.3" redirectPort="8443" />
    
    #Locate the preceding parameters, remove the <! - - and - -> annotation symbols, and modify the parameters as follows:
    <Connector port="8009" protocol="AJP/1.3" redirectPort="443" />
     #Set redirectPort to 443 to redirect HTTP requests to HTTPS requests.
    ```

4.  Save the configuration in the server.xml file.
5.  Restart the Tomcat service.
    1.  Run ./shutdown.sh in the bin directory of Tomcat to disable the Tomcat service.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/105838/156447326138751_en-US.png)

    2.  Run ./startup.sh in the bin directory of Tomcat to enable the Tomcat service.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/105838/156447326138752_en-US.png)


## Subsequent procedures {#section_e3j_jk2_kgb .section}

After the Tomcat service restarts, enter domain name https://www.YourDomainName.com into the address bar of your browser, and verify the certificate deployment result. If the green lock icon appears in the address bar of your browser, the certificate is installed.

See also:

-   [Deploy SSL certificates on Tomcat servers](../../../../intl.en-US/User Guide/Download and install SSL certificates/Install SSL certificates in Tomcat servers/Install .pfx SSL certificates.md#)
-   [Install SSL certificates in Apache servers](../../../../intl.en-US/User Guide/Download and install SSL certificates/Install SSL certificates in Apache servers.md#)
-   [Deploy SSL certificate on Ubuntu Apache2](intl.en-US/Best Practices/Deploy SSL certificate on Ubuntu Apache2.md#)
-   [How do I deploy the issued certificate in Apache server](../../../../intl.en-US/FAQ/FAQ/How do I deploy the issued certificate in Apache server.md#)
-   [Install SSL certificates in Nginx/Tengine servers](../../../../intl.en-US/User Guide/Download and install SSL certificates/Install SSL certificates in Nginx__Tengine servers.md#)
-   [Install SSL certificates in IIS servers](../../../../intl.en-US/User Guide/Download and install SSL certificates/Install SSL certificates in IIS servers.md#)
-   [An SSL certificate is configured by the jetty server](../../../../intl.en-US/FAQ/FAQ/An SSL certificate is configured by the jetty server.md#)

