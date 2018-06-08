# 浏览器是如何检查SSL证书是否工作正常的? {#concept_tl3_qvv_ydb .concept}

SSL数字证书必须由浏览器中“受信任的根证书颁发机构”在验证服务器身份后颁发，具有网站身份验证和加密传输双重功能。

配置完成SSL数字证书后，如果您能使用https:// 方式访问您的网站，则表示网站已经部署了SSL证书。

## 操作步骤 {#section_vcb_vvv_ydb .section}

1.  在浏览器地址栏中，输入https:// + 您的数字证书绑定的域名（如 https://www.aliyun.com ）。
2.  按回车键（Enter）通过HTTPS方式访问您的网站。
3.  网站页面能正常访问，且浏览器地址栏中显示安全锁标志，说明您的SSL数字证书已部署成功。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13607/4283_zh-CN.png)


