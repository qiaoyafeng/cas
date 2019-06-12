# Symantec与DigitalCert合并相关证书签发时效受影响 {#concept_ejf_rcw_ydb .concept}

Digicert于2017年12月1日，完成对Symantec证书服务的并购。此后，所有新申请Symantec/GeoTrust品牌证书，切换到Digicert+Symantec交叉认证PKI体系下签发。新根证书同时拥有两个根CA的兼容性，即兼容性更高。阿里云平台的Symantec/GeoTrust已签发的旧根，也会按计划更新到新交叉根下。

从2017年12月1日到2017年12月20日，预计在此期间，OV/EV证书签发时间需要5~10个工作日；DV证书的签发，需要1~4个工作日。如果签发失败，建议您重新提交后等待鉴证系统签发队列签发。

Symantec免费证书预计要在本月底才能逐步恢复。

给您带来的不便之处，万分抱歉！在此期，如需紧急签发证书，建议更换为GlobalSign证书品牌，提工单要求加速签发GlobalSign证书。

