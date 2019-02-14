# CentOS系统Tomcat 8.5/9部署SSL证书 {#concept_i2b_cdb_mgb .concept}

本文档介绍了CentOS系统下Tomcat 8.5或9部署SSL证书的操作说明。

## 环境准备 {#section_m3b_x3j_kgb .section}

操作系统：CentOS 7.6 64位

Web服务器：Tomcat 8.5或9

## 前提条件 {#section_dp2_hk2_kgb .section}

-   已从阿里云SSL证书服务控制台下载Tomcat服务器证书（包含PFX格式证书文件和TXT格式密码文件）。
-   您申请SSL证书时绑定的域名已完成DNS解析、实现了该域名指向您Tomcat服务器的IP地址。

    域名解析设置完成后执行ping www.yourdomain.com命令，如果返回了您所设置解析的主机IP地址，说明解析成功。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/105838/155016900038731_zh-CN.png)


## 操作步骤 {#section_b2p_3k2_kgb .section}

1.  解压Tomcat证书。

    **说明：** 每次下载证书都会产生新的密码，该密码仅匹配本次下载的证书。如果需要更新证书文件，同时也要更新匹配的密码。

2.  在**Tomcat**安装目录下新建**cert**目录，将下载的证书和密码文件拷贝到**cert**目录下。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/105838/155016900038747_zh-CN.png)

3.  打开Tomcat/conf/server.xml，在server.xml文件中找到以下参数并进行修改。

    ```
    <Connector port="8080" protocol="HTTP/1.1"
                   connectionTimeout="20000"
                   redirectPort="8443" />
        
     #找到以上参数，去掉<!- - 和 - ->这对注释符并修改为如下参数：
     <Connector port="80" protocol="HTTP/1.1"
     #将Connector port修改为80。
                   connectionTimeout="20000"
                   redirectPort="443" />   
                   #将redirectPort修改为SSL默认端口443，让HTTP访问自动跳转为HTTPS访问。
    ```

    ```
    
    
        <Connector port="8443"
              protocol="org.apache.coyote.http11.Http11NioProtocol"
              maxThreads="150"
              SSLEnabled="true">
            <SSLHostConfig>
                <Certificate       certificateKeystoreFile="cert/keystore.pfx"
                 certificateKeystorePassword="XXXXXXX"
                             certificateKeystoreType="PKCS12" />
    
        #找到以上参数，去掉<!- - 和 - ->这对注释符并修改为如下参数：
        <Connector port="443"
        #将Tomcat中默认的HTTPS端口Connector port 8443修改为443。8443端口不可通过域名直接访问、需要在域名后加上端口号；443端口是HTTPS的默认端口，可通过域名直接访问，无需在域名后加端口号。
              protocol="org.apache.coyote.http11.Http11NioProtocol"
              #server.xml文件中Connector port有两种运行模式（NIO和APR），请选择NIO模式（也就是protocol="org.apache.coyote.http11.Http11NioProtocol"）这一段进行配置。
              maxThreads="150"
              SSLEnabled="true">
            <SSLHostConfig>
                <Certificate       certificateKeystoreFile="/usr/local/tomcat/cert/证书域名.pfx"
                 #此处certificateKeystoreFile代表证书文件的路径，请用您证书的路径+文件名替换证书域名.pfx，例如：certificateKeystoreFile="/usr/local/tomcat/cert/abc.com.pfx"
                 certificateKeystorePassword="证书密码"
                 #此处certificateKeystorePassword为SSL证书的密码，请用您证书密码文件pfx-password.txt中的密码替换，例如：certificateKeystorePassword="bMNML1Df"
                 certificateKeystoreType="PKCS12" />
                 #证书类型为PFX格式时，certificateKeystoreType修改为PKCS12。
        
    ```

    ```
    <Connector port="8009" protocol="AJP/1.3" redirectPort="8443" />
        
    #找到以上参数，去掉<!- - 和 - ->这对注释符并修改为如下参数：
    <Connector port="8009" protocol="AJP/1.3" redirectPort="443" />
     #将redirectPort修改为443，让HTTP访问自动跳转为HTTPS访问。
    ```

4.  保存server.xml文件配置。
5.  重启Tomcat服务。
    1.  在Tomcat下的bin目录中执行./shutdown.sh关闭Tomcat服务。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/105838/155016900038751_zh-CN.png)

    2.  在Tomcat下的bin目录中执行./startup.sh开启Tomcat服务。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/105838/155016900038752_zh-CN.png)


## 后续操作 {#section_e3j_jk2_kgb .section}

Tomcat服务重启成功后，您可在浏览器中输入您SSL证书绑定的域名https://www.YourDomainName.com验证证书安装结果。浏览器地址栏显示绿色的小锁标识说明证书安装成功。

