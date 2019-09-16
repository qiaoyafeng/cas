# DescribeDVOrderResult {#doc_api_cas_DescribeDVOrderResult .reference}

调用DescribeDVOrderResult接口查询DV订单的详细信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=cas&api=DescribeDVOrderResult&type=RPC&version=2018-07-13)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeDVOrderResult|系统规定参数。取值：DescribeDVOrderResult。

 |
|InstanceId|String|是|cas-cn-\*\*\*|指定证书实例。

 |
|Lang|String|否|zh|指定请求和接收消息的语言类型。

 -   **zh**：中文
-   **en**：英文

 |
|SourceIp|String|否|1.2.3.4|指定请求的来源IP地址。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Certificate|String|-----BEGIN CERTIFICATE----- MIIF...... -----END CERTIFICATE-----|证书内容，为PEM编码格式。

 **说明：** 仅在**OrderStatus**为**issued**时，该参数出现。

 |
|CheckName|String|\_xx.aliyundns20181016.certificatestests.com|授权验证名称。

 **说明：** 仅在**OrderStatus**为**checking**时，该参数出现。

 |
|CheckType|String|DNS|授权验证类型。取值为DNS或者FILE。

 **说明：** 

-   仅在**OrderStatus**为**checking**时，该参数出现。
-   当CheckType为DNS时，**CheckName**是主机值，**CheckValue**是记录值。
-   当CheckType为FILE时，**CheckName**为不包含协议的URL地址，**CheckValue**为文件中的内容。

 |
|CheckValue|String|201810150000000k09v6d4........|授权验证值。

 **说明：** 仅在**OrderStatus**为**checking**时，该参数出现。

 |
|OrderStatus|String|checking|订单状态。

 取值选项：

 -   checking：审核中
-   issued：已签发
-   check\_fail：审核失败

 |
|PrivateKey|String|----BEGIN RSA PRIVATE KEY----- MII.... -----END RSA PRIVATE KEY-----|证书私钥内容，为PEM编码格式。

 **说明：** 仅在**OrderStatus**为**issued**时，该参数出现。

 |
|RequestId|String|EECA10D5-BD0....|返回结果的请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeDVOrderResult
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeDVOrderResult>
	  <CheckValue>201810150000000k09v6d49sb26ys9whgpjp7cdavl6ik8a1nfct9mnep68n0h31</CheckValue>
	  <OrderStatus>checking</OrderStatus>
	  <CheckType>DNS</CheckType>
	  <RequestId>EECA10D5-BD0F-4EF1-B3EA-B4578E5C6F8E</RequestId>
	  <CheckName>***.aliyundns20181016.certificatestests.com</CheckName>
</DescribeDVOrderResult>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"CheckValue":"201810150000000k09v6d49sb26ys9whgpjp7cdavl6ik8a1nfct9mnep68n0h31",
	"OrderStatus":"checking",
	"CheckType":"DNS",
	"RequestId":"EECA10D5-BD0F-4EF1-B3EA-B4578E5C6F8E",
	"CheckName":"***.aliyundns20181016.certificatestests.com"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/cas)查看更多错误码。

