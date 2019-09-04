# DescribeOrderInstanceList {#doc_api_cas_DescribeOrderInstanceList .reference}

查询证书订单实例列表。

调用DescribeOrderInstanceList接口，可查询证书订单的实例列表。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=cas&api=DescribeOrderInstanceList&type=RPC&version=2018-07-13)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeOrderInstanceList|系统规定参数。取值：DescribeOrderInstanceList。

 |
|StartIndex|Integer|是|1|开始索引号。指定从该索引号开始查询证书订单实例信息。

 |
|Lang|String|否|zh|请求字段的语言种类。

 |
|SourceIp|String|否|1.2.3.4|指定访问源IP地址。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|OrderList| | |返回的订单实例列表。

 |
|CertType|String|\*\*\* DV SSL|证书的类型。

 |
|Id|Long|1111100000|返回的数据源ID。

 |
|InstanceId|String|cas-cn-v\*\*\*|证书实例的ID。

 |
|Source|String|\*\*\*.test.\*\*\*|证书订单的请求源。

 |
|Status|String|Paid|证书订单的状态。

 订单包括以下状态：

 -   **Paid**：订单已支付
-   **Verifying**：证书审核中
-   **Verification Failed**：证书验证失败
-   **Pending Verification**：证书待验证
-   **Pending Verification for Revocation**：证书吊销待验证
-   **Verifying Revocation**：证书吊销审核中
-   **Issued**：证书已签发

 |
|RequestId|String|EF69F215-B307-4A23-8890-D8171D3A51D3|返回结果的请求ID。

 |
|TotalCount|Integer|0|返回订单实例的总数量。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeOrderInstanceList
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeOrderInstanceList>
	  <TotalCount>0</TotalCount>
	  <RequestId>FACBE1FA-9316-4A58-AA95-B88E40B93A78</RequestId>
</DescribeOrderInstanceList>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"TotalCount":0,
	"OrderList":[],
	"RequestId":"EF69F215-B307-4A23-8890-D8171D3A51D3"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/cas)查看更多错误码。

