# 如何在同一服务器上实现多站点多域名HTTPS {#concept_kql_qwv_ydb .concept}

假设有这样一个场景，我们有多个站点（例如site1.marei.com，site2.marei.com和site3.marei.com）绑定到同一个IP：PORT，并区分不同的主机头。我们为每一个SSL站点申请并安装了证书。在浏览网站时，用户仍看到证书不匹配的错误。

## IIS中实现 {#section_ul5_qwv_ydb .section}

问题原因

当一个https的请求到达IIS服务器时，https请求为加密状态，需要拿到相应的服务器证书解密请求。由于每个站点对应的证书不同，服务器需要通过请求中不同的主机头来判断需要用哪个证书解密，然而主机头作为请求的一部分也被加密。最终IIS只好使用第一个绑定到该IP：PORT的站点证书解密请求，从而有可能造成对于其他站点的请求失败而报错。

解决方案

-   第一种解决方案将每个https站点绑定到不同的端口。但是这样的话客户端浏览网页时必须手动指定端口，例如https：//site.domain.com:444
-   第二种解决方案是为每个站点分配一个独立的ip，这样冲突就解决了，甚至主机头也不用添加了。
-   第三种解决方案是使用通配证书。我们采用通配证书颁发给.domain.com，对于我们的示例中，应该采用颁发给.marei.com的证书，这样任何访问该domain的请求均可以通过该证书解密，证书匹配错误也就不复存在了。
-   第四种解决方案是升级为IIS8，IIS8中添加的对于SNI（Server Name Indication）的支持，服务器可以通请求中提取出相应的主机头从而找到相应的证书。

    SNI开启方式请参考[http://www.iis.net/learn/get-started/whats-new-in-iis-8/iis-80-server-name-indication-sni-ssl-scalability](http://www.iis.net/learn/get-started/whats-new-in-iis-8/iis-80-server-name-indication-sni-ssl-scalability)


## Nginx中实现 {#section_yl5_qwv_ydb .section}

打开Nginx安装目录下conf目录中打开nginx.conf文件，找到

```
server {
    listen 443;
    server_name domain1;
    ssl on;
    ssl_certificate 磁盘目录/订单号1.pem;
    ssl_certificate_key 磁盘目录/订单号1.key;
    ssl_session_timeout 5m;
    ssl_protocols TLSv1 TLSv1.1 TLSv1.2; 
    ssl_ciphers AESGCM:ALL:!DH:!EXPORT:!RC4:+HIGH:!MEDIUM:!LOW:!aNULL:!eNULL;
    ssl_prefer_server_ciphers   on;
    location / {
        root   html;
        index  index.html index.htm;
    }
}
```

在上述基础上，再添加另一段配置

```
server {
    listen 443;
    server_name dommain2;
    ssl on;
    ssl_certificate 磁盘目录/订单号2.pem;
    ssl_certificate_key 磁盘目录/订单号2.key;
    ssl_session_timeout 5m;
    ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
    ssl_ciphers AESGCM:ALL:!DH:!EXPORT:!RC4:+HIGH:!MEDIUM:!LOW:!aNULL:!eNULL;
    ssl_prefer_server_ciphers on;
    location / {
        root html;
        index index.html index.htm;
    }
}
```

通过上述配置在Nginx中支持多个证书。

## Apache配置HTTPS虚拟主机共享443端口 {#section_mps_dxv_ydb .section}

```
Listen 443
NameVirtualHost *:443
<VirtualHost *:443>
  ……
ServerName www.example1.com
SSLCertificateFile     common.crt;
SSLCertificateKeyFile  common.key;
SSLCertificateChainFile  ca.crt
  ……
</VirtualHost>
<VirtualHost *:443>
  ……
ServerName www.example2.com
SSLCertificateFile     common2.crt;
SSLCertificateKeyFile  common2.key;
SSLCertificateChainFile  ca2.crt

  ……
</VirtualHost>
```

