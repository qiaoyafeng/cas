# 在Nginx/Tengine服务器上安装证书 {#concept_n45_21x_yfb .concept}

## 前提条件 {#section_xdh_4qb_1gb .section}

申请证书时需要选择**系统自动创建CSR**。

## 操作指南 {#section_ydh_4qb_1gb .section}

1.  登录阿里云[SSL证书控制台](https://yundunnext.console.aliyun.com/?p=casnext#/overview/cn-hangzhou)。
2.  在SSL证书页面定位到需要下载的证书并单击证书卡片右下角的**下载**打开**证书下载**对话框。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/66242/154503779133499_zh-CN.png)

3.  在**证书下载**对话框中定位到Nginx/Tengine服务器，并单击右侧**操作**栏的**下载**将Apache版证书压缩包下载到本地。
4.  解压Nginx/Tengine证书。您将看到文件中有一个证书文件（以.pem为后缀或文件类型）和一个秘钥文件（以.key为后缀或文件类型）。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/66002/154503779133690_zh-CN.png)

5.  在**Apache安装目录**下新建**cert目录**，并将下载的Apache证书和秘钥文件拷贝到**cert目录**中。
6.  打开**Nginx安装目录** \> **conf文件夹** \> **nginx.conf文件**，在**nginx.conf文件**中找到以下属性：

    ```
    
    # HTTPS server
      server {
      listen 443;
      server_name localhost;
      ssl on;
      ssl_certificate cert.pem;
      ssl_certificate_key cert.key;
      ssl_session_timeout 5m;
      ssl_protocols SSLv2 SSLv3 TLSv1;
      ssl_ciphers ALL:!ADH:!EXPORT56:RC4+RSA:+HIGH:+MEDIUM:+LOW:+SSLv2:+EXP;
      ssl_prefer_server_ciphers on;
      location / {
    
    ```

    修改nginx.conf文件如下：

    ```
    
    以下属性中以ssl开头的属性代表与证书配置有关，其他属性请根据自己的需要进行配置。
    server {
    listen 443;
    # localhost修改为您证书绑定的域名。
    server_name localhost;
    ssl on;
    root html;
    index index.html index.htm;
    #将1570059_key.test.com.pem替换成您证书的文件名。
    ssl_certificate cert/1570059_key.test.com.pem;
    #将1570059_key.test.com.key替换成您证书的私钥文件名。
    ssl_certificate_key cert/1570059_key.test.com.key;
    ssl_session_timeout 5m;
    # 修改加密套件如下：
    ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:ECDHE:ECDH:AES:HIGH:!NULL:!aNULL:!MD5:!ADH:!RC4;
    #protocols修改如下：
    ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
    ssl_prefer_server_ciphers on;
    location / {
    #站点目录：
    root html;
    #添加以下属性：
    index index.html index.htm;
    
    ```

7.  保存**nginx.conf文件**后退出。
8.  重启Nginx服务器。

