# What is the difference between revoking a certificate and deleting a certificate? {#concept_qhn_1wn_fhb .concept}

Alibaba Cloud SSL Certificates Service allows you to revoke certificates and delete expired or revoked certificates.

**Revoke**: An issued certificate is canceled on the part of the issuing authority. After the certificate is revoked, it is no longer valid for encryption and the browser no longer trusts it.

**Delete**: Certificate resources are deleted from the Alibaba Cloud system.

## Restrictions on certificate revocation and refunds {#section_6k1_gx1_day .section}

You can apply to [Revoke certificates](../../../../reseller.en-US/User Guide/Revoke certificates.md#) when you no longer need it or for security reasons. Certificate revocation is not subject to any restrictions.

When a paid certificate is revoked \(**you submit a revocation application and the revocation review is completed**\) within 30 days after it is issued, you are entitled to a full refund. If you revoke a certificate after 30 days, no refund is made.

## Restrictions on certificate deletion {#section_gqp_2j8_4uk .section}

-   Unexpired certificates can be deleted only after being revoked.
-   Expired certificates can be deleted at any time.
-   Manually uploaded certificates can be deleted at any time.

