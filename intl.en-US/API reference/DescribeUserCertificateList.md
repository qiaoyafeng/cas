# DescribeUserCertificateList {#doc_api_cas_DescribeUserCertificateList .reference}

Query the certificate list.

You can call this operation to query the certificate list.

## Debugging {#api_explorer .section}

[Alibaba Cloud provides OpenAPI Explorer to simplify API usage. You can use OpenAPI Explorer to search for APIs, call APIs, and dynamically generate SDK example code.](https://api.aliyun.com/#product=cas&api=DescribeUserCertificateList&type=RPC&version=2018-07-13)

## Request parameters {#parameters .section}

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeUserCertificateList|The operation that you want to perform. Set this value to DescribeUserCertificateList.

 |
|CurrentPage|Integer|Yes|1|The number of the page to return. Default value: 1

 |
|ShowSize|Integer|Yes|50|The number of entries to return on each page. Default value: 50

 |
|Lang|String|No|ZH|The language type of the request and response.

 |
|SourceIp|String|No|1.2.3.4|The source IP address of the request.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|CertificateList| | |The data structure of the certificate list.

 |
|buyInAliyun|Boolean|true|Indicates whether the certificate was purchased from Alibaba Cloud.

 |
|city|String|hongzhou|The city where the organization that purchases the certificate is located.

 |
|common|String|\*.com|The CN attribute of the certificate.

 |
|country|String|CN|The country where the organization that purchases the certificate is located.

 |
|endDate|String|2027-10-14|The expiration date of the certificate.

 |
|expired|Boolean |false|Indicates whether the certificate expired.

 |
|fingerprint|String|6DEB816DE48D5E7DE6D7FE92A6B620B13DD3266B|The certificate fingerprint.

 |
|id|Long|763762|The ID of the certificate.

 |
|issuer|String|DigiCert|The certificate authority.

 |
|name|String|auto-test-23673|The name of the certificate.

 |
|orgName|String|Alibaba|The name of the organization that purchases the certificate.

 |
|province|String|Zhejiang|The province where the organization that purchases the certificate is located.

 |
|sans|String|\*.com|The sans section of the certificate.

 |
|startDate|String|2017-10-16|The issuance date of the certificate.

 |
|CurrentPage|Integer|1|The number of the page to return.

 |
|RequestId|String|123|The ID of the request.

 |
|ShowSize|Integer|50|The number of entries to return on each page.

 |
|TotalCount|Integer|60|The total number of entries.

 |

## Examples {#demo .section}

Sample request

``` {#request_demo}

http(s)://[Endpoint]/? Action=DescribeUserCertificateList
&<Common request parameters>

```

Sample success response

`XML` format

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

`JSON` format

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

## Error codes { .section}

