# Glossary {#concept_orz_v2p_ydb .concept}

## Digital certificate {#section_sht_nfp_ydb .section}

A digital certificate is a digitally signed document, issued by the Certificate Authority \(CA\). It contains the public key information and details of the identity of its owner. A basic certificate includes a public key, certificate name, and the digital signature of the CA.

Note that the digital certificates are valid only for a specific period of time.

## SSL certificate {#section_tht_nfp_ydb .section}

An SSL certificate is a server digital certificate that complies with the SSL protocol. Issued by a trusted root certificate authority in the web browser after server authentication is complete, an SSL certificate provides both website authentication and encrypted transmission.

## HTTPS {#section_uht_nfp_ydb .section}

HTTPS is an SSL protocol-based communication protocol for encrypted transmission over a network.

After an SSL certificate is installed for a website, visiting that website with HTTPS activates the SSL encryption channel \(SSL protocol\) between the client-side browser and the web server. This provides intensive bi-directional encryption of communications between the client and server, and prevents the contents of the communication from being divulged or tampered with. HTTPS is a combination of HTTP and SSL, namely, the secured edition of HTTP.

## Certificate authority \(CA\) {#section_vht_nfp_ydb .section}

The certificate authority is an entity that issues digital certificates. As a trusted e-commerce third party, a CA is responsible for attesting to the validity of public keys in the public key infrastructure.

## Root certificate {#section_wht_nfp_ydb .section}

A root certificate is a self-signed certificate by a CA, serving as the starting point of the trust chain. Installing the root certificate means you trust the aforementioned CA.

