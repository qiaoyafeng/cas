# Is web browsing speed affected if an SSL certificate is installed {#concept_igh_lvv_ydb .concept}

When an SSL certificate is deployed on a server, encryption and decryption are required for each SSL connection, which puts a pressure on server resources such as CPU, but web browsing speed remains generally unaffected. To relieve the resource pressure off the server:

-   Only use SSL for pages that require encryption, such as https://www.domain.com/login.asp.  Do not use https:// for all webpages.
-   Limit the use of large image or other large files on SSL-secured pages.

