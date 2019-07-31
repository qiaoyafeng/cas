# 阿里云企业邮箱接入全站HTTPS最佳实践 {#task_1443917 .task}

本文档介绍阿里云企业邮箱接入全站HTTPS服务的最佳实践。

您需要已开通企业邮箱服务，并且设置了自己的企业邮箱域名。设置企业邮箱域名相关内容参见[企业邮箱](https://help.aliyun.com/product/35466.html?spm=5176.8565205.0.0.6a3e1c57p98Iga)。

1.  登录[阿里云企业邮箱控制台](https://alimail.console.aliyun.com/?spm=a2c1d.8251892.aliyun_sidebar.daliyun_sidebar_mail.22805b76VJtXrU)。在左侧导航栏，单击**邮箱列表**。![1](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1069030/156456752653023_zh-CN.png)


2.  单击**业务内容**下的邮箱域名， 查看**基本信息**选项 ，获取**邮箱访问地址**。![2](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1069030/156456752753024_zh-CN.png)


3.  登录阿里云[SSL证书控制台](https://yundunnext.console.aliyun.com/?p=cas#/overview/cn-hangzhou)。
4.  单击**全站HTTPS**，进入**全站HTTPS**页面。![1](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1069028/156456752752946_zh-CN.png)


5.  单击**添加站点**。![2](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1069028/156456752752947_zh-CN.png)


6.  在添加站点页面，输入站点**域名**。 在**站点域名**页签，阅读**使用条款**并勾选**我已仔细阅读并同意该服务条款**，然后输入步骤**3**获取的**邮箱访问地址**。

    ![5](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1069028/156456752752953_zh-CN.png)

7.  单击右下角的**下一步**，在**站点IP**页，手动输入您的源站地址 。 支持**IPv4**和**域名**两种源站地址类型。此时**源站地址**类型选择**域名** 。

    ![6](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1069030/156456752753025_zh-CN.png)

8.  单击**下一步**，进入**SSL选项**，建议全部开启。 SSL选项分为以下两种安全配置：

    -   **强制HTTPS访问**：开启该功能，来自客户端（浏览器）的每一个HTTP协议的URL地址请求，都将被301重定向等效的HTTPS协议的URL地址，同时支持HSTS。即浏览器端的每个HTTP请求都会被跳转成HTTPS请求。
    -   **TLS/SSL卸载**：开启该功能，来自客户端（浏览器）的每一个HTTP协议的请求，都将被重定向到等效HTTPS协议的URL地址。即阿里云服务器使用HTTPS协议访问源站。
    ![7](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1069028/156456752852961_zh-CN.png)

9.  单击**下一步**，配置证书并完成服务接入，具体请参考[开启全站HTTPS服务](cn.zh-CN/用户指南/全站HTTPS/开启全站HTTPS服务.md#)。

