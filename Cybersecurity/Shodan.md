# Shodan

## What is Shodan?

**Shodan** is a search engine that scans the internet for publicly accessible devices and services.

It can find things such as:

* Web servers
* Networking equipment
* Industrial control systems
* Traffic cameras
* IoT devices

Shodan can show information about what is running on publicly accessible systems.

## Search Queries

You can search for specific software, versions or services.

Example:

```text
apache 2.4.1
```

This can find servers advertising that Apache version.

## Shodan Filters

| Filter     | Purpose                      | Example                 |
| ---------- | ---------------------------- | ----------------------- |
| `country`  | Search within a country      | `country:IE`            |
| `port`     | Search by port               | `port:22`               |
| `org`      | Search by organisation/ASN   | `org:AS7224`            |
| `hostname` | Search for a hostname/domain | `hostname:fakebank.thm` |

## Why Shodan is Useful

During a **penetration test or vulnerability assessment**, Shodan can help identify publicly exposed systems and services.

The information can then be compared against known vulnerabilities such as **CVEs**.

### Key Takeaway

**Shodan = search engine for publicly exposed devices and services on the Internet.**

It is useful for **reconnaissance** and identifying what an organisation has exposed to the Internet.
