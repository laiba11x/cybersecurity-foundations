# SFTP and FTPS

## SFTP

**SFTP (SSH File Transfer Protocol)** allows secure file transfer using SSH.

* Uses **SSH port 22**.
* Part of the SSH protocol suite.
* Uses the same SSH security and encryption.
* Connect with:

```bash
sftp username@hostname
```

### Common SFTP Commands

* **get filename** – downloads a file.
* **put filename** – uploads a file.

SFTP commands are generally Unix-like and differ from traditional FTP commands.

## SFTP vs FTPS

**SFTP** and **FTPS** are different protocols.

* **SFTP** → uses **SSH**, port **22**.
* **FTPS** → uses **TLS**, usually port **990**.
* FTPS requires a **TLS certificate**.
* FTPS uses separate connections for control and data transfer.

### Key idea

**SFTP = secure file transfer over SSH**

**FTPS = FTP secured with TLS**
