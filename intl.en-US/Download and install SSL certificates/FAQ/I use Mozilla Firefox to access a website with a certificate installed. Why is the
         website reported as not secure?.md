# I use Mozilla Firefox to access a website with a certificate installed. Why is the website reported as not secure?

**Problem description**

After the certificate is installed, the website is reported as normal when I access it by using Google Chrome. However, the same website is reported as not secure when I access it by using Mozilla Firefox.

**Cause**

A weak encryption algorithm is configured on your server.

**Solution**

We recommend that you use the encryption suite `ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:ECDHE:ECDH:AES:HIGH:! NULL:! aNULL:! MD5:! ADH:! RC4` and the protocol `ssl_protocols TLSv1 TLSv1.1 TLSv1.2` for your website server.

