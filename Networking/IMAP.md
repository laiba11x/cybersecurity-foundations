# IMAP (Internet Message Access Protocol)

IMAP is used to **access and synchronise emails across multiple devices**.

Unlike POP3, IMAP normally keeps emails on the server and synchronises changes such as:

* Read/unread status
* Moved messages
* Deleted messages

### Common IMAP Commands

* **LOGIN** – authenticates the user.
* **SELECT** – selects a mailbox/folder.
* **FETCH** – retrieves a specific email and its contents.
* **MOVE** – moves messages to another mailbox.
* **COPY** – copies messages to another mailbox.
* **LOGOUT** – ends the session.

### IMAP Port

* **TCP port 143**

### POP3 vs IMAP

* **POP3** → downloads emails, often removing them from the server.
* **IMAP** → keeps emails on the server and synchronises them across devices.

### Key idea

**SMTP sends → IMAP synchronises/retrieves → POP3 downloads.**
