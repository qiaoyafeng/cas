# 为什么chrome浏览器访问HTTPS域名失败？ {#task_1846841 .task}

## 问题描述 {#section_0tq_yl0_noa .section}

已完成证书导入IIS10 web应用，且已经在SSL设置中启用证书。IIS10 web应用的域名与SSL证书绑定之后，chrome浏览器访问`https://域名`失败。

## 问题原因 {#section_tyl_fuf_j4f .section}

服务器端加密套件以及协议未优化，需要优化更新达到最优配置。

## 解决方法 {#section_lsf_gwv_i57 .section}

可以通过工具一键式操作为IIS服务加密套件及协议设置最优配置。

1.  首先[下载工具](http://www.itrus.cn/soft/ITrusIIS.exe)。
2.  然后将下载的工具导入服务器。
3.  双击`.exe`程序文件，打开工具。
4.  单击**最佳配置** \> **应用**。
5.  重启服务器，使配置生效。

