# Ubuntu系统Apache 2部署SSL证书 {#concept_cfn_yf2_kgb .concept}

本文档为您介绍了如何在Ubuntu系统以及Apache2中安装阿里云SSL证书。

## 环境准备 {#section_m3b_x3j_kgb .section}

操作系统：Ubuntu

Web服务器：Apache 2

## 前提条件 {#section_dp2_hk2_kgb .section}

-   已从[阿里云SSL证书服务控制台](https://yundunnext.console.aliyun.com/?spm=5176.2020520155.aliyun_sidebar.30.25af2a528ujbXD&p=cas#/overview/cn-hangzhou)下载Apache服务器证书。
-   已安装Open SSL。

## 操作步骤 {#section_b2p_3k2_kgb .section}

1.  运行以下命令在apache2目录下创建ssl目录。

    ```
    mkdir /etc/apache2/ssl
    ```

2.  运行以下命令将下载的阿里云证书文件复制到ssl目录中。

    ```
    cp -r YourDomainName_public.crt /etc/apache2/ssl
    ```

    ```
    cp -r YourDomainName_chain.crt /etc/apache2/ssl
    ```

    ```
    cp -r YourDomainName.key /etc/apache2/ssl
    ```

3.  运行以下命令启用SSL模块。

    ```
    sudo a2enmod ssl
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/93419/155011412036989_zh-CN.png)

    SSL模块启用后可执行`ls /etc/apache2/sites-available`查看目录下生成的default-ssl.conf文件。

    **说明：** 443端口是网络浏览端口，主要用于HTTPS服务。SSL模块启用后会自动放行443端口。若443端口未自动放行，可执行`vi /etc/apache2/ports.conf`并添加`Listen 443`手动放行。

4.  运行以下命令修改SSL配置文件default-ssl.conf。

    ```
    vi /etc/apache2/sites-available/default-ssl.conf
    ```

    在default-ssl.conf文件中找到以下参数进行修改后保存并退出。

    ```language-javascript
    <IfModules mod_ssl.c>
    <VirtualHost *:443>  
    ServerName 
    #修改为证书绑定的域名www.YourDomainName.com。
    SSLCertificateFile /etc/apache2/www.YourDomainName_public.crt 
    #将/etc/apache2/www.YourDomainName.com_public.crt替换为证书文件路径+证书文件名。
    SSLCertificateKeyFile /etc/apache2/www.YourDomainName.com.key  
    #将/etc/apache2/www.YourDomainName.com.key替换为证书秘钥文件路径+证书秘钥文件名。
    SSLCertificateChainFile /etc/apache2/www.YourDomainName.com_chain.crt  
    #将/etc/apache2/www.YourDomainName.com_chain.crt替换为证书链文件路径+证书链文件名。
    
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/93419/155011412136991_zh-CN.png)

    /sites-available：该目录存放的是可用的虚拟主机；/sites-enabled：该目录存放的是已经启用的虚拟主机。

    **说明：** default-ssl.conf文件可能存放在/etc/apache2/sites-available或/etc/apache2/sites-enabled目录中。

5.  运行以下命令把default-ssl.conf映射至/etc/apache2/sites-enabled文件夹中建立软链接、实现二者之间的自动关联。

    ```
    sudo ln -s /etc/apache2/sites-available/default-ssl.conf /etc/apache2/sites-enabled/001-ssl.conf
    ```

6.  运行以下命令重新加载Apache 2配置文件。

    ```
    sudo /etc/init.d/apache2 force-reload
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/93419/155011412136992_zh-CN.png)

7.  运行以下命令重启Apache 2服务。

    ```
    sudo /etc/init.d/apache2 restart
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/93419/155011412136993_zh-CN.png)


## 后续操作 {#section_e3j_jk2_kgb .section}

Apache 2服务重启成功后，您可在浏览器中输入https://www.YourDomainName.com验证证书安装结果。浏览器地址栏显示绿色的小锁标识说明证书安装成功。

