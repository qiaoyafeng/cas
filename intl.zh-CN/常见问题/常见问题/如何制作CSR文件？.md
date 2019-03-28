# 如何制作CSR文件？ {#concept_b4f_mrp_ydb .concept}

在申请数字证书之前，您必须先生成证书私钥和证书请求文件（Certificate Signing Request，简称 CSR）。CSR文件是您的公钥证书原始文件，包含了您的服务器信息和您的单位信息，需要提交给CA认证中心进行审核。

**说明：** 建议您使用系统创建的CSR，避免出现内容不正确而导致的审核失败。关于审核失败详细信息，请参考[审核失败 - 主域名不能为空](intl.zh-CN/常见问题/常见问题/审核失败 - 主域名不能为空.md#)。

手动生成CSR文件的同时会生成私钥文件，请务必妥善保管和备份您的私钥。

您手动生成CSR文件时，一般需要输入以下信息：

**说明：** 输入的中文信息需要使用UTF8编码格式。

-   Organization Name\(O\)： 申请单位名称法定名称，可以是中文或英文。
-   Organization Unit\(OU\)： 申请单位的所在部门，可以是中文或英文。
-   Country Code\(C\)： 申请单位所属国家，只能是两个字母的国家码。例如，中国只能是CN。
-   State or Province\(S\)： 申请单位所在省名或州名，可以是中文或英文。
-   Locality\(L\)： 申请单位所在城市名，可以是中文或英文。
-   Common Name\(CN\)： 申请SSL证书的具体网站域名。

**说明：** 证书服务系统对CSR文件的密钥长度有严格要求，密钥长度必须是2,048位，密钥类型必须为RSA。如果申请证书是多域名或者通配子域名，在**Common Name**或**What is your first and last name?**字段只需要输入一个域名即可（通配子域名可以输入\*.example.com等）。

## 使用OpenSSL工具生成CSR文件 {#section_x2y_3rv_ydb .section}

1.  安装[OpenSSL工具](https://www.openssl.org/)。
2.  执行命令`openssl req -new -nodes -sha256 -newkey rsa:2048 -keyout myprivate.key -out mydomain.csr`生成CSR文件。其中，
    -   `-new` 指定生成一个新的CSR。
    -   `-nodes` 指定私钥文件不被加密。
    -   `-sha256` 指定摘要算法。
    -   `-keyout` 生成私钥文件。
    -   `-newkey rsa:2048` 指定私钥类型和长度。
3.  生成CSR文件mydomain.csr。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13600/15537512524272_zh-CN.png)

    需要输入的信息说明如下：

    |字段|说明|示例|
    |--|--|--|
    |Country Name|ISO国家代码（两位字符）|CN|
    |State or Province Name|所在省份|ZheJiang|
    |Locality Name|所在城市|HangZhou|
    |Organization Name|公司名称|HangZhou xxx Technologies, Inc.|
    |Organizational Unit Name|部门名称|IT Dept.|
    |Common Name|申请证书的域名|www.example.com|
    |Email Address|不需要输入|-|
    |A challenge password|不需要输入|-|

    完成命令提示的输入后，会在当前目录下生成myprivate.key（私钥文件）和 mydomain.csr（CSR，证书请求文件）两个文件。


**说明：** 在使用OpenSSL工具生成中文证书时需要注意中文编码格式必须使用UTF8编码格式。同时，需要在编译OpenSSL工具时指定支持UTF8编码格式。

如果您需要输入中文信息，建议您使用Keytool工具生成CSR文件。

## 使用Keytool工具生成CSR文件 {#section_ix2_yrv_ydb .section}

1.  安装Keytool工具，Keytool工具一般包含在Java Development Kit（JDK）工具包中。
2.  使用Keytool工具生成keystore证书文件。

    **说明：** Keystore证书文件中包含密钥，导出密钥方式请参考[主流数字证书都有哪些格式？](intl.zh-CN/常见问题/常见问题/主流数字证书都有哪些格式？.md#)。

    1.  执行命令`keytool -genkey -alias mycert -keyalg RSA -keysize 2048 -keystore ./mydomain.jks生成 keystore`证书文件。其中，

        -   `-keyalg` 指定密钥类型，必须是RSA。
        -   `-keysize` 指定密钥长度为 2,048。
        -   `-alias` 指定证书别名，可自定义。
        -   `-keystore` 指定证书文件保存路径。
        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13600/15537512524273_zh-CN.png)

    2.  输入证书保护密码，然后根据下表依次输入所需信息：

        |问题|说明|示例|
        |--|--|--|
        |What is your first and last name?|申请证书的域名|www.example.com|
        |What is the name of your organizational unit?|部门名称|IT Dept.|
        |What is the name of your organization?|公司名称|HangZhou xxx Technologies,Ltd.|
        |What is the name of your City or Locality?|所在城市|HangZhou|
        |What is the name of your State or Province?|所在省份|ZheJiang|
        |What is the two-letter country code for this unit?|ISO 国家代码（两位字符）|CN|

        输入完成后，确认输入内容是否正确，输入Y表示正确。

    3.  根据提示输入密钥密码。可以与证书密码一致，如果一致直接按回车键即可。
3.  通过证书文件生成证书请求。
    1.  执行命令`keytool -certreq -sigalg SHA256withRSA -alias mycert -keystore ./mydomain.jks -file ./mydomain.csr`生成CSR文件。其中，
        -   `sigalg`指定摘要算法，使用SHA256withRSA。
        -   `alias`指定别名，必须与keystore文件中的证书别名一致。
        -   `keystore`指定证书文件。
        -   `file`指定证书请求文件（CSR）。
    2.  根据提示输入证书密码即可以生成mydomain.csr。

