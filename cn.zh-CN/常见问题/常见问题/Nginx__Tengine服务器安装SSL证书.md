# Nginx/Tengine服务器安装SSL证书 {#concept_95491_zh .concept}

在证书控制台下载Nginx版本证书。下载到本地的压缩文件包解压后包含：

-    **.crt**文件：是证书文件，crt是pem文件的扩展名。
-    **.key**文件：证书的私钥文件（申请证书时如果没有选择**自动创建CSR**，则没有该文件）。

**说明：** **.pem**扩展名的证书文件采用Base64-encoded的PEM格式文本文件，可根据需要修改扩展名。

以Nginx标准配置为例，假如证书文件名是a.pem，私钥文件是a.key。

1.  在Nginx的安装目录下创建cert目录，并且将下载的全部文件拷贝到cert目录中。如果申请证书时是自己创建的CSR文件，请将对应的私钥文件放到cert目录中并且命名其为a.key。
2.  打开 **Nginx安装目录** \> **conf目录**中的 nginx.conf 文件，找到：

    ```
    # HTTPS server
    # #server {
    # listen 443;
    # server_name localhost;
    # ssl on;
    # ssl_certificate cert.pem;
    # ssl_certificate_key cert.key;
    # ssl_session_timeout 5m;
    # ssl_protocols SSLv2 SSLv3 TLSv1;
    # ssl_ciphers ALL:!ADH:!EXPORT56:RC4+RSA:+HIGH:+MEDIUM:+LOW:+SSLv2:+EXP;
    # ssl_prefer_server_ciphers on;
    # location / {
    #
    #
    #}
    #}
    ```

3.  将其修改为 \(以下属性中ssl开头的属性与证书配置有直接关系，其它属性请结合自己的实际情况复制或调整\) :

    ```
    server {
        listen 443;
        server_name localhost;
        ssl on;
        root html;
        index index.html index.htm;
        ssl_certificate   cert/a.pem;
        ssl_certificate_key  cert/a.key;
        ssl_session_timeout 5m;
        ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:ECDHE:ECDH:AES:HIGH:!NULL:!aNULL:!MD5:!ADH:!RC4;
        ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
        ssl_prefer_server_ciphers on;
        location / {
            root html;
            index index.html index.htm;
        }
    }
    ```

4.  保存并退出。
5.  重启Nginx。

