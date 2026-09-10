# WHOIS and Domain Registration

## Domain Registration

* When someone **registers a domain**, they gain control over its DNS records.
* The domain owner can configure records such as:

  * **A**
  * **AAAA**
  * **MX**
  * Other valid DNS records
* Domains are usually registered for one or more years and require an annual fee.

## WHOIS

* **WHOIS** provides information about a registered domain and its registrant.
* WHOIS is **not an acronym**.
* Information can include:

  * Registrant name
  * Organisation
  * Address
  * Phone number
  * Email address
  * Domain creation date
  * Last updated date
  * Expiration date
  * Registrar

### Privacy Protection

* Domain owners can use **WHOIS privacy protection** to hide their personal information from public WHOIS records.
* Instead of the actual registrant's details, the record may show a privacy service or proxy organisation.

## WHOIS Command

On Linux, the `whois` command can be used to look up domain registration information:

```bash
whois example.com
```

### Key idea

**WHOIS = information about a registered domain and its registrant**

**Domain registration = gives the owner control over the domain's DNS records**

**WHOIS privacy = hides the registrant's personal information**
