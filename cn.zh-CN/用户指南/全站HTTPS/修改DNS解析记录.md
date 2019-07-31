# 修改DNS解析记录 {#concept_1340452 .concept}

修改域名的DNS解析记录，需要到您的域名DNS服务商系统中进行修改。本文档以阿里云DNS控制台为例，介绍如何修改DNS解析记录。

当您完成全站HTTPS服务的添加站点及配置证书，且站点的**接入状态**和**证书状态**都正常后，控制台会显示您站点专用的**CName**地址。可以使用该CNAME地址更新站点域名的CNAME解析记录值，将网站的Web请求转发至全站HTTPS服务，完成该服务的接入。

## 操作步骤 {#section_6ya_2z4_0f8 .section}

您可以参考以下步骤修改DNS解析记录：

1.  登录[云解析DNS控制台](https://dns.console.aliyun.com/#/dns/domainList)。
2.  在左侧导航栏，单击**域名解析**。选择待操作的域名，单击右侧操作列下的解析设置。
3.  选择待操作的域名，单击右侧**操作**栏下的**解析设置**。

    ![1](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1069029/156455260453001_zh-CN.png)

4.  选择待操作的**主机记录**，单击右侧**操作**栏下的**修改**。

    关于域名的主机记录，以域名`abc.com`为例：

    -   **www**： 用于精确匹配www开头的域名，如`www.abc.com`。
    -   **@**： 用于匹配根域名`abc.com`。
    -   **\***： 用于匹配泛域名，包括根域名和所有子域名，如`blog.abc.com`、`www.abc.com`、`abc.com`等。
    ![2](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1069029/156455260453009_zh-CN.png)

5.  在修改记录对话框中，完成以下操作：

    ![3](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1069029/156455260553010_zh-CN.png)

    -   **记录类型**：修改为CNAME。
    -   **记录值**：修改为已复制的WAF CNAME地址。
    -   其他设置保持不变。TTL值一般建议设置为10分钟。TTL值越大，则DNS记录的同步和更新越慢。
    关于修改解析记录：

    -   对于同一个主机记录，CNAME解析记录值只能填写一个，您需要将其修改为WAF CNAME地址。
    -   不同DNS解析记录类型间存在冲突。例如，对于同一个主机记录，CNAME记录与A记录、MX记录、TXT记录等其他记录互相冲突。在无法直接修改记录类型的情况下，您可以先删除存在冲突的其他记录，再添加一条新的CNAME记录。
    **说明：** 关于DNS解析记录互斥的详细说明，请参考[解析记录冲突的规则](https://help.aliyun.com/document_detail/39787.html)。

6.  单击**确定**，完成DNS配置，等待DNS解析记录生效。
7.  （可选）验证DNS配置。您可以Ping网站域名或使用[17ce](https://www.17ce.com/) 

    **说明：** 由于DNS解析记录生效需要一定时间，如果验证失败，您可以等待10分钟后重新检查。

8.  查看DNS解析状态。
    1.  返回SSL证书控制台，进入**全站HTTPS**服务页面。
    2.  单击站点域名右侧**操作**栏中的**检测**。

        ![10](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1069028/156455260552977_zh-CN.png)


