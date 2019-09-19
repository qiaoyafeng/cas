# Make API requests {#concept_1830029 .concept}

You can send HTTP GET requests to call the SSL Certificates Service API. Before you send a request, specify the request parameters for the specific operation. A response is returned for each request. Requests and responses are encoded by using UTF-8.

## Request syntax {#section_mqz_m07_d8r .section}

The SSL Certificates Service API is in the remote procedure call \(PRC\) style. You can call the SSL Certificates Service API by sending an HTTP GET request.

The request syntax is as follows:

``` {#codeblock_ycp_eml_0he}
https://Endpoint/?Action=xx&Parameters
```

In the request:

-   Endpoint: The endpoint of the SSL Certificates Service API is cas.aliyuncs.com.
-   Action: The operation that you want to perform. For example, you can call the DescribeUserCertificateList operation to query the user asset list.
-   Version: The API version that you want to use. The current version of the SSL Certificates Service API is 2018-07-13.
-   Parameters: The request parameters. The parameters are separated with ampersands \(&\).

    Request parameters consist of common request parameters and API operation-specific parameters. Common request parameters include the API version number and authentication information. For more information about common request parameters, see [Common parameters](reseller.en-US/API reference/Common parameters.md#).


The following example shows how to call the DescribeUserCertificateList operation to query the list of security events:

**Note:** To improve readability, the API request is displayed in the following format:

``` {#codeblock_age_769_yaj}
http(s)://cas.aliyuncs.com/? Action=DescribeUserCertificateList
&Format=xml
&Version=2018-07-13
&Signature=xxxx%xxxx%3D
&SignatureMethod=HMAC-SHA1
&SignatureNonce=15215528852396
&SignatureVersion=1.0
&AccessKeyId=key-test
&TimeStamp=2012-06-01T12:00:00Z
...
```

## API signature {#section_a7t_qt9_r4d .section}

SSL Certificates Service authenticates each API request. Before sending a request by using HTTP or HTTPS, you must add signature information to the request.

For more information about the signature calculation process, see [RPC API signatures](https://www.alibabacloud.com/help/doc-detail/66384.htm).

SSL Certificates Service implements symmetric encryption through an AccessKey pair \(AccessKey ID and AccessKey Secret\) to verify the identity of the request sender. An AccessKey pair is an identity credential issued to Alibaba Cloud accounts and RAM users. It is similar to a user logon password. The AccessKey ID is used to verify the identity of the user. The AccessKey Secret is used to encrypt the signature string and is also used by the server to verify the signature string. The AccessKey Secret must be kept confidential.

When you call an RPC API, you need to add the signature to your request by using the following format:

``` {#codeblock_s2p_07g_one}
https://endpoint/?SignatureVersion=1.0&SignatureMethod=HMAC-SHA1&Signature=CT9X0VtwR86fNWSnsc6v8YGOjuE%3D&SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0ad82fd6cf
```

Take the DescribeUserCertificateList operation as an example. If the AccessKey ID is `testid` and the AccessKey Secret is `testsecret`, the original request URL is as follows:

``` {#codeblock_oar_9es_v2y}
https://cas.aliyuncs.com/?Action=DescribeUserCertificateList
&TimeStamp=2016-02-23T12:46:24Z
&Format=XML
&AccessKeyId=testid
&SignatureMethod=HMAC-SHA1
&SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0ad82fd6cf
&Version=2018-07-13
&SignatureVersion=1.0
```

To calculate the signature, perform the following operations:

1.  Use the request parameters to create the string to be signed.

    ``` {#codeblock_8su_ksv_nmj}
    GET&%2F&AccessKeyId%3Dtestid&Action%3DDescribeUserCertificateList&Format%3DXML&SignatureMethod%3DHMAC-SHA1&SignatureNonce%3D3ee8c1b8-83d3-44af-a94f-4e0ad82fd6cf&SignatureVersion%3D1.0&TimeStamp%3D2016-02-23T12%253A46%253A24Z&Version%3D2018-12-03
    ```

2.  Calculate the HMAC value of the string.

    Append an ampersand \(&\) to the AccessKey Secret, which will be used as the key to calculate the HMAC value. In this example, the key is `testsecret&`.

    ``` {#codeblock_lj2_5mp_2jd}
    CT9X0VtwR86fNWSnsc6v8YGOjuE=
    ```

3.  Add the signature to the request parameters:

    ``` {#codeblock_jwo_x4o_1vz}
    https://advs.aliyuncs.com/?Action=DescribeUserCertificateList
    &TimeStamp=2016-02-23T12:46:24Z
    &Format=XML
    &AccessKeyId=testid
    &SignatureMethod=HMAC-SHA1
    &SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0ad82fd6cf
    &Version=2018-07-13
    &SignatureVersion=1.0
    &Signature=CT9X0VtwR86fNWSnsc6v8YGOjuE%3D
    ```


**Note:** Alibaba Cloud provides SDKs in multiple languages and third-party SDKs to simplify signature algorithm coding. For more information about Alibaba Cloud SDKs, see .

