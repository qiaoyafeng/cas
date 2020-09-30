# How can I apply for multi-domain wildcard certificates or hybrid certificates?

In the SSL Certificates Service console, you can bind only one domain at a time when you apply for wildcard and single-domain certificates. If you want to bind one or more wildcard and single domains at a time, submit a ticket to request a combination of the certificates.

## Prerequisites

-   Wildcard and single-domain certificates are purchased. For more information, see [Select and purchase certificates](/intl.en-US/.md).

    **Note:** For more information about domain types, see [How do I enter domains to be added to a certificate?](/intl.en-US/Apply for the certificate/FAQ/How do I enter domains to be added to a certificate.md)

-   Certificates that you want to combine are the same brand.
-   Certificates that you want to combine are not issued.

## Background information

After you purchase the certificates, combine them before you issue them. submit a [ticket](https://workorder-intl.console.aliyun.com/console.htm#/ticket/createIndex) to Alibaba Cloud and describe your requirement for the combination in the ticket. After your request is approved, Alibaba Cloud combines the certificates.

Only the OV SSL certificates of GlobalSign can be combined.

## Procedure

In the following example, two wildcard certificates and three single-domain certificates are used to illustrate the combination procedure. Each of the certificates is an OV certificate of DigiCert in the Professional edition and is valid for one year.

1.  Purchase two wildcard certificates and three single-domain certificates.

    **Note:** When you purchase the certificates, make sure that the numbers and types of the certificates are the same as those of the domains that you want to bind.

    After you purchase the certificates, immediately perform the next step.

2.  Submit a [ticket](https://workorder-intl.console.aliyun.com/console.htm#/ticket/createIndex) to request a combination of the purchased certificates.

    Provide the following information in the ticket:

    -   Ticket title: Combine single-domain certificates
    -   Ticket content: Take a screenshot of the certificates that you want to combine and enter the domains that you want to bind. For example, enter a.com, b.com, \*.p.a.com, and \*.p.b.com. The first a.com is the base domain, to which the certificate is issued.
    -   Ticket type: urgent.
3.  Log on to the [SSL Certificates Service console](https://yundunnext.console.aliyun.com/?p=cas).. On the Apply for Certificate page, bind the domains to the certificate that is reserved after the combination operation.

    After your request is approved and processed, only one certificate is reserved, and other certificates are dimmed. The dimmed certificates cannot be edited. You can select the editable certificate to bind domains. The system displays the numbers of wildcard and single domains that you can bind.

    **Note:** When you bind the first domain, enter a single domain. For more information, see [How do I enter domains to be added to a certificate?](/intl.en-US/Apply for the certificate/FAQ/How do I enter domains to be added to a certificate.md)

    We recommend that you select Automatic for CSR Generation when you create the CSR file. If you select Manual, you must use the first single domain in the domain list as `Common Name` in the CSR file. For more information, see [How do I create a CSR file?]()

4.  Submit the required materials for review.

    The CA vendor will make validation phone calls through the landline phone of your company or the mobile phone of the applicant in three to five business days. Make sure that the validation calls are properly answered.


