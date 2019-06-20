# Which domain I must use while applying for an SSL certificate {#concept_rlv_cvv_ydb .concept}

The following example is used to describe how to choose an appropriate domain when applying for an SSL digital certificate.

Assume that www.domain.com is your website.

Your website includes a user logon page at http://www.domain.com/login.asp. You want to apply for an SSL digital certificate to guarantee confidentiality of your users’ usernames and passwords and prevent user information from being leaked or stolen during transmission. Your website also includes a user logon information management page at http://www.domain.com/oa/manage.asp. You also want to use the SSL digital certificate to secure the confidential information in the internal management system.

In this situation, you can use the www.domain.com domain to apply for an SSL certificate to secure these pages.

If your website exhibits exceptionally high traffic, we recommend that you set up a separate web server \(HTTP server\) for pages that require an SSL certificate and apply for the SSL certificate with a separate domain, such as secure.domain.com or ssl.domain.com.

**Note:** Make sure that the https:// address matches the domain used to apply for the SSL certificate. If they do not match, you may receive the error "The name on the security certificate is invalid or does not match the name of the site."  Please apply for an SSL digital certificate using the appropriate domain name according to the specific circumstances of your website.

For more information, see [How to select: certificate type-certificate brand-number of protected domain names](reseller.en-US/FAQ/How do I select: certificate type-certificate brand-number of protected domain names?.md#).

