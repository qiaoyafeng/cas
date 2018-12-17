# 在Apache服务器上安装证书 {#concept_zsp_d1x_yfb .concept}

您可以将下载的证书安装到Apache服务器上。

## 前提条件 {#section_xdh_4qb_1gb .section}

申请证书时需要选择**系统自动创建CSR**。

申请证书时如果选择**手动创建CSR**，您需要选择**其他服务器**下载.crt证书文件。

## 操作指南 {#section_ydh_4qb_1gb .section}

1.  登录阿里云[SSL证书控制台](https://yundunnext.console.aliyun.com/?p=casnext#/overview/cn-hangzhou)。
2.  在SSL证书页面定位到需要下载的证书并单击证书卡片右下角的**下载**打开**证书下载**对话框。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/66242/154503774633499_zh-CN.png)

3.  在**证书下载**对话框中定位到Apache服务器，并单击右侧**操作**栏的**下载**将Apache版证书压缩包下载到本地。
4.  解压Apache证书。您将看到文件中有一个证书文件（以.crt为后缀或文件类型）和一个秘钥文件（以.key为后缀或文件类型）。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/66001/154503774633689_zh-CN.png)

5.  在**Apache安装目录**下新建**cert目录**，并将下载的Apache证书和秘钥文件拷贝到**cert目录**中。
6.  打开**Apache安装目录** \> **conf文件夹** \> **httpd.conf文件**，在**httpd.conf文件**中找到以下参数并进行配置。

    ```
    删除行首的配置语句注释符号“#”。如果找不到请确认是否编译过 openssl 插件。
    #LoadModule ssl_module modules/mod_ssl.so 
    删除行首的配置语句注释符号“#”。
    #Include conf/extra/httpd-ssl.conf
    
    ```

7.  保存**httpd.conf文件**后退出。
8.  打开**Apache安装目录** \> **conf文件夹** \> **extra** \> **httpd-ssl.conf文件**，在**httpd-ssl.conf文件**中找到以下参数并进行配置。

    **说明：** 根据操作系统的不同， 也可能http-ssl.conf文件也可能存放在conf.d/ssl.conf目录中。

    ```
    
    # 添加SSL协议支持协议，去掉不安全的协议。
    SSLProtocol all -SSLv2 -SSLv3
    # 修改加密套件如下：
    SSLCipherSuite HIGH:!RC4:!MD5:!aNULL:!eNULL:!NULL:!DH:!EDH:!EXP:+MEDIUM
    SSLHonorCipherOrder on
    # 将1570059_key.test.com_public.crt替换成您证书公钥文件名。
    SSLCertificateFile cert/1570059_key.test.com_public.crt
    # 将a.key替换成您证书的私钥文件名。
    SSLCertificateKeyFile cert/a.key
    # 以下证书链开头如果有 '#'字符，请删除。
    SSLCertificateChainFile cert/a_chain.crt
    ```

9.  保存httpd-ssl.conf文件配置。
10. 进入Apache 安装目录下的bin 目录，使用以下命令重启Apache服务器。

    ```
    /apachectl -k stop./apachectl -k start
    ```


