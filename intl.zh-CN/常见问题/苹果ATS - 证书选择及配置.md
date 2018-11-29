# 苹果ATS - 证书选择及配置 {#concept_tv3_rm5_ydb .concept}

自2017年1月1日起，根据苹果要求，所有iOS应用必须使用ATS（App Transport Security），即iOS应用内的连接必须使用安全的HTTPS连接。同时，苹果要求使用的不仅是一个简单的HTTPS协议连接，而且必须要满足iOS9中的新增特性。

**说明：** 阿里云的CDN、SLB服务中的HTTPS配置完全符合ATS的要求。

苹果ATS针对HTTPS协议包含四个方面的要求。

## 证书颁发机构的要求 {#section_utf_wm5_ydb .section}

-   建议您使用Symantec、GeoTrust品牌的OV型及以上数字证书。
-   对于个人用户，建议使用DV型数字证书，不推荐使用免费证书。
-   CFCA品牌的数字证书只在最新的苹果设备上才支持，因此不推荐选择CFCA品牌。

## 证书的哈希算法和密钥长度的要求 {#section_bvr_rm5_ydb .section}

-   哈希算法：上述推荐的证书品牌中是使用的哈希算法都是SHA256或者更高强度的算法，符合ATS的要求。
-   密钥长度
    -   如果您选择使用系统创建CSR的方式，系统生成的密钥采用的是2,048位的RSA加密算法，完全符合ATS的要求。
    -   如果您选择自己创建CSR文件，请确保使用2,048位或以上的RSA加密算法。

## 传输协议的要求 {#section_dvr_rm5_ydb .section}

传输协议必须满足TLS1.2。需要在Web服务器上开启TLSv1.2，通常要求：

-   基于OpenSSL环境的Web服务器，需要使用OpenSSL 1.0及以上版本，推荐使用OpenSSL 1.0.1及以上版本。
-   基于Java环境的Web服务器，需要使用JDK 1.7 及以上版本。
-   其他Web服务器，除IIS7.5以及Weblogic 10.3.6比较特殊外，只要Web服务版本满足，默认均开启TLSv1.2。

详细Web服务器配置要求说明如下：

-   Apache 、 Nginx Web服务器需要使用OpenSSL 1.0及以上版本来支持TLSv1.2。
-   Tomcat 7及以上版本Web服务器需要使用JDK 7.0及以上版本来支持TLSv1.2。
-   IIS 7.5 Web服务器默认不开启TLSv1.2，需要修改注册表以开启TLSv1.2。

    下载并导入[ats.reg](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/48151/cn_zh/1481732046198/ATS.rar) 注册表脚本后，重启（或注销）服务器，即可使TLSv1.2 生效。

-   IBM Domino Server 9.0.1 FP3 Web服务器支持TLSv1.2。根据ATS要求，建议使用IBM Domino Server 9.0.1 FP5版本。更多信息请参考：
    -   [IBM Notes and Domino wiki](https://www-10.lotus.com/ldd/dominowiki.nsf/dx/TLS_Cipher_Configuration#TLS+1.2)
    -   [IBM HTTP SSL Server Questions and Answers](http://publib.boulder.ibm.com/httpserv/ihsdiag/ssl_questions.html)
-   IBM HTTP Server 8.0及以上版本支持TLSv1.2。根据ATS要求，建议使用IBM HTTP Server 8.5及以上版本。
-   Weblogic 10.3.6及以上版本Web服务器需要使用Java7及以上版本来支持TLSv1.2。

    **说明：** Weblogic 10.3.6中存在多个SHA256兼容问题，建议最低使用Weblogic 12版本，或为Weblogic 10.3.6配置前端Apache或Nginx的HTTPS代理或SSL前端负载。

-   Webspere V7.0.0.23及以上版本、Webspere V8.0.0.3及以上版本、Webspere V8.5.0.0及以上版本支持 TLSv1.2。关于如何配置Webspere服务器支持TLSv1.2，请参考 [Configure websphere application server SSL protocol to TLSv1.2](https://developer.ibm.com/answers/questions/206952/how-do-i-configure-websphere-application-server-ss.html)。

## 签字算法的要求 {#section_hvr_rm5_ydb .section}

签字算法必须满足如下算法要求：

-   TLS\_ECDHE\_ECDSA\_WITH\_AES\_256\_GCM\_SHA384
-   TLS\_ECDHE\_ECDSA\_WITH\_AES\_128\_GCM\_SHA256
-   TLS\_ECDHE\_ECDSA\_WITH\_AES\_256\_CBC\_SHA384
-   TLS\_ECDHE\_ECDSA\_WITH\_AES\_256\_CBC\_SHA
-   TLS\_ECDHE\_ECDSA\_WITH\_AES\_128\_CBC\_SHA256
-   TLS\_ECDHE\_ECDSA\_WITH\_AES\_128\_CBC\_SHA
-   TLS\_ECDHE\_RSA\_WITH\_AES\_256\_GCM\_SHA384
-   TLS\_ECDHE\_RSA\_WITH\_AES\_128\_GCM\_SHA256
-   TLS\_ECDHE\_RSA\_WITH\_AES\_256\_CBC\_SHA384
-   TLS\_ECDHE\_RSA\_WITH\_AES\_128\_CBC\_SHA256
-   TLS\_ECDHE\_RSA\_WITH\_AES\_128\_CBC\_SHA

## 配置示例 {#section_jvr_rm5_ydb .section}

以下通过举例方式说明不同Web服务器的ATS协议及加密套件应该如何配置：

**说明：** 示例中只列举了与ATS协议有关的属性，请不要完全复制以下配置用于您的实际环境。

**Nginx配置文件片段**

Nginx配置文件中ssl\_ciphers及ssl\_protocols属性与ATS协议有关。

```

server {
ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:ECDHE:ECDH:AES:HIGH:!NULL:!aNULL:!MD5:!ADH:!RC4;
ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
}
```

**Tomcat配置文件片段**

Tomcat配置文件中的SSLProtocol及SSLCipherSuite属性与ATS协议有关。

```

<Connector port="443" protocol="HTTP/1.1" SSLEnabled="true"
scheme="https" secure="true"
ciphers="TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256"
SSLProtocol="TLSv1+TLSv1.1+TLSv1.2"
SSLCipherSuite="ECDHE-RSA-AES128-GCM-SHA256:ECDHE:ECDH:AES:HIGH:!NULL:!aNULL:!MD5:!ADH:!RC4" />
```

IIS系列Web服务器的配置方法，请参考 [Enabling TLS 1.2 on IIS 7.5 for 256-bit cipher strength](http://jackstromberg.com/2013/09/enabling-tls-1-2-on-iis-7-5-for-256-bit-cipher-strength/)。您也可以使用[IIS Crypto](https://www.nartac.com/Products/IISCrypto/Download)可视化配置插件进行配置。

## ATS检测工具 {#section_ovr_rm5_ydb .section}

您可在苹果电脑中使用系统自带的工具进行ATS检测，执行以下命令即可：`nscurl --ats-diagnostics --verbose 网址`

