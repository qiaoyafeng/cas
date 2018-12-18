# 在Apache服务器上安装证书 {#concept_zsp_d1x_yfb .concept}

您可以将从阿里云SSL证书服务控制台下载的证书安装到您的Apache服务器上。

## 前提条件 {#section_xdh_4qb_1gb .section}

申请证书时需要选择**系统自动创建CSR**。

本文档证书名称以**domain name**为示例，如证书文件名称为**domain name\_public.cert**，证书链文件名称为**domain name\_chain.cert**,证书秘钥文件名称为**domain name.key**。

## 操作指南 {#section_ydh_4qb_1gb .section}

1.  登录阿里云[SSL证书控制台](https://yundunnext.console.aliyun.com/?p=casnext#/overview/cn-hangzhou)。
2.  在SSL证书页面定位到需要下载的证书并单击证书卡片右下角的**下载**打开**证书下载**对话框。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/66242/154512147533499_zh-CN.png)

3.  在**证书下载**对话框中定位到Apache服务器，并单击右侧**操作**栏的**下载**将Apache版证书压缩包下载到本地。
4.  解压Apache证书。

    您将看到文件夹中有3个文件：

    -   证书文件（以.crt为后缀或文件类型）
    -   证书链文件（以.crt为后缀或文件类型）
    -   秘钥文件（以.key为后缀或文件类型）
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/66001/154512147533689_zh-CN.png)

    **说明：** **.crt**扩展名的证书文件采用Base64-encoded的PEM格式文本文件，您可根据需要修改成**.pem**等扩展名。

    证书的格式详见[主流数字证书都有哪些格式](https://help.aliyun.com/knowledge_detail/42214.html)。

5.  在**Apache安装目录**下新建**cert目录**，并将下载的Apache证书、证书链和秘钥文件拷贝到**cert目录**中。

    **说明：** 如果申请证书时选择了**手动创建CSR文件**，请将手动生成创建的秘钥文件拷贝到**cert目录**下。

6.  打开**Apache安装目录** \> **conf文件夹** \> **httpd.conf文件**，在**httpd.conf文件**中找到以下参数并进行配置。

    ```
    #LoadModule ssl_module modules/mod_ssl.so   #删除行首的配置语句注释符号“#”。如果找不到请确认是否编译过 openssl 插件。
    #Include conf/extra/httpd-ssl.conf   删除行首的配置语句注释符号“#”。
    
    ```

7.  保存**httpd.conf文件**后退出。
8.  打开**Apache安装目录** \> **conf文件夹** \> **extra** \> **httpd-ssl.conf文件**，在**httpd-ssl.conf文件**中找到以下参数并进行配置。

    **说明：** 根据操作系统的不同， 也可能http-ssl.conf文件也可能存放在conf.d/ssl.conf目录中。

    ```
    
    SSLProtocol all -SSLv2 -SSLv3    # 添加SSL协议支持协议，去掉不安全的协议。
    SSLCipherSuite HIGH:!RC4:!MD5:!aNULL:!eNULL:!NULL:!DH:!EDH:!EXP:+MEDIUM    # 修改加密套件如下：
    SSLHonorCipherOrder on
    SSLCertificateFile cert/domain name_public.crt    # 将domain name_public.crt替换成您证书文件名。
    SSLCertificateKeyFile cert/domain name.key    # 将domain name.key替换成您证书的秘钥文件名。
    SSLCertificateChainFile cert/domain name_chain.crt   # 以下证书链开头如果有#字符，请删除。
    ```

9.  保存httpd-ssl.conf文件配置。
10. 进入Apache 安装目录下的bin 目录，使用以下命令重启Apache服务器。

    ```
    /apachectl -k stop./apachectl -k start
    ```


