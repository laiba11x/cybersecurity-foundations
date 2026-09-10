# SSH (Secure Shell)

SSH is used to **securely connect to and administer remote systems**.

Unlike TELNET, SSH **encrypts network traffic**, protecting login credentials and other data from being intercepted.

### Benefits of SSH

* **Secure authentication** – supports passwords, public keys and two-factor authentication.
* **Confidentiality** – encrypts data to prevent eavesdropping.
* **Integrity** – helps ensure data has not been modified.
* **Tunnelling** – can securely route other traffic through an SSH connection.
* **X11 Forwarding** – allows graphical applications on a remote Unix-like system to be used over SSH.

### Connecting with SSH

```bash
ssh username@hostname
```

If your username is the same as the remote username:

```bash
ssh hostname
```

### SSH Port

* **TCP port 22**

### SSH vs TELNET

* **TELNET** → TCP 23, traffic sent in cleartext.
* **SSH** → TCP 22, traffic encrypted.

### Key idea

**SSH is the secure alternative to TELNET for remote administration.**
