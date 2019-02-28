# chrome浏览器提示错误 {#concept_wdh_rrp_ydb .concept}

2016年11月左右，陆续接到用户反馈chrome 53版本，qq浏览器9.5.1版本（内置chrome53内核）在访问HTTPS网站时，出现`NET::ERR_CERTIFICATE_TRANSPARENCY_REQUIRED 错误`的错误。

该问题为Google Chrome 53版本浏览器的BUG，导致显示HTTPS网站异常，如果采用非53版本的chrome浏览器就可避免上述报错。

请参考[Symantec的官网说明](https://www.symantec.com/connect/tr/blogs/chrome-53-bug-affecting-symantec-ssltls-certificates)。

