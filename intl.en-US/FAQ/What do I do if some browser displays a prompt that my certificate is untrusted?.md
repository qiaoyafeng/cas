# What do I do if some browser displays a prompt that my certificate is untrusted? {#concept_mj2_1t5_ydb .concept}

If you receive a prompt on some device that your certificate is untrusted, check the brand of that certificate and the type of device on which the prompt is displayed.

Some brands are unsupported on certain devices.

The current mainstream devices on the market are compatible with Symantec, geotrust-branded digital certificates.

## Troubleshooting procedures {#section_tk4_1t5_ydb .section}

Once you have excluded any potential compatibility issue between the certificate and your device, you can:

1.  Use either of the following tools for a more advanced verification process:
    -   [Symantect CryptoReport SSL/TLS certificate checker](https://cryptoreport.websecurity.symantec.com/checker/views/certCheck.jsp)
    -   [GeoCerts SSL Checker](https://www.geocerts.com/ssl_checker)

        If the results show a different certificate brand, type, or domain from your order, check the configuration of the certificate on the server.

        If the results show that the certificate chain is incomplete, check if you have the right configuration for the certificate.

        **Note:** A PEM digital certificate provided with Alibaba Cloud Certificates Service consists of two segments, and both the segments must be available. Remove the blank lines between these segments, if any. After the configuration is modified, restart the web service and perform verification again.

2.  Make sure that you have disabled insecure protocols in the configuration, such as SSLv3 which has known bugs.
3.  Check if there is any reference of HTTP resource in your webpage. Some browsers may consider the certificate to be insecure if an HTTP resource is referenced in an HTTPS site.
4.  If a domain is associated with multiple servers, check if the certificate is correctly deployed on each server.

