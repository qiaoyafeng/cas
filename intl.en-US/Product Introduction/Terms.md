# Terms

This topic introduces basic concepts and terms used in Alibaba Cloud SSL Certificates Service.

## digital certificate

A digital certificate is a document signed by a trusted CA. The certificate contains information about the public key owner and the public key file. It is a trusted credential that is issued by a CA to a website. A certificate must contain a public key, a certificate name, and a digital signature provided by a CA.

Digital certificates are valid only for a specific period of time.

## SSL

Secure Sockets Layer \(SSL\) is a protocol that is used to encrypt data transmitted between browsers and websites on the network. It prevents data tampering or interception during transmission.

## SSL certificate

An SSL certificate is a trusted credential that is issued by a CA to a website. It uses the SSL protocol for communications and implements website identity authentication and encrypted transmission.

SSL provides an encryption mechanism for application data transmission on a TCP/IP network. The applications include HTTP, Telnet, and FTP. SSL uses public keys to encrypt data transmitted by TCP/IP connections, ensure message integrity, and authenticate servers and clients. Client authentication is optional.

SSL Certificates Service uses a public-key encryption system that uses a matching key pair to encrypt and decrypt data. Each user creates a private key that is highly secured and not disclosed to anyone for decryption and signature. Meanwhile, the user creates a public key and discloses this key to a group of users for encryption and signature verification.

After you install an SSL certificate on a web server, HTTPS is enabled for the web server. Your website will transmit data through HTTPS, which helps establish trusted and encrypted connections between your website and the web server. This ensures the security of data during transmission.

For more information about the private keys of certificates, see [What is a public key and a private key?](/intl.en-US/Product Introduction/SSL certificate concepts/What is a public key and a private key?.md).

## HTTPS

HTTPS is based on HTTP and SSL. It is a secure version of HTTP and encrypts website communications based on SSL.

After you install an SSL certificate on the server of your website, HTTPS is enabled to activate the **SSL-encrypted channel** between browsers and the web server. This enables bidirectional encrypted transmission and prevents content tampering or interception during transmission.

## CA

CA stands for certificate authority.

As a trusted third party in an e-commerce transaction, CA is responsible for verifying the validity of public keys.

## NGINX

NGINX is a lightweight web server and processes highly concurrent connections. You can configure it as a reverse proxy server or an email proxy server that complies with Internet Message Access Protocol \(IMAP\) or Post Office Protocol version 3 \(POP3\). NGINX is based on BSD-like licenses. NGINX runs on different operating systems, such as Linux, Windows, FreeBSD, Solaris, AIX, and macOS. It can be used for reverse proxy, load balancing, and dynamic and static separation.

## Tengine

Tengine is a web server project initiated by Taobao. It supports all the features of NGINX and is compatible with NGINX configurations.

## PuTTY

PuTTY is connection software that allows you to perform operations by using Telnet, SSH, rlogin, pure TCP, and serial interfaces. It can remotely manage Linux and Windows operating systems.

## Xshell

Xshell is a powerful terminal emulator. It supports Telnet on SSH1 and SSH2 clients and also in Windows. Xshell can remotely manage servers that run different operating systems from Windows. Xshell supports VT100, VT220, VT320, Xterm, Linux, SCO ANSI, and ANSI terminals and provides a variety of terminal screen views to replace traditional Telnet clients.

## CentOS

CentOS is an enterprise-grade Linux distribution and is derived from the sources of Red Hat Enterprise Linux. It is open source and free of charge.

## CSR

A certificate signing request \(CSR\) file contains your server and company information. When you apply for an SSL certificate, you must submit the CSR file to a CA. The CA signs the CSR file by using the private key of the root certificate and generates a public key file to issue your SSL certificate.

