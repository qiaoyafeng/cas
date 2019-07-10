# 安装PFX格式证书 {#concept_omf_lxn_yfb .concept}

您可以将下载的证书安装到Tomcat服务器上。Tomcat支持PFX格式和JKS两种格式的证书，您可根据您Tomcat的版本择其中一种格式的证书安装到Tomcat上。

## 背景信息 {#section_lyv_472_xzw .section}

-   本文教程以Tomcat 7为例。
-   Tomcat 9强制要求证书别名设置为tomcat。您需要使用以下keytool命令将`protocol="HTTP/1.1"`转换成`protocol="org.apache.coyote.http11.Http11NioProtocol"`。

    ``` {#codeblock_vme_lr0_kv2}
    keytool -changealias -keystore domain name.pfx -alias alias -destalias tomcat
    ```

-   本文档证书名称以**domain name**为示例，如证书文件名称为**domain name.pfx**，证书密码文件名称为**pfx-password.txt**。
-   申请证书时如果未选择**系统自动创建CSR**，证书下载压缩包中将不包含.txt文件。需要您选择**其他类型服务器**下载.crt证书，并使用openssl命令生成pfx文件。

## 操作指南 {#section_ygk_xhx_yfb .section}

1.  登录阿里云[SSL证书控制台](https://yundunnext.console.aliyun.com/?spm=5176.2020520001.aliyun_sidebar.108.356a4bd3MLXFkb&p=cas#/overview/cn-hangzhou)。
2.  在SSL证书页面，点击**已签发**标签，定位到需要下载的证书并单击证书卡片右下角的**下载**打开**证书下载**对话框。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65316/156276398939265_zh-CN.jpg)

3.  在**证书下载**对话框中定位到Tomcat服务器，并单击右侧**操作**栏的**下载**将Tomcat版证书压缩包下载到本地。
4.  解压Tomcat证书。

    您将看到文件夹中有2个文件：

    -   证书文件（以.pfx为后缀或文件类型）
    -   密码文件（以.txt为后缀或文件类型）
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65316/156276398933514_zh-CN.png)

    **说明：** 每次下载证书都会产生新的密码，该密码仅匹配本次下载的证书。如果需要更新证书文件，同时也要更新匹配的密码。

5.  在**Tomcat**安装目录下新建**cert**目录，将下载的证书和密码文件拷贝到**cert**目录下。
6.  打开**Tomcat** \> **conf** \> **server.xml文件**，在**server.xml文件**中添加以下属性（其中port属性请根据您的实际情况修改）：

    ``` {#codeblock_n5m_6q3_oa6}
    <!--
      <Connector  port="8443"
    protocol="HTTP/1.1"
      port="8443" SSLEnabled="true"
      maxThreads="150" scheme="https" secure="true"
      clientAuth="false" sslProtocol="TLS" />
    -->
    ```

    ``` {#codeblock_vxr_ezk_s8m}
    <Connector port="443"
        protocol="HTTP/1.1"
        SSLEnabled="true"
        scheme="https"
        secure="true"
        keystoreFile="domain name.pfx"   #此处keystoreFile代表证书文件的路径，请用您证书的文件名替换domain name。
        keystoreType="PKCS12"
        keystorePass="证书密码"   #请用您证书密码替换文件中的内容。
        clientAuth="false"
        SSLProtocol="TLSv1+TLSv1.1+TLSv1.2"
        ciphers="TLS_RSA_WITH_AES_128_CBC_SHA,TLS_RSA_WITH_AES_256_CBC_SHA,TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA,TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256,TLS_RSA_WITH_AES_128_CBC_SHA256,TLS_RSA_WITH_AES_256_CBC_SHA256"/>
    ```

    **说明：** 其中port属性根据实际情况修改（https默认端口为443）。如果使用其他端口号，则您需要使用https://yourdomain:port的方式来访问您的网站。

7.  保存server.xml文件配置。
8.  （可选步骤）配置web.xml文件开启HTTP强制跳转HTTPS。

    ``` {#codeblock_3ux_sgp_8ay}
    #在</welcome-file-list>后添加以下内容：
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

9.  重启Tomcat。

## 后续操作 {#section_630_vdz_11w .section}

证书安装完成后，可通过登录证书绑定域名的方式验证证书是否安装成功。

``` {#codeblock_erk_43t_uzs}
https://domain name:port   #domain name替换成证书绑定的域名
```

如果网页地址栏出现绿色小锁标志，表示证书安装成功。

验证证书是否安装成功时，如果网站无法通过https正常访问，需确认您安装证书的服务器443端口是否已开启或被其他工具拦截。

## 相关文档 {#section_2lq_zzj_qza .section}

-   [在Tomcat服务器上安装SSL证书](intl.zh-CN/用户指南/下载证书并安装到其他服务器/Tomcat服务器安装SSL证书/安装PFX格式证书.md#)
-   [Ubuntu系统Apache 2部署SSL证书](../../../../intl.zh-CN/最佳实践/Ubuntu系统Apache 2部署SSL证书.md#)
-   [我获取到的数字证书如何配置在自己的Apache中？](../../../../intl.zh-CN/常见问题/常见问题/我获取到的数字证书如何配置在自己的Apache中？.md#)
-   [在Nginx/Tengine服务器上安装证书](intl.zh-CN/用户指南/下载证书并安装到其他服务器/在Nginx__Tengine服务器上安装证书.md#)
-   [在IIS服务器上安装证书](intl.zh-CN/用户指南/下载证书并安装到其他服务器/在IIS服务器上安装证书.md#)
-   [CentOS系统Tomcat 8.5/9部署SSL证书](../../../../intl.zh-CN/最佳实践/CentOS系统Tomcat 8.5__9部署SSL证书.md#)
-   [Jetty服务器配置SSL证书](../../../../intl.zh-CN/常见问题/常见问题/Jetty服务器配置SSL证书.md#)

