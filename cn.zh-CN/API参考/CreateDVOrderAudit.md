# CreateDVOrderAudit {#doc_api_cas_CreateDVOrderAudit .reference}

提交DV订单。

调用本接口实现DV订单提交。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=cas&api=CreateDVOrderAudit&type=RPC&version=2018-07-13)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateDVOrderAudit|系统规定参数。取值：CreateDVOrderAudit。

 |
|City|String|是|hangzhou| 

 指定城市。建议用拼音。

 |
|Domain|String|是|\*.com|指定域名。如果有多个域名，要用半角逗号分开。

 |
|DomainVerifyType|String|是|DNS|指定域名授权验证类型。取值为FILE或DNS，注意是大写。

 |
|Email|String|是|\*@xx.com| 

 指定用户邮箱。

 |
|InstanceId|String|是|cas-cn-1111| 

 指定证书实例名称。

 |
|Mobile|String|是|12345XXXXXX| 

 指定手机号码。

 |
|Province|String|是|zhejiang| 

 指定省份。建议用拼音。

 |
|Username|String|是|AXXX| 

 指定用户姓名。

 |
|Lang|String|否|zh|指定请求和接收消息的语言类型。

 |
|SourceIp|String|否|1.2.3.4|指定请求的来源IP地址。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|5D97F21E-2B95-4EA9-8A9B-2759E04A5B4C|返回结果的请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=CreateDVOrderAudit
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateDVOrderAudit>
	  <RequestId>5D97F21E-2B95-4EA9-8A9B-2759E04A5B4C</RequestId>
</CreateDVOrderAudit>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"5D97F21E-2B95-4EA9-8A9B-2759E04A5B4C"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/cas)查看更多错误码。

