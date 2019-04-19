# 谷歌浏览器无法访问安装云盾证书后的IIS服务 {#concept_74807_zh .concept}

本文主要介绍安装云盾证书后，谷歌浏览器无法访问IIS服务的解决方法。

## 问题描述 { .section}

购买云盾证书并部署在Windows系统IIS服务后，通过谷歌浏览器无法访问，其他浏览器可以正常访问。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/123601/155566713938717_zh-CN.png)

## 解决方案 { .section}

通过以下两种方法，解决安装云盾证书的IIS服务谷歌浏览器无法访问的现象。

1.  使用IIS加密套件优化工具。下载 [ITrusIIS.rar](http://alipay-rmsdeploy-image.cn-hangzhou.alipay.aliyun-inc.com/skylark/confluence/alibank/21443f32c0f8577862d48d85f7e15184.rar)压缩包，解压后运行软件，选择**最佳配置** ，单击 **应用**，重启服务器生效配置。
2.  加密套件的注册表文件，下载 [IIS8.rar](http://alipay-rmsdeploy-image.cn-hangzhou.alipay.aliyun-inc.com/skylark/confluence/alibank/f8f6753e2e4de66a1961879a3b862d56.rar)压缩包，解压后运行软件，重启服务器生效配置。

## 相关文档 { .section}

-   [KB72475](http://kb.aliyun-inc.com/kb/72475/cn/zh-cn) 谷歌浏览器无法识别IIS绑定的证书

## 适用于 { .section}

-   云服务器ECS
-   云盾

