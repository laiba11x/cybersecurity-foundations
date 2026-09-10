# FTP (File Transfer Protocol)

FTP (File Transfer Protocol) is designed to **transfer files** between a client and a server.

### Common FTP Commands

* **USER** – enter username.
* **PASS** – enter password.
* **RETR** – download a file from the server.
* **STOR** – upload a file to the server.
* **LS** – list available files.

### FTP Port

* FTP uses **TCP port 21** by default for the control connection.
* File transfers use a **separate connection**.

### Anonymous FTP

Some FTP servers allow users to log in with the username **anonymous** without providing a password.

### Example

```text
ftp 10.129.176.38
anonymous
ls
type ascii
get coffee.txt
```

### Key idea

FTP is specifically designed for **efficient file transfer** between clients and servers.
