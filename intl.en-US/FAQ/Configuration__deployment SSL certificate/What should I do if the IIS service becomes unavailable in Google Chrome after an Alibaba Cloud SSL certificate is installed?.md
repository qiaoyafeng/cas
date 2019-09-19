# What should I do if the IIS service becomes unavailable in Google Chrome after an Alibaba Cloud SSL certificate is installed? {#concept_74807_zh .concept}

This topic describes how to access the Internet Information Services \(IIS\) service in Google Chrome after an Alibaba Cloud SSL certificate is installed.

## Symptom {#section_b42_maq_ofc .section}

After the purchased Alibaba Cloud SSL certificate is deployed on a Windows IIS server, you can access the IIS service only in browsers other than Google Chrome.

## Solution {#section_6ey_n8r_zh3 .section}

You can resolve the problem through the following methods:

1.  Use the IIS cipher suite optimization tool. Download the [ITrusIIS.rar](http://alipay-rmsdeploy-image.cn-hangzhou.alipay.aliyun-inc.com/skylark/confluence/alibank/21443f32c0f8577862d48d85f7e15184.rar) package, decompress it, run the software, select **Optimal Configuration**, click **Apply**, and restart the server to apply the configuration.
2.  Encrypt the suite registry, download the [IIS8.rar](http://alipay-rmsdeploy-image.cn-hangzhou.alipay.aliyun-inc.com/skylark/confluence/alibank/f8f6753e2e4de66a1961879a3b862d56.rar) package, decompress it, and restart the server to apply the configuration.

## References {#section_zro_2xy_0zh .section}

-   [KB72475](http://kb.aliyun-inc.com/kb/72475/cn/zh-cn) What should I do if the IIS service becomes unavailable in Google Chrome after an Alibaba Cloud SSL certificate is installed?

## Application scope {#section_jqe_rlq_jmd .section}

-   ECS
-   Alibaba Cloud Security

