# 开启全站HTTPS服务 {#concept_1340451 .concept}

本文档介绍如何开启全站HTTPS服务功能。

开启全站HTTPS服务流程如下：

![0](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1069028/156474059052935_zh-CN.png)

## 步骤一：添加HTTPS站点 {#section_4gp_uam_idh .section}

您可以参考以下步骤添加站点：

1.  登录阿里云[SSL证书控制台](https://yundunnext.console.aliyun.com/?p=cas#/overview/cn-hangzhou)。
2.  您可以参考以下三种方法进入添加站点页面。
    -   **通过全站HTTPS** 
        1.  在SSL证书控制台，单击**全站HTTPS**，进入**全站HTTPS**页面。

            ![1](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1069028/156474059052946_zh-CN.png)

        2.  单击**添加站点**。

            ![2](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1069028/156474059052947_zh-CN.png)

    -   **通过已签发证书的部署操作** 

        在SSL证书控制台已签发证书列表，单击**证书**右侧**操作**下的**部署**，并选择**全站HTTPS**。

        ![3](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1069028/156474059152948_zh-CN.png)

    -   **通过已签发证书的下载操作** 
        1.  在SSL证书控制台已签发证书列表，单击**证书**右侧**操作**下的**下载**。
        2.  在**证书下载**页面，单击**全站HTTPS服务**模块的**免费试用**。

            ![4](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1069028/156474059152951_zh-CN.png)

3.  在添加站点页面，添加站点域名。

    在**站点域名**页签，阅读**使用条款**并勾选**我已仔细阅读并同意该服务条款**，然后输入待添加站点域名。

    ![5](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1069028/156474059152953_zh-CN.png)

4.  单击右下角的**下一步**，进入**站点IP**页签。
5.  在**站点IP**页，配置网站源站地址。

    支持**IPv4**和**域名**两种源站地址类型。系统会自动检测您源站的域名解析情况，给出默认选择。您可以根据实际情况调整。

    **说明：** 最多可以填写三个IPv4地址，系统会采用RR策略回源。

    ![6](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1069028/156474059152958_zh-CN.png)

6.  单击**下一步**，进行[步骤二：设置SSL选项](#section_q2r_w8m_qg2)。

## 步骤二：设置SSL选项 {#section_q2r_w8m_qg2 .section}

您可以参考以下步骤进行安全配置：

1.  在**SSL选项**页签，单击对应功能按钮，开启/关闭功能。

    SSL选项分为以下两种安全配置：

    -   **强制HTTPS访问**：开启该功能，来自客户端（浏览器）的每一个HTTP协议的URL地址请求，都将被301重定向等效的HTTPS协议的URL地址，同时支持HSTS。即浏览器端的每个HTTP请求都会被跳转成HTTPS请求。
    -   **TLS/SSL卸载**：开启该功能，来自客户端（浏览器）的每一个HTTP协议的请求，都将被重定向到等效HTTPS协议的URL地址。即阿里云服务器使用HTTPS协议访问您的源站。
    ![7](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1069028/156474059252961_zh-CN.png)

2.  单击**下一步**，进入[步骤三：配置证书](#section_sw3_0yt_51w)页签。

## 步骤三：配置证书 {#section_sw3_0yt_51w .section}

如果添加的站点域名在SSL证书系统申请过证书且有效期大于90天，您可以选择已有证书。您也可以根据需要重新申请证书。

1.  在**配置证书**页签，选择或申请证书文件。

    ![8](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1069028/156474059252965_zh-CN.png)

2.  单击**确认**，完成站点配置。

    站点配置完后，会在**全站HTTPS**页的站点列表中呈现，然后进行[步骤四：添加DNS解析记录](#section_hbw_n1y_ohg)。


## 步骤四：添加DNS解析记录 {#section_hbw_n1y_ohg .section}

将已添加站点的DNS记录解析到该服务的CNAME域名。

1.  在**全站HTTPS**页的站点列表中，查看已添加站点的**证书状态**。

    当**证书状态**是正常后，单击右侧**操作**栏下**检测** 。

    ![9](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1069028/156474059252972_zh-CN.png)

2.  在**接入检测**页面，按照窗口给出的提示信息到您的DNS管理系统添加一条CNAME解析记录，完成您站点的接入配置。

    添加解析记录请参考[修改DNS解析记录](cn.zh-CN/用户指南/全站HTTPS/修改DNS解析记录.md#)。

    ![10](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1069028/156474059252977_zh-CN.png)

    当站点**接入状态**是正常时，您的网站已经接入生效了，即开启了全站HTTPS服务。

    ![11](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1069028/156474059252979_zh-CN.png)

    **说明：** 

    -   仅当站点的**接入状态**是异常，即未接入到全站HTTPS服务的站点才可以删除。
    -   已添加的站点支持修改**源站地址**、**强制HTTPS访问**功能、**TLS/SSL卸载**功能和**证书**配置。

## 后续操作 {#section_qec_cfy_1k6 .section}

请参见[使用全站HTTPS服务后源站要做什么调整？](../../../../cn.zh-CN/常见问题/常见问题/使用全站HTTPS服务后源站要做什么调整？.md#)

