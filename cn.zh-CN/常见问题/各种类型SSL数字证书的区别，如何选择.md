# 各种类型SSL数字证书的区别，如何选择 {#concept_bkt_v4p_ydb .concept}

用于网站HTTPS化的SSL数字证书，当前主要分为DV SSL、OV SSL、EV SSL三种类型的证书。

-   DV SSL数字证书部署在服务器上后，用户浏览器访问网站时，展示如下：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13572/4190_zh-CN.png)

-   OV SSL数字证书部署在服务器上后，用户浏览器访问网站时，展示如下：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13572/4191_zh-CN.png)

-   EV SSL数字证书部署在服务器上后，用户浏览器访问网站时，展示如下：

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13572/4192_zh-CN.png)


区别简述如下，

|数字证书|DV SSL|OV SSL|EV SSL|
|----|------|------|------|
|用户建议|个人|组织、企业|大型企业、金融机构|
|公信等级|一般|高|强|
|认证强度|网站真实性|组织及企业真实性|严格认证|
|安全性|一般|中|高|
|可信度|常规|中|高（地址栏绿色）|

云上签发的Symantec证书，在原有OV、EV基础上，推出了增强型OV、增强型EV证书。增强型与专业版OV及高级版EV的区别主要在于，增强型OV、增强EV支持ECC椭圆加密算法。有研究表示160位的椭圆密钥与1024位的RSA密钥安全性相同。

