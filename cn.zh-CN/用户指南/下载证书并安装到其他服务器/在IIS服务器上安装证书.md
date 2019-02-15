# 在IIS服务器上安装证书 {#concept_ntq_f1x_yfb .concept}

您可将下载的阿里云SSL证书安装到IIS服务器上，使您的IIS服务器支持HTTPS安全访问。

## 前提条件 {#section_xdh_4qb_1gb .section}

申请证书时需要选择**系统自动创建CSR**。

申请证书时如果选择**手动创建CSR**，则不会生成证书文件。您需要选择**其他服务器**下载.crt证书文件后，使用openssl命令将.crt文件的证书转换成.pfx格式。

## 操作指南 {#section_ydh_4qb_1gb .section}

1.  登录阿里云[SSL证书控制台](https://yundunnext.console.aliyun.com/?p=casnext#/overview/cn-hangzhou)。
2.  在SSL证书页面定位到需要下载的证书并单击证书卡片右下角的**下载**打开**证书下载**对话框。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/66242/155020010833499_zh-CN.png)

3.  在**证书下载**对话框中定位到IIS服务器，并单击右侧**操作**栏的**下载**将IIS版证书压缩包下载到本地。
4.  解压IIS证书。您将看到文件中有一个证书文件（以.pfx为后缀或文件类型）和一个秘钥文件（以.txt为后缀或文件类型）。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/66003/155020010833691_zh-CN.png)

    **说明：** 每次下载证书都会产生新的密码，该密码仅匹配本次下载的证书。如果需要更新证书文件，同时也要更新匹配的密码文件。

5.  在**控制台**操作对话框中导入您下载的IIS证书文件。
    1.  单击**开始** \> **运行** \> **MMC**打开控制台。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/66003/155020010833701_zh-CN.png)

    2.  单击**文件** \> **添加/删除管理单元**打开**添加/删除管理单元**对话框。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/66003/155020010833702_zh-CN.png)

    3.  在**可用的管理单元**中单击**证书** \> **添加** \> **计算机账户** \> **本地计算机（运行此控制台的计算机）** \> **完成**。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/66003/155020010833703_zh-CN.png)

    4.  在控制台左侧导航栏单击**控制台根节点**下的**证书**打开证书树形列表。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/66003/155020010833705_zh-CN.png)

    5.  单击**个人** \> **证书** \> **** \> **所有任务** \> **导入**打开**证书导入向导**对话框。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/66003/155020010933706_zh-CN.png)

    6.  单击**浏览**导入下载的PFX格式证书文件。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/66003/155020011833837_zh-CN.png)

        **说明：** 在导入证书文件时，**文件名**右侧文件类型下拉菜单中请选择**所有文件**类型。

    7.  输入证书秘钥文件里的密码。

        您可在下载的IIS证书文件中打开pfx-password .txt文件查看证书密码。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/66003/155020011833838_zh-CN.png)

    8.  勾选**根据证书类型，自动选择证书存储**并单击**下一步**完成证书的导入。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/66003/155020011833839_zh-CN.png)

6.  分配服务器证书。
    1.  打开IIS8.0 管理器面板，定位到待部署证书的站点，单击**绑定**。
    2.  在**网站绑定**对话框中单击**添加** \> **选择https类型** \> **端口选择443** \> **导入的IIS证书名称** \> **确定**。

        **说明：** SSL 缺省端口为 443 端口，请不要修改。 如果您使用其他端口如：8443，则访问网站时必须输入`https://www.domain.com:8443`\)。


