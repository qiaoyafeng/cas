# Ubuntu系统Apache 2部署SSL证书 {#concept_cfn_yf2_kgb .concept}

本文档为您介绍了如何在Ubuntu系统以及Apache2中安装阿里云SSL证书。

## 环境准备 {#section_m3b_x3j_kgb .section}

操作系统：Ubuntu

Web服务器：Apache 2

## 前提条件 {#section_dp2_hk2_kgb .section}

-   已从[SSL证书控制台](https://yundunnext.console.aliyun.com/?p=cas#/overview/cn-hangzhou)下载Apache服务器证书。
-   已安装Open SSL。

## 操作步骤 {#section_b2p_3k2_kgb .section}

1.  运行以下命令在apache2目录下创建ssl目录。

    ``` {#codeblock_zar_o4i_kxn}
    mkdir /etc/apache2/ssl
    ```

2.  运行以下命令将下载的阿里云证书文件复制到ssl目录中。

    ``` {#codeblock_bmb_kug_fw5}
    cp -r YourDomainName_public.crt /etc/apache2/ssl
    ```

    ``` {#codeblock_f9k_47o_ixa}
    cp -r YourDomainName_chain.crt /etc/apache2/ssl
    ```

    ``` {#codeblock_4py_zxp_p3s}
    cp -r YourDomainName.key /etc/apache2/ssl
    ```

3.  运行以下命令启用SSL模块。

    ``` {#codeblock_cek_fl1_wqf}
    sudo a2enmod ssl
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/93419/155983836736989_zh-CN.png)

    SSL模块启用后可执行`ls /etc/apache2/sites-available`查看目录下生成的default-ssl.conf文件。

    **说明：** 443端口是网络浏览端口，主要用于HTTPS服务。SSL模块启用后会自动放行443端口。若443端口未自动放行，可执行`vi /etc/apache2/ports.conf`并添加`Listen 443`手动放行。

4.  运行以下命令修改SSL配置文件default-ssl.conf。

    ``` {#codeblock_jsm_eeb_lv1}
    vi /etc/apache2/sites-available/default-ssl.conf
    ```

    在default-ssl.conf文件中找到以下参数进行修改后保存并退出。

    ``` {#codeblock_kza_axj_m73 .language-javascript}
    <IfModules mod_ssl.c>
    <VirtualHost *:443>  
    ServerName   #修改为证书绑定的域名www.YourDomainName.com。
    SSLCertificateFile /etc/apache2/ssl/www.YourDomainName_public.crt   #将/etc/apache2/ssl/www.YourDomainName.com_public.crt替换为证书文件路径+证书文件名。
    SSLCertificateKeyFile /etc/ssl/apache2/www.YourDomainName.com.key   #将/etc/apache2/ssl/www.YourDomainName.com.key替换为证书秘钥文件路径+证书秘钥文件名。
    SSLCertificateChainFile /etc/apache2/ssl/www.YourDomainName.com_chain.crt  #将/etc/apache2/ssl/www.YourDomainName.com_chain.crt替换为证书链文件路径+证书链文件名。
    						
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/93419/155983836736991_zh-CN.png)

    /sites-available：该目录存放的是可用的虚拟主机；/sites-enabled：该目录存放的是已经启用的虚拟主机。

    **说明：** default-ssl.conf文件可能存放在/etc/apache2/sites-available或/etc/apache2/sites-enabled目录中。

5.  运行以下命令把default-ssl.conf映射至/etc/apache2/sites-enabled文件夹中建立软链接、实现二者之间的自动关联。

    ``` {#codeblock_yiu_5sf_pz1}
    sudo ln -s /etc/apache2/sites-available/default-ssl.conf /etc/apache2/sites-enabled/001-ssl.conf
    ```

6.  运行以下命令重新加载Apache 2配置文件。

    ``` {#codeblock_a6z_6jp_zid}
    sudo /etc/init.d/apache2 force-reload
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/93419/155983836736992_zh-CN.png)

7.  运行以下命令重启Apache 2服务。

    ``` {#codeblock_0pl_duv_m3d}
    sudo /etc/init.d/apache2 restart
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/93419/155983836736993_zh-CN.png)


## 后续操作 {#section_e3j_jk2_kgb .section}

Apache 2服务重启成功后，您可在浏览器中输入https://www.YourDomainName.com验证证书安装结果。浏览器地址栏显示绿色的小锁标识说明证书安装成功。

安装证书相关文档：

-   [在Tomcat服务器上安装SSL证书](../../../../intl.zh-CN/用户指南/下载证书并安装到其他服务器/Tomcat服务器安装SSL证书/安装PFX格式证书.md#)
-   [在Apache服务器上安装SSL证书](../../../../intl.zh-CN/用户指南/下载证书并安装到其他服务器/在Apache服务器上安装SSL证书.md#)
-   [我获取到的数字证书如何配置在自己的Apache中？](../../../../intl.zh-CN/常见问题/常见问题/我获取到的数字证书如何配置在自己的Apache中？.md#)
-   [在Nginx/Tengine服务器上安装证书](../../../../intl.zh-CN/用户指南/下载证书并安装到其他服务器/在Nginx__Tengine服务器上安装证书.md#)
-   [在IIS服务器上安装证书](../../../../intl.zh-CN/用户指南/下载证书并安装到其他服务器/在IIS服务器上安装证书.md#)
-   [CentOS系统Tomcat 8.5/9部署SSL证书](intl.zh-CN/最佳实践/CentOS系统Tomcat 8.5__9部署SSL证书.md#)
-   [Jetty服务器配置SSL证书](../../../../intl.zh-CN/常见问题/常见问题/Jetty服务器配置SSL证书.md#)

