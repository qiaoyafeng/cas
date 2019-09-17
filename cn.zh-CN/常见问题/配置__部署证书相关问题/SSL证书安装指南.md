# SSL证书安装指南 {#concept_95505_zh .concept}

阿里云SSL证书服务可提供Nginx服务器、Apache服务器、Tomcat服务器、IIS服务器和其他服务器类型证书下载并安装到对应的服务器中。

不同格式的证书下载解压后可能包含以下文件：

-   .key 文件是证书私钥文件，如果申请证书时没有选择系统创建CSR，则没有该文件。请您保存好该私钥文件。
-   .crt 文件是证书文件，一般包含两段内容。如果是Apache服务器，会将证书文件拆分成 \_public.crt\(证书\)文件和\_chain.crt（证书链或中间证书）文件。
-   .pem 文件是证书文件，一般包含两段内容。Nginx证书会使用扩展名文件，在阿里云SSL证书中与.crt文件一样。

    **说明：** **.crt**扩展名的证书文件采用Base64-encoded的PEM格式文本文件，可根据需要，修改成.pem等扩展名。

-   .pfx 文件，一般适合Tomcat/IIS服务器。每次下载都会产生新密码，该密码仅匹配本次下载的证书。如果需要更新证书文件，同时也要更新密码。

**说明：** 如果证书是在阿里云的产品上使用，建议下载Nginx服务器版本的证书。

## 常见的服务器安装指南 { .section}

-   [在Tomcat服务器上安装SSL证书](../../../../intl.zh-CN/用户指南/下载证书并安装到其他服务器/Tomcat服务器安装SSL证书/安装PFX格式证书.md#)
-   [在Apache服务器上安装SSL证书](../../../../intl.zh-CN/用户指南/下载证书并安装到其他服务器/在Apache服务器上安装SSL证书.md#)
-   [Ubuntu系统Apache 2部署SSL证书](../../../../intl.zh-CN/最佳实践/Ubuntu系统Apache 2部署SSL证书.md#)
-   [我获取到的数字证书如何配置在自己的Apache中？](intl.zh-CN/常见问题/配置__部署证书相关问题/我获取到的数字证书如何配置在自己的Apache中？.md#)
-   [在Nginx/Tengine服务器上安装证书](../../../../intl.zh-CN/用户指南/下载证书并安装到其他服务器/在Nginx__Tengine服务器上安装证书.md#)
-   [在IIS服务器上安装证书](../../../../intl.zh-CN/用户指南/下载证书并安装到其他服务器/在IIS服务器上安装证书.md#)
-   [CentOS系统Tomcat 8.5/9部署SSL证书](../../../../intl.zh-CN/最佳实践/CentOS系统Tomcat 8.5__9部署SSL证书.md#)
-   [Jetty服务器配置SSL证书](intl.zh-CN/常见问题/配置__部署证书相关问题/Jetty服务器配置SSL证书.md#)

