# 在Apache服务器上安装SSL证书 {#concept_zsp_d1x_yfb .concept}

您可以将从阿里云SSL证书控制台下载的证书安装到您的Apache服务器上，使Apache服务器支持 HTTPS安全访问 。

## 前提条件 {#section_xdh_4qb_1gb .section}

-   申请证书时需要选择**系统自动创建CSR**。
-   本文档证书名称以**domain name**为示例，如证书文件名称为**domain name\_public.cert**，证书链文件名称为**domain name\_chain.cert**，证书秘钥文件名称为**domain name.key**。
-   已安装OpenSSL。

## 操作指南 {#section_ydh_4qb_1gb .section}

1.  登录阿里云[SSL证书控制台](https://yundunnext.console.aliyun.com/?spm=5176.2020520001.aliyun_sidebar.108.356a4bd3MLXFkb&p=cas#/overview/cn-hangzhou)。
2.  在SSL证书页面，点击**已签发**标签，定位到需要下载的证书并单击证书卡片右下角的**下载**打开**证书下载**对话框。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/66001/156103388939177_zh-CN.jpg)

3.  在**证书下载**对话框中定位到 Apache服务器 ，并单击右侧**操作**栏的**下载**将Apache版证书压缩包下载到本地。
4.  解压Apache证书。

    您将看到文件夹中有3个文件：

    -   证书文件（以.crt为后缀或文件类型）
    -   证书链文件（以.crt为后缀或文件类型）
    -   秘钥文件（以.key为后缀或文件类型）
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/66001/156103388933689_zh-CN.png)

    **说明：** **.crt**扩展名的证书文件采用 Base64-encoded 的PEM格式文本文件，您可根据需要修改成**.pem**等扩展名。

    证书的格式详见[主流数字证书都有哪些格式](https://www.alibabacloud.com/help/faq-detail/42214.htm)。

5.  在**Apache**安装目录中新建**cert**目录，并将下载的Apache证书、 证书链 和秘钥文件拷贝到**cert**目录中。

    **说明：** 如果申请证书时选择了**手动创建CSR文件**，请将手动生成创建的秘钥文件拷贝到**cert目录**中。

6.  打开Apache/conf/httpd.conf，在httpd.conf文件中找到以下参数并进行配置。

    ``` {#codeblock_vj3_m4j_m4z}
    #LoadModule ssl_module modules/mod_ssl.so   
    #删除行首的配置语句注释符号“#”加载mod_ssl.so模块启用SSL服务，Apache默认是不启用该模块的。如果找不到该配置，请重新编译mod_ssl模块。
    #Include conf/extra/httpd-ssl.conf   删除行首的配置语句注释符号“#”。
    						
    ```

7.  保存httpd.conf文件后退出。
8.  打开Apache/conf/extra/httpd-ssl.conf，在httpd-ssl.conf文件中找到以下参数并进行配置。

    **说明：** 根据操作系统的不同， http-ssl.conf文件也可能存放在conf.d/ssl.conf目录中。

    ``` {#codeblock_pln_6w3_3ng}
    
    SSLProtocol all -SSLv2 -SSLv3    
    # 添加SSL协议支持协议，去掉不安全的协议。
    SSLCipherSuite HIGH:!RC4:!MD5:!aNULL:!eNULL:!NULL:!DH:!EDH:!EXP:+MEDIUM    
    # 使用此加密套件。
    SSLHonorCipherOrder on
    SSLCertificateFile cert/domain name_public.crt    
    # 将domain name_public.crt替换成您证书文件名。
    SSLCertificateKeyFile cert/domain name.key    
    # 将domain name.key替换成您证书的秘钥文件名。
    SSLCertificateChainFile cert/domain name_chain.crt   
    # 证书链开头如果有#字符，请删除。
    ```

9.  保存 httpd-ssl.conf 文件配置。
10. 重启Apache服务器使SSL配置生效。
    1.  在Apache bin目录下执行以下命令停止Apache服务。

        ``` {#codeblock_4m8_i2n_6ct}
        apachectl -k stop
        ```

    2.  在Apache bin目录下执行以下命令开启Apache服务。

        ``` {#codeblock_7ja_5lf_ta0}
        apachectl -k start
        ```


## 后续操作 {#section_lqu_o0n_01p .section}

证书安装完成后，可通过登录证书绑定域名的方式验证证书是否安装成功。

``` {#codeblock_tmi_f7y_x1b}
https：//domain name   #domain name替换成证书绑定的域名
```

如果网页地址栏出现绿色小锁标志，表示证书安装成功。

验证证书是否安装成功时，如果网站无法通过https正常访问，需确认您安装证书的服务器443端口是否已开启或被其他工具拦截。

## 相关文档 {#section_pb6_zff_hrb .section}

-   [在Tomcat服务器上安装SSL证书](intl.zh-CN/用户指南/下载证书并安装到其他服务器/Tomcat服务器安装SSL证书/安装PFX格式证书.md#)
-   [Ubuntu系统Apache 2部署SSL证书](../../../../intl.zh-CN/最佳实践/Ubuntu系统Apache 2部署SSL证书.md#)
-   [我获取到的数字证书如何配置在自己的Apache中？](../../../../intl.zh-CN/常见问题/常见问题/我获取到的数字证书如何配置在自己的Apache中？.md#)
-   [在Nginx/Tengine服务器上安装证书](intl.zh-CN/用户指南/下载证书并安装到其他服务器/在Nginx__Tengine服务器上安装证书.md#)
-   [在IIS服务器上安装证书](intl.zh-CN/用户指南/下载证书并安装到其他服务器/在IIS服务器上安装证书.md#)
-   [CentOS系统Tomcat 8.5/9部署SSL证书](../../../../intl.zh-CN/最佳实践/CentOS系统Tomcat 8.5__9部署SSL证书.md#)
-   [Jetty服务器配置SSL证书](../../../../intl.zh-CN/常见问题/常见问题/Jetty服务器配置SSL证书.md#)

