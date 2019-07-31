# 使用全站HTTPS服务后源站要做什么调整？ {#concept_1357845 .concept}

站点使用全站HTTPS服务后，源站需要调整网页中引用资源的链接格式和获取客户端IP的请求源。

## 修改网页中的资源链接格式 {#section_qd5_d3u_0m2 .section}

在HTTPS页面中引用HTTP资源，一般叫做混合内容（Mixed Content\) ，Firefox和Chrome等浏览器会提示这类页面不安全。

如果您网页中存在用HTTP协议引用资源，建议您按照如下方式调整。

如果一个网页引用了`abc.com`中的一个资源，原来引用方式如下。

``` {#screen_9i6_n8x_ilg .screen}
<img src="http://abc.com/images/a.png" />
```

建议您修改为以下引用方式。

``` {#screen_vs8_chk_plo .screen}
<img src="//abc.com/images/a.png" />
```

## 修改获取客户端IP的请求源 {#section_54j_3sz_j1n .section}

如果您的程序或日志中有获取访问者IP地址的地方，需要修改为从请求源参数`X-Forwarded-For`中获取IP。

**说明：** 如果您没有修改请求源，获取到的IP将是全站HTTPS服务的访问IP。

