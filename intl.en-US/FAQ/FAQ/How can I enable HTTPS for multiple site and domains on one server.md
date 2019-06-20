# How can I enable HTTPS for multiple site and domains on one server {#concept_kql_qwv_ydb .concept}

Consider the following scenario: You have multiple sites \(for example: site1.marei.com, site2.marei.com, and site3.marei.com\) that are associated with the same IP: PORT and configured with different host headers. You have deployed a certificate for each SSL site. In this situation, a certificate mismatch error still occurs when browsing these websites.

## For IIS {#section_ul5_qwv_ydb .section}

Cause

An https request arrives at the IIS server in an encrypted form, and needs to be decrypted with an appropriate server certificate. Because each site is associated with a unique certificate, the server has to determine which certificate to use for decryption based on different host headers in the request. However, the host header is also encrypted as a part of the request. As a result, the IIS server is forced to use the first certificate associated with the IP: PORT site to decrypt the request, which may cause the request to other sites to fail, resulting in an error.

Solutions

-   Solution 1: Associate each HTTPS site with a unique port. Using this solution, the visitor must manually specify a port when browsing a webpage, for example, https://site.domain.com:444.
-   Solution 2: Assign a separate IP for each site, which eliminates the conflict and the requirement to add host headers.
-   Solution 3: Use a wildcard certificate, and associate the wildcard certificate with \*.domain.com \(for this example, use \*.marei.com\). In this way, all requests to this domain can be decrypted with this certificate, negating the certificate mismatch error.
-   Solution 4: Upgrade to IIS 8 and then enable SNI \(Server Name Indication\). This allows the server to find the certificate using the host header extracted from the request.

    For more information about how to enable SNI, see [IIS 8.0 Server Name Indication \(SNI\): SSL Scalability](http://www.iis.net/learn/get-started/whats-new-in-iis-8/iis-80-server-name-indication-sni-ssl-scalability).


## For Nginx {#section_yl5_qwv_ydb .section}

Open the nginx.conf file in the conf directory under Nginx installation directory, and locate the following configurations:

```
server {
    listen 443;
    server_name domain1;
    ssl on;
    ssl_certificate //Disk directory/Certificate order No. 1.pem;
    ssl_certificate_key //Disk directory/Certificate order No. 1.key;
    ssl_session_timeout 5m;
    ssl_protocols TLSv1 TLSv1.1 TLSv1.2; 
    ssl_ciphers AESGCM:ALL:! DH:! EXPORT:! RC4:+HIGH:! MEDIUM:! LOW:! aNULL:! eNULL;
    ssl_prefer_server_ciphers on;
    location / {
        root html;
        index index.html index.htm;
    }
}
```

Add an additional configuration segment as follows:

```
server {
    listen 443;
    server_name dommain2;
    ssl on;
    ssl_certificate //Disk directory/Certificate order No. 2.pem;
    ssl_certificate_key //Disk directory/Certificate order No. 2.key;
    ssl_session_timeout 5m;
    ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
    ssl_ciphers AESGCM:ALL:! DH:! EXPORT:! RC4:+HIGH:! MEDIUM:! LOW:! aNULL:! eNULL;
    ssl_prefer_server_ciphers on;
    location / {
        root html;
        index index.html index.htm;
    }
}
```

Using this solution, you can enable multi-certificate support in the Nginx server.

## For Apache Configure HTTPS virtual hosts to share Port 443 as follows: {#section_mps_dxv_ydb .section}

```
Listen 443
NameVirtualHost *:443
<VirtualHost *:443>
  ……
ServerName www.example1.com
SSLCertificateFile common.crt;
SSLCertificateKeyFile common.key;
SSLCertificateChainFile ca.crt
  ……
</VirtualHost>
<VirtualHost *:443>
  ……
ServerName www.example2.com
SSLCertificateFile common2.crt;
SSLCertificateKeyFile common2.key;
SSLCertificateChainFile ca2.crt

  ……
</VirtualHost>
```

