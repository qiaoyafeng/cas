# Symantec SSL数字证书升级重签提示 {#concept_f2n_3bh_d2b .concept}

预计2018年10月中旬，Google Chrome浏览器将不再信任Symantec及GeoTrust品牌的部分数字证书，为此Symantec针对Chrome浏览器发布了一项根证书升级计划。为了避免与Google Chrome浏览器相关的任何兼容性问题，建议您尽快参考本文档中的说明替换您的Symantec品牌数字证书。

## 受影响范围 {#section_ycg_2ch_d2b .section}

属于以下时间范围内的Symantec品牌数字证书将受本次Symantec根证书升级计划影响，需要在指定时间前替换现有数字证书。

**说明：** 根据Symantec官方消息，自2017年12月1日起Symantec已经启用新的证书签发体系，在该时间点之后签发的数字证书完全符合谷歌的建议，将不再存在兼容性问题。

-   签发时间在2016年6月1日前且到期时间在2018年3月18日后的数字证书：您需要在2018年3月18日前完成证书替换，并且将替换后的证书重新部署。
-   签发时间在2016年6月1日后的数字证书：您需要在2018年9月13日前完成证书替换，并且将替换后的证书重新部署。

**说明：** 属于以下时间范围的Symantec数字证书不受本次根证书升级计划影响：

-   2016年6月1日前签发且2018年3月前到期的数字证书
-   2016年6月1日后签发且2018年9月前到期的数字证书

## 证书替换服务 {#section_fhl_xgh_d2b .section}

自2018年6月起，阿里云证书服务已针对受影响范围内的Symantec数字证书启动证书的替换升级服务。

-   对于受影响范围内的OV/EV类型的数字证书，CA认证中心的审核人员将通过电话与您联系，经确认后将重新为您签发新的数字证书。

    **说明：** 如果您在[云盾证书服务管理控制台](https://yundun.console.aliyun.com/?&p=cas#/cas/home)中发现处于审核中状态的OV/EV类型证书订单，请您耐心等待CA中心审核人员的通知。

-   对于受影响范围内的DV类型的数字证书，阿里云工作人员将为您提交证书重签申请，您需要在[云盾证书服务管理控制台](https://yundun.console.aliyun.com/?&p=cas#/cas/home)中根据进度提示完成域名验证操作。

    **说明：** 如果您原先的DV型数字证书订单符合以下条件，系统将尝试自动添加DNS解析记录帮助您完成域名验证：

    -   通过DNS方式完成域名验证
    -   证书绑定的域名由云解析服务管理
    -   已授权证书服务系统自动添加DNS解析记录
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/14803/6322_zh-CN.png)


![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/14803/6321_zh-CN.png)

