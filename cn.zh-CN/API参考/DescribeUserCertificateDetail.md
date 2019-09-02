# DescribeUserCertificateDetail {#doc_api_cas_DescribeUserCertificateDetail .reference}

查询单个证书的详细信息。

调用本接口查询单个证书的详细信息，包括证书名称、证书内容、证书私钥、签发机构、证书有效期和证书指纹等信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=cas&api=DescribeUserCertificateDetail&type=RPC&version=2018-07-13)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeUserCertificateDetail|系统规定参数。取值：DescribeUserCertificateDetail。

 |
|CertId|Long|是|12345|证书ID。调用**CreateUserCertificate**接口添加证书返回结果中的**CertId**。

 |
|Lang|String|否|zh|请求和接收消息的语言类型。

 |
|SourceIp|String|否|1.2.3.4|请求的来源IP地址。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|BuyInAliyun|Boolean|true|是否在阿里云购买。

 |
|Cert|String|-----BEGIN CERTIFICATE----- MIIF...... -----END CERTIFICATE-----|证书内容，为PEM编码格式。

 |
|City|String|hangzhou|证书组织所在城市。

 |
|Common|String|\*.com|证书的CN属性。

 |
|Country|String|Chinese|证书组织所在国家。

 |
|EndDate|String|2020-07-13|证书到期日期。

 |
|Expired|Boolean|false|证书是否过期。

 |
|Fingerprint|String|6DEB816DE48D5E7DE|证书指纹。

 |
|Id|Long|1|证书ID。

 |
|Issuer|String|Alibaba|证书颁发机构。

 |
|Key|String|-----BEGIN RSA PRIVATE KEY----- MII.... -----END RSA PRIVATE KEY-----|证书私钥内容，为PEM编码格式。

 |
|Name|String|cert-1|证书名称。

 |
|OrgName|String|Alibaba|证书所有组织名称。

 |
|Province|String|zhejiang|证书组织所在省。

 |
|RequestId|String|123|请求消息的ID。

 |
|Sans|String|\*.com|证书中sans部分。

 |
|StartDate|String|2018-07-13|证书签发日期。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeUserCertificateDetail
&CertId=12345
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeUserCertificateDetail>
	  <RequestId>08F45EA0-66A7-4504-9B31-3589F5CE308D</RequestId>
</DescribeUserCertificateDetail>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"08F45EA0-66A7-4504-9B31-3589F5CE308D"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/cas)查看更多错误码。

