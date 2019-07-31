# 全站HTTPS介绍 {#concept_1340450 .concept}

SSL证书支持全站HTTPS服务，帮助您解决SSL证书安装部署、证书到期更新、证书私钥安全存储及TLS加速等问题

将服务器域名的DNS记录解析到该服务的CNAME域名上，即可将您原来的站点服务器设置为全站HTTPS服务。

## 产品优势 {#section_pds_3g0_yth .section}

-   使用全站HTTPS服务，无需再关注证书时间到期之前，重新申请并部署证书的问题。
-   使用全站HTTPS服务，无需再关注证书时间到期后，网站无法提供服务的问题。
-   使用全站HTTPS服务，无需再关注各种加密套件的选择和配置问题。全站HTTPS服务的安全配置支持苹果的ATS、腾讯公司的微信小程序和支付宝小程序及支付接口回调的要求。当仅配置证书开启HTTPS服务时，如果使用错误或低级别的安全套件会使网站出现数据泄露的信息安全问题。
-   使用全站HTTPS服务，提高保障数据传输和网上通信的安全性。您可以查看全站HTTPS服务站点在SSL Labs的检测结果是**A+**。

## 私钥安全性 {#section_bna_onn_hq3 .section}

一般站点服务器的证书和密钥全部部署安装在Web服务器所属主机上。用户访问时，Web服务器会直接处理用户的应用层请求，如果Web服务器存在漏洞（例如：缓冲区溢出等），则有可能导致密钥泄漏，并占用Web服务器的CPU资源。

全站HTTPS服务采用的是阿里云自主研发的证书安全服务，将证书私钥文件加密保存在**KeyManager**服务节点中。**KeyManger**是基于HSM使用信封加密的方式加密存储业务方密钥，确保密钥的安全性。如果Web服务器出现漏洞，通知Web服务器将TLS/SSL的卸载转发给**KeyServer**服务，**KeyServer**服务会按需到**KeyManager**服务获取私钥文件，并加密保存私钥文件至内存中，而不会在硬盘中保存私钥文件。所以即便服务器被攻破了，也仍然无法获取到私钥。

**说明：** Web服务器和**KeyServer**及**KeyServer**与**KeyManager**之间有严格的身份校验规则，同时使用TLS加密隧道进行数据交流。

## TLS/SSL加速 {#section_h2g_nha_7ih .section}

TLS/SSL加速，即通过特定的算法优化内存中的私钥缓存数据。**Tengine**和**KeyServer**之间，**KeyServer**和**KeyManager**之间均采用保活连接，减少TCP握手和TLS握手的开销。同时**KeyServer**服务器上安装了英特尔公司的QAT双加速卡，通过冗余来保证高可用和容灾（每个Web服务器配置多个KeyServer集群，每个KeyServer配置多个KeyManager集群）。

