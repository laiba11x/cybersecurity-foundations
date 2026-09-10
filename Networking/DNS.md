# DNS — Domain Name System

## What is DNS?

* **DNS (Domain Name System)** maps **domain names to IP addresses**.
* This means we can use names such as `example.com` instead of remembering IP addresses.
* DNS operates at the **Application Layer (Layer 7)** of the OSI model.
* DNS normally uses:

  * **UDP port 53**
  * **TCP port 53** as a fallback

## Common DNS Records

### A Record

Maps a hostname to an **IPv4 address**.

Example:

`example.com → 172.17.2.172`

### AAAA Record

Maps a hostname to an **IPv6 address**.

### CNAME Record

Maps one domain name to **another domain name**.

Example:

`www.example.com → example.com`

### MX Record

Specifies the **mail server** responsible for handling email for a domain.

## DNS in Practice

When you visit a website, your device can query DNS for the domain's **A record** to find its IPv4 address.

When sending an email, the mail server can query DNS for the domain's **MX record** to find the appropriate mail server.

## nslookup

`nslookup` can be used to query DNS from the command line.

```bash
nslookup www.example.com
```

The response can contain both:

* An **A record** → IPv4 address
* An **AAAA record** → IPv6 address

### Key idea

**DNS = domain name → IP address**

**A = IPv4**

**AAAA = IPv6**

**CNAME = another domain name**

**MX = mail server**
