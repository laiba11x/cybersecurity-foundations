## DNS (Domain Name System)

**DNS** translates human-readable **domain names** into **IP addresses**.

For example:

`tryhackme.com` → `104.26.10.229`

This means we can use easy-to-remember domain names instead of remembering IP addresses.

### Key Takeaway

**DNS = translates domain names into IP addresses.**

## Domain Hierarchy

A domain name is organised into different levels.

### TLD (Top-Level Domain)

The **TLD** is the rightmost part of a domain name.

Example:

`tryhackme.com`

* `.com` = TLD
* `.com` is a **gTLD (Generic TLD)**.
* **ccTLDs** represent countries, such as `.uk` or `.ca`.

### Second-Level Domain

The **Second-Level Domain (SLD)** is directly before the TLD.

Example:

`tryhackme.com`

* `tryhackme` = Second-Level Domain
* `.com` = TLD

### Subdomain

A **subdomain** is placed before the Second-Level Domain.

Example:

`admin.tryhackme.com`

* `admin` = Subdomain
* `tryhackme` = Second-Level Domain
* `.com` = TLD

Multiple subdomains can be used, for example:

`jupiter.servers.tryhackme.com`

### Key Takeaway

**Domain structure:**

`subdomain.second-level-domain.tld`

Example:

`admin.tryhackme.com`

## DNS Record Types

DNS has different **record types** that provide different types of information.

| Record    | Purpose                                                                                 |
| --------- | --------------------------------------------------------------------------------------- |
| **A**     | Resolves a domain to an **IPv4 address**                                                |
| **AAAA**  | Resolves a domain to an **IPv6 address**                                                |
| **CNAME** | Resolves a domain to **another domain name**                                            |
| **MX**    | Identifies the **mail servers** for a domain                                            |
| **TXT**   | Stores **text-based information**, often used for email security or domain verification |

### Key Takeaway

* **A → IPv4**
* **AAAA → IPv6**
* **CNAME → another domain**
* **MX → email servers**
* **TXT → text information / verification**

## What Happens When You Make a DNS Request?

When you enter a domain name, DNS finds the IP address for that domain.

The process is generally:

1. **Your computer checks its local DNS cache.**
2. If there is no result, it asks a **Recursive DNS Server**.
3. If the Recursive DNS Server doesn't have the answer cached, it asks the **Root DNS Server**.
4. The Root Server directs it to the correct **TLD server** (such as `.com`).
5. The TLD server directs it to the domain's **Authoritative DNS Server** (nameserver).
6. The Authoritative Server provides the correct DNS record/IP address.
7. The result is sent back to the Recursive DNS Server and then to your computer.
8. The result is **cached** for future requests.

### DNS Caching

DNS records have a **TTL (Time To Live)** value.

TTL tells devices how long they can keep a DNS response in their cache before requesting it again.

Caching makes DNS faster and reduces unnecessary DNS requests.

### Key Takeaway

**Computer → Recursive DNS → Root → TLD → Authoritative DNS → IP address**

DNS caching can avoid this process when the answer is already stored locally.

