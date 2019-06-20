# 在GlassFish服务器上安装证书 {#concept_ypq_wrq_1gb .concept}

本文档介绍如何在Glassfish服务器上安装SSL证书。

## 操作步骤 {#section_yhb_dz2_cgb .section}

本文档证书名称以**cer01**为示例，如证书文件名称为**cer01.pem**，证书秘钥文件名称为**cer01.key**。

1.  登录阿里云[SSL证书控制台](https://yundunnext.console.aliyun.com/?spm=5176.2020520001.aliyun_sidebar.108.356a4bd3MLXFkb&p=cas#/overview/cn-hangzhou)。
2.  在SSL证书页面，点击**已签发**标签，定位到需要下载的证书并单击证书卡片右下角的**下载**打开**证书下载**对话框。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/77568/155244804639185_zh-CN.jpg)

3.  在**证书下载**对话框中定位到**其他**服务器类型，并单击右侧**操作**栏的**下载**将证书压缩包下载到本地。
4.  解压证书。您将看到文件中有一个证书文件（以.pem为后缀或文件类型）和一个秘钥文件（以.txt为后缀或文件类型）。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/77568/155244804634118_zh-CN.png)

5.  输入以下两行命令将证书和秘钥文件转换成JKS格式。

    ```
    openssl pkcs12 -export -in cer01.pem -inkey cer01.key -out temp.p12 -passout pass:changeit -name s1as
    #请用您的证书名称替换命令行中cer01.pem、用您的证书秘钥替换cer01.key。转换证书格式时设置的密码必须和您Glassfish服务器中自带的证书密码一致，该证书默认密码是changeit。
    ```

    ```
    keytool -importkeystore -srckeystore temp.p12 -srcstoretype PKCS12 -srcstorepass changeit -deststoretype JKS -destkeystore ./glassfish5/glassfish/domains/domain1/config/keystore.jks -deststorepass changeit -alias s1as
    #转换证书格式时设置的密码必须和您Glassfish服务器中自带的证书密码一致，该证书默认密码是changeit。
    ```

6.  重启domain。

    ```
    ./glassfish5/bin/asadmin restart-domain
    ```

7.  检查您阿里云证书绑定的域名是否生效。

    ```
    wget https://127.0.0.1:8181
    ```


