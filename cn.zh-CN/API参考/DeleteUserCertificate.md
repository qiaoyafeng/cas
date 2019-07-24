# DeleteUserCertificate {#doc_api_cas_DeleteUserCertificate .reference}

删除用户证书。

调用本接口删除用户的证书文件。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=cas&api=DeleteUserCertificate&type=RPC&version=2018-07-13)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteUserCertificate|系统规定参数。取值：DeleteUserCertificate。

 |
|CertId|Long|是|123|指定证书ID。调用**CreateUserCertificate**接口添加证书返回结果中的**CertId**。

 |
|Lang|String|否|ZH|指定请求和接收消息的语言类型。

 |
|SourceIp|String|否|1.2.3.4|指定请求的来源IP地址。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|BDXX|返回请求消息的ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DeleteUserCertificate
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteUserCertificate>
	  <RequestId>BDB81BA2-E1F5-4D08-A2DD-4BE2BF44C90E</RequestId>
</DeleteUserCertificate>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"BDB81BA2-E1F5-4D08-A2DD-4BE2BF44C90E"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/cas)查看更多错误码。

