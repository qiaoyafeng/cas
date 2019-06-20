# Domain name certificate application note {#concept_c4l_tcw_ydb .concept}

When the domain name console automatically issues a domain name association certificate, it can be automatically issued without requiring the user to apply for the certificate, there are the following prerequisites for the configuration of the relevant subsequent certificate issuance and verification file:

-   Domain name in ALI cloud WAN network
-   Cloud analytics in ALI cloud

    If cloud resolution is not in ALI cloud, the autoissue cannot be completed after the certificate application. If the user does not have the ability to configure DNS resolution, it is recommended that DNS resolution be transferred to Ali cloud, authorization is automatically configured for DNS authentication parsing records in the background so that the issue can be completed.

    When there is a large number of certificate-issuing requirements, it is recommended that you transfer DNS resolution to Ali cloud, certificate Application and management work can be greatly simplified.

-   Domain Name certified by real name
-   Domain name within the effective period

