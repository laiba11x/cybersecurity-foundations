# SMTP (Simple Mail Transfer Protocol)

SMTP is used to **send emails** between mail clients and mail servers, and between mail servers.

### Common SMTP Commands

* **HELO / EHLO** – starts an SMTP session.
* **MAIL FROM** – specifies the sender.
* **RCPT TO** – specifies the recipient.
* **DATA** – starts sending the email content.
* **`.`** – on its own line, indicates the end of the email.
* **QUIT** – ends the SMTP session.

### SMTP Port

* SMTP uses **TCP port 25** by default.

### Example

```text
telnet 10.129.176.38 25
HELO client.thm
MAIL FROM: <user@client.thm>
RCPT TO: <recipient@server.thm>
DATA
Subject: Test

Hello!
.
QUIT
```

### Key idea

SMTP defines how **emails are sent** from clients to mail servers and between mail servers.
