# DescribeDVOrderResult {#doc_api_cas_DescribeDVOrderResult .reference}

Query a DV certificate order.

You can call this operation to query the information of a DV certificate order.

## Debugging {#api_explorer .section}

[Alibaba Cloud provides OpenAPI Explorer to simplify API usage. You can use OpenAPI Explorer to search for APIs, call APIs, and dynamically generate SDK example code.](https://api.aliyun.com/#product=cas&api=DescribeDVOrderResult&type=RPC&version=2018-07-13)

## Request parameters {#parameters .section}

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeDVOrderResult|The operation that you want to perform. Set this value to DescribeDVOrderResult.

 |
|InstanceId|String|Yes|cas-cn-mpXX|The ID of the DV certificate.

 |
|Lang|String|No|ZH|The language type of the request and response.

 |
|SourceIp|String|No|1.2.3.4|The source IP address of the request.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|Certificate|String|-----BEGIN CERTIFICATE----- MIIF...... -----END CERTIFICATE-----|The certificate content, in PEM format.

 **Note:** This parameter only appears when the **OrderStatus** parameter is **issued**.

 |
|CheckName|String|\_xx.aliyundns20181016.certificatestests.com|The verification item.

 **Note:** This parameter only appears when the **OrderStatus** parameter is **checking**.

 |
|CheckType|String|DNS|The verification type. The value is DNS or FILE.

 **Note:** 

-   This parameter only appears when the **OrderStatus** parameter is **checking**.
-   When the CheckType parameter is DNS, **CheckName** indicates the host name, and **CheckValue** indicates the recorded host name.
-   When the CheckType parameter is FILE, **CheckName** indicates the URL excluding the protocol, and **CheckValue** indicates the content of the file.

 |
|CheckValue|String|201810150000000k09v6d4........|The verification value.

 **Note:** This parameter only appears when the **OrderStatus** parameter is **checking**.

 |
|OrderStatus|String|checking|The order status.

 Valid values:

 -   checking: The certificate is under review.
-   issued: The certificate has been issued.
-   check\_failed: The certificate failed the review.

 |
|PrivateKey|String|----BEGIN RSA PRIVATE KEY----- MII.... -----END RSA PRIVATE KEY-----|The private key of the certificate, in PEM format.

 **Note:** This parameter only appears when the **OrderStatus** parameter is **issued**.

 |
|RequestId|String|EECA10D5-BD0....|The ID of the request.

 |

## Examples {#demo .section}

Sample request

``` {#request_demo}

http(s)://[Endpoint]/? Action=DescribeDVOrderResult
&<Common request parameters>

```

Sample success response

`XML` format

``` {#xml_return_success_demo}
<DescribeDVOrderResult>
	  <CheckValue>201810150000000k09v6d49sb26ys9whgpjp7cdavl6ik8a1nfct9mnep68n0h31</CheckValue>
	  <OrderStatus>checking</OrderStatus>
	  <CheckType>DNS</CheckType>
	  <RequestId>EECA10D5-BD0F-4EF1-B3EA-B4578E5C6F8E</RequestId>
	  <CheckName>_dnsauth.aliyundns20181016.certificatestests.com</CheckName>
</DescribeDVOrderResult>
```

`JSON` format

``` {#json_return_success_demo}
{
	"CheckValue":"201810150000000k09v6d49sb26ys9whgpjp7cdavl6ik8a1nfct9mnep68n0h31",
	"OrderStatus":"checking",
	"CheckType":"DNS",
	"RequestId":"EECA10D5-BD0F-4EF1-B3EA-B4578E5C6F8E",
	"CheckName":"_dnsauth.aliyundns20181016.certificatestests.com"
}
```

## Error codes { .section}

