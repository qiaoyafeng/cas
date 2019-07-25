# DescribeUserCertificateList {#doc_api_cas_DescribeUserCertificateList .reference}

查询证书列表。

调用本接口查询证书列表信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=cas&api=DescribeUserCertificateList&type=RPC&version=2018-07-13)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeUserCertificateList|系统规定参数。取值：DescribeUserCertificateList。

 |
|CurrentPage|Integer|是|1|指定当前页码。默认取值为1。

 |
|ShowSize|Integer|是|50|指定每页显示多少条记录。默认取值为50。

 |
|Lang|String|否|ZH|请求和接收消息的语言类型。

 |
|SourceIp|String|否|1.2.3.4|请求的来源IP地址。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|CertificateList| | |证书显示列表的数组结构。

 |
|buyInAliyun|Boolean|true|是否在阿里云购买。

 |
|city|String|hongzhou|证书组织所在城市。

 |
|common|String|\*.com|证书的CN属性。

 |
|country|String|CN|证书组织所在国家。

 |
|endDate|String|2027-10-14|证书到期日期。

 |
|expired|Boolean|false|是否过期。

 |
|fingerprint|String|6DEB816DE48D5E7DE6D7FE92A6B620B13DD3266B|证书指纹。

 |
|id|Long|763762|证书ID。

 |
|issuer|String|Alibaba|证书颁发机构。

 |
|name|String|auto-test-23673|证书名称。

 |
|orgName|String|Alibaba|证书所有组织名称。

 |
|province|String|Zhejiang|证书组织所在省。

 |
|sans|String|\*.com|证书中sans部分。

 |
|startDate|String|2017-10-16|证书签发日期。

 |
|CurrentPage|Integer|1|当前页码。

 |
|RequestId|String|123|请求消息的ID。

 |
|ShowSize|Integer|50|每页显示多少条记录。

 |
|TotalCount|Integer|60|总记录数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeUserCertificateList
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeUserCertificateList>
	  <TotalCount>736</TotalCount>
	  <RequestId>E865F6AD-0294-4A24-A58B-DAC6BE2BDD20</RequestId>
	  <CertificateList>
		    <startDate>2017-10-16</startDate>
		    <expired>false</expired>
		    <common>*.jinxibei.com</common>
		    <buyInAliyun>true</buyInAliyun>
		    <endDate>2027-10-14</endDate>
		    <orgName>Alibaba</orgName>
		    <city>Hangzhou</city>
		    <country>CN</country>
		    <id>763762</id>
		    <fingerprint>6DEB816DE48D5E7DE6D7FE92A6B620B13DD3266B</fingerprint>
		    <issuer>Alibaba</issuer>
		    <name>auto-test-23673</name>
		    <sans>*.jinxibei.com</sans>
		    <province>Zhejiang</province>
	  </CertificateList>
	  <ShowSize>1</ShowSize>
	  <CurrentPage>50</CurrentPage>
    </DescribeUserCertificateList>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"TotalCount":736,
	"RequestId":"E865F6AD-0294-4A24-A58B-DAC6BE2BDD20",
	"ShowSize":1,
	"CertificateList":[
		{
			"startDate":"2017-10-16",
			"expired":false,
			"common":"*.jinxibei.com",
			"buyInAliyun":true,
			"endDate":"2027-10-14",
			"orgName":"Alibaba",
			"city":"Hangzhou",
			"country":"CN",
			"id":763762,
			"fingerprint":"6DEB816DE48D5E7DE6D7FE92A6B620B13DD3266B",
			"issuer":"Alibaba",
			"name":"auto-test-23673",
			"sans":"*.jinxibei.com",
			"province":"Zhejiang"
		}
	],
	"CurrentPage":50
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/cas)查看更多错误码。

