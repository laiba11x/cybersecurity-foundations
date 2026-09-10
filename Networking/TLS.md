# TLS (Transport Layer Security)

TLS (Transport Layer Security) is a cryptographic protocol that provides **secure communication** between a client and server over an insecure network.

### What TLS Provides

* **Confidentiality** – prevents others from reading the data.
* **Integrity** – prevents others from modifying the data.
* **Authentication** – certificates help verify the identity of a server.

### SSL vs TLS

* **SSL** (Secure Sockets Layer) was the predecessor to TLS.
* **TLS 1.0** improved on SSL 3.0.
* **TLS 1.3** is the modern version discussed in this room.

### TLS Certificates

Servers use **digital certificates** to identify themselves.

A typical process is:

1. Server administrator creates a **Certificate Signing Request (CSR)**.
2. CSR is submitted to a **Certificate Authority (CA)**.
3. The CA verifies the request and issues a signed certificate.
4. The server uses the certificate to prove its identity.

**Certificate Authority (CA)** = trusted organisation that issues/signs digital certificates.

### Self-Signed Certificates

A self-signed certificate is signed by the server itself rather than a trusted third-party CA.

It **cannot prove the server's authenticity** in the same way as a certificate signed by a trusted CA.

### Examples of TLS-Secured Protocols

* HTTP → **HTTPS**
* DNS → **DoT (DNS over TLS)**
* MQTT → **MQTTS**
* SIP → **SIPS**
* SMTP → **SMTPS**
* POP3 → **POP3S**
* IMAP → **IMAPS**

### Key idea

**TLS protects data in transit by providing confidentiality and integrity, while certificates help authenticate the communicating party.**
