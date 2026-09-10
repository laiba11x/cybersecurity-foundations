# POP3 (Post Office Protocol 3)

POP3 is used by an email client to **retrieve/download emails from a mail server**.

### Common POP3 Commands

* **USER** – identifies the user.
* **PASS** – provides the user's password.
* **STAT** – shows the number of messages and total size.
* **LIST** – lists messages and their sizes.
* **RETR** – retrieves a specific email.
* **DELE** – marks an email for deletion.
* **QUIT** – ends the POP3 session and applies changes.

### POP3 Port

* **TCP port 110**

### Example

```text
telnet 10.129.176.38 110
USER username
PASS password
LIST
RETR 1
QUIT
```

### Security

POP3 without encryption can expose **login credentials and email contents** to someone capturing the network traffic.

### Key idea

**SMTP sends emails → POP3 retrieves emails.**
