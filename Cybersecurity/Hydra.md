# Hydra

## What is Hydra?

* **Hydra** is an online **brute-force password testing tool**.
* It automates trying usernames and passwords against authentication services.
* Instead of manually trying passwords, Hydra can use a **password list** to test many possibilities quickly.

### Common uses

Hydra can test authentication services such as:

* SSH
* FTP
* HTTP/HTTPS login forms
* SMB
* RDP
* SMTP
* SNMP
* MySQL
* PostgreSQL
* VNC
* Telnet

Hydra supports many different protocols and authentication methods.

## How Hydra Works

Basic idea:

**Username + Password List → Hydra → Authentication Service → Test credentials**

Hydra tries combinations from the supplied lists and identifies credentials that successfully authenticate.

## Why Strong Passwords Matter

Brute-force attacks are more effective against weak or commonly used passwords.

Weak passwords may be:

* Commonly used.
* Short.
* Missing special characters.
* Based on predictable words or patterns.
* Left as the application's default password.

For example, default credentials such as:

```text id="n7p4k2"
admin:password
```

should always be changed.

### Key point

Hydra demonstrates why **strong, unique passwords and changing default credentials** are important security controls.

Hydra should only be used against systems where you have permission to test.
