# CreateUserCertificate {#doc_api_cas_CreateUserCertificate .reference}

添加证书。

 **调用本接口添加证书。** 

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=cas&api=CreateUserCertificate&type=RPC&version=2018-07-13)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateUserCertificate|系统规定参数。取值：CreateUserCertificate。

 |
|Cert|String|是|---BEGIN CERTIFICATE----- MIIF...... -----END CERTIFICATE-----|指定证书内容。要使用PEM编码格式。

 |
|Key|String|是|---BEGIN RSA PRIVATE KEY----- MII.... -----END RSA PRIVATE KEY-----|指定证书私钥内容。要使用PEM编码格式。

 |
|Name|String|是|auto-test-AXX|自定义证书名称。一个用户下的证书名称不能重复。

 |
|Lang|String|否|ZH|指定请求和接收消息的语言类型。

 |
|SourceIp|String|否|1.2.3.4|指定请求的来源IP地址。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|CertId|Long|321|证书ID。

 |
|RequestId|String|BDXXX|请求消息的ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=CreateUserCertificate
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateUserCertificate>
	  <RequestId>15BE9F82-71D1-4A83-9002-381C0BE2A889</RequestId>
	  <HostId>cas.aliyuncs.com</HostId>
	  <Code>200</Code>
    </CreateUserCertificate>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"15BE9F82-71D1-4A83-9002-381C0BE2A889",
	"HostId":"cas.aliyuncs.com",
	"Code":"200"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/cas)查看更多错误码。

