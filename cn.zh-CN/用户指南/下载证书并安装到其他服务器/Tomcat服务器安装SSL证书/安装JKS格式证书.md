# 安装JKS格式证书 {#concept_m3d_h15_zfb .concept}

您可以将下载的证书安装到Tomcat服务器上。Tomcat支持PFX格式和JKS两种格式的证书，您可根据选您Tomcat的版本择其中一种格式的证书安装到Tomcat上。

## 背景信息 {#section_fk5_oy7_l27 .section}

-   本文档证书名称以**domain name**为示例，如证书文件名称为**domain name.pfx**，证书密码文件名称为**pfx-password.txt**。
-   申请证书时如果未选择**系统自动创建CSR**，证书下载压缩包中将不包含.txt文件。需要您选择**其他类型服务器**下载.crt证书，并使用openssl命令生成pfx文件。

## 操作指南 {#section_ygk_xhx_yfb .section}

1.  登录阿里云[SSL证书控制台](https://yundunnext.console.aliyun.com/?spm=5176.2020520001.aliyun_sidebar.108.356a4bd3MLXFkb&p=cas#/overview/cn-hangzhou)。
2.  在SSL证书页面，点击**已签发**标签，定位到需要下载的证书并单击证书卡片右下角的**下载**打开**证书下载**对话框。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/66242/156276406933499_zh-CN.png)

3.  在**证书下载**对话框中定位到Tomcat服务器，并单击右侧**操作**栏的**下载**将Tomcat版证书压缩包下载到本地。
4.  解压Tomcat证书。您将看到文件中有一个证书文件（以.pfx为后缀或文件类型）和一个密码文件（以.txt为后缀或文件类型）。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/65316/156276407033514_zh-CN.png)

    **说明：** 每次下载证书都会产生新的密码，该密码仅匹配本次下载的证书。如果需要更新证书文件，同时也要更新匹配的密码文件。

5.  输入以下JAVA JDK命令将PFX格式的证书转换成JKS格式。

    ``` {#codeblock_miy_2v1_fbu}
    keytool -importkeystore -srckeystore domain name.pfx -destkeystore domain name.jks -srcstoretype PKCS12 -deststoretype JKS
    ```

    **说明：** Windows系统中，需在`%JAVA_HOME%/jdk/bin`目录下执行该命令。

6.  回车后输入PFX证书密码和JKS证书密码。

    **说明：** JKS证书密码等同于PFX证书密码。两个密码不同的时候会导致Tomcat重启失败。

7.  在**Tomcat**安装目录下新建**cert**目录，将证书和密码文件拷贝到**cert**目录下。
8.  打开**Tomcat安装目录** \> **conf文件夹** \> **server.xml文件**，在**server.xml文件**中找到 `<Connector port=”8443”`标签并进行修改。

    ``` {#codeblock_ny0_sfx_c0z}
    <!--
      <Connector port="8443"
    protocol="HTTP/1.1"
    port="8443" SSLEnabled="true"
      maxThreads="150" scheme="https" secure="true"
      clientAuth="false" sslProtocol="TLS" />
    
    -->
    ```

    参考以下完整配置（其中port属性请根据您的实际情况修改）：

    ``` {#codeblock_9gt_rkj_fwq}
    <Connector port="443"
        protocol="HTTP/1.1"
        SSLEnabled="true"
        scheme="https"
        secure="true"
        keystoreFile="cert/domain name.jks"  #此处keystoreFile代表证书文件的路径，请用您证书的文件名替换domain name。
        keystoreType="PKCS12"
        keystorePass="证书密码"   #请用您证书密码文件中的密码替换“证书密码”。
        clientAuth="false"
        SSLProtocol="TLSv1+TLSv1.1+TLSv1.2"
        ciphers="TLS_RSA_WITH_AES_128_CBC_SHA,TLS_RSA_WITH_AES_256_CBC_SHA,TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA,TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256,TLS_RSA_WITH_AES_128_CBC_SHA256,TLS_RSA_WITH_AES_256_CBC_SHA256"/>
    ```

9.  保存server.xml文件配置。
10. （可选步骤）配置web.xml文件开启HTTP强制跳转HTTPS。

    ``` {#codeblock_xwj_4ym_oa3}
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

11. 重启Tomcat。

## 后续操作 { .section}

证书安装完成后，可通过登录证书绑定域名的方式验证证书是否安装成功。

``` {#d7e190}
https://domain name:port   #domain name替换成证书绑定的域名
```

如果网页地址栏出现绿色小锁标志，表示证书安装成功。

验证证书是否安装成功时，如果网站无法通过https正常访问，需确认您安装证书的服务器443端口是否已开启或被其他工具拦截。

