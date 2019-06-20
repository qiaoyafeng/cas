# How can I install SSL certificates on Nginx or Tengine servers? {#concept_95491_zh .concept}

In the Alibaba Cloud SSL Certificates console, you can download SSL certificates for Nginx. After you decompress the downloaded package, the following files are displayed:

-   .crt file: indicates the certificate file. crt is the extension of a pem file.
-   .key file: indicates the private key file \(the file is not available if you did not select Automatic for **CSR Generation** when applying for SSL certificates\).

**Note:** The .pem certificate file is a Base64-encoded text file. You can modify its extension as needed.

Use the standard Nginx configuration as an example. Assume that the certificate file is named a.pem, and the private key file is named a.key.

1.  Create a cert directory in the Nginx installation directory, and copy all downloaded files to the cert directory. If you created the CSR file yourself to request a certificate, place the corresponding private key file in the cert directory and name it a.key.
2.  Go to **Nginx installation directory** \> **conf**. Open the Nginx.conf file and locate the following configurations:

    ```
    # HTTPS server
    # #server {
    # listen 443;
    # server_name localhost;
    # ssl on;
    # ssl_certificate cert.pem;
    # ssl_certificate_key cert.key;
    # ssl_session_timeout 5m;
    # ssl_protocols SSLv2 SSLv3 TLSv1;
    # ssl_ciphers ALL:! ADH:! EXPORT56:RC4+RSA:+HIGH:+MEDIUM:+LOW:+SSLv2:+EXP;
    # ssl_prefer_server_ciphers on;
    # location / {
    #
    #
    #}
    #}
    ```

3.  Change it to \(the attributes that start with ssl are directly related to the certificate configuration, and the others can be copied or adjusted as needed\):

    ```
    server {
        listen 443;
        server_name localhost;
        ssl on;
        root html;
        index index.html index.htm;
        ssl_certificate   cert/a.pem;
        ssl_certificate_key  cert/a.key;
        ssl_session_timeout 5m;
        ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:ECDHE:ECDH:AES:HIGH:! NULL:! aNULL:! MD5:! ADH:! RC4;
        ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
        ssl_prefer_server_ciphers on;
        location / {
            root html;
            index index.html index.htm;
        }
    }
    ```

4.  Save the settings and exit.
5.  Restart Nginx.

