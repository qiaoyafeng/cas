# CreateDVOrderAudit {#doc_api_cas_CreateDVOrderAudit .reference}

Submit a domain validated \(DV\) certificate order.

You can call this operation to submit a DV certificate order.

## Debugging {#api_explorer .section}

[Alibaba Cloud provides OpenAPI Explorer to simplify API usage. You can use OpenAPI Explorer to search for APIs, call APIs, and dynamically generate SDK example code.](https://api.aliyun.com/#product=cas&api=CreateDVOrderAudit&type=RPC&version=2018-07-13)

## Request parameters {#parameters .section}

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateDVOrderAudit|The operation that you want to perform. Set this value to CreateDVOrderAudit.

 |
|City|String|Yes|hangzhou| 

 The city where the organization that purchases the certificate is located. We recommend that you set this parameter in Pinyin.

 |
|Domain|String|Yes|\*.com|The domain name. If multiple domain names exist, separate them with commas \(,\).

 |
|DomainVerifyType|String|Yes|DNS|The verification type of the domain name. The value is FILE or DNS. Note that the value is in uppercase.

 |
|Email|String|Yes|\*@xx.com| 

 The contact email.

 |
|InstanceId|String|Yes|cas-cn-1111| 

 The ID of the DV certificate.

 |
|Mobile|String|Yes|12345XXXXXX| 

 The contact phone number.

 |
|Province|String|Yes|zhejiang| 

 The province where the organization from which you purchase the certificate is located. We recommend that you set this parameter in Pinyin.

 |
|Username|String|Yes|AXXX| 

 The name of the contact.

 |
|Lang|String|No|ZH|The language type of the request and response.

 |
|SourceIp|String|No|1.2.3.4|The source IP address of the request.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|None|The ID of the request. \[DO NOT TRANSLATE\] \[DO NOT TRANSLATE\]

 |

## Examples {#demo .section}

Sample request

``` {#request_demo}

http(s)://[Endpoint]/? Action=CreateDVOrderAudit
&<Common request parameters>

```

Sample success response

`XML` format

``` {#xml_return_success_demo}
<CreateDVOrderAudit>
	  <RequestId>5D97F21E-2B95-4EA9-8A9B-2759E04A5B4C</RequestId>
</CreateDVOrderAudit>
```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"5D97F21E-2B95-4EA9-8A9B-2759E04A5B4C"
}
```

## Error codes { .section}

