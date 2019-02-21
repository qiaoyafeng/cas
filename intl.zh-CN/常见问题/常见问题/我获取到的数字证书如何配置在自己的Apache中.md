# 我获取到的数字证书如何配置在自己的Apache中 {#concept_ccz_hcv_ydb .concept}

通过证书服务申请的数字证书，可以按照通常的方式配置到各种Web服务容器中。但有些数字证书是带有证书链的，在Apache服务器中配置需要按以下步骤进行操作。

## 1. 检查您的数字证书是否带有证书链 {#section_y4j_3cv_ydb .section}

使用文本编辑器打开您的数字证书文件（例如mycert.pem）检查您的数字证书是否带有证书链。如果您的证书文件中有三段`BEGIN CERTIFICATE`信息，说明您的数字证书包含证书链。

**说明：** 如果您的数字证书不包含证书链，则无需执行后续操作，直接在Apache服务器中配置即可。

```

-----BEGIN CERTIFICATE-----
xxxxxx...
-----END CERTIFICATE-----


-----BEGIN CERTIFICATE-----
xxxxxx...
-----END CERTIFICATE-----

-----BEGIN CERTIFICATE-----
xxxxxx...
-----END CERTIFICATE-----
```

## 2. 分离证书链 {#section_epj_3cv_ydb .section}

使用文本编辑器打开您的数字证书文件，复制后两段证书信息（即后两段`-----BEGIN CERTIFICATE-----`）内容到新的文本文件中，并另存为mycert\_chain.pem，即可分离您的数字证书中的证书链。

## 3. 修改文件名称 {#section_fpj_3cv_ydb .section}

将原证书文件名称修改为mycert.pem。这样，您就有了两个pem文件，分别是原证书文件mycert.pem和证书链文件mycert\_chain.pem。

## 4. 配置Apache {#section_gpj_3cv_ydb .section}

在Apache服务器的配置文件中进行如下配置即可。

```

...
SSLEngine On 
SSLCertificateFile conf/ssl.crt/mycert.pem 
SSLCertificateKeyFile conf/ssl.key/mycert.key 
SSLCertificateChainFile conf/ssl.crt/mycert_chain.pem 
...
```

