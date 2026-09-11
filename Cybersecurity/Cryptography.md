# Cryptography

Cryptography is the practice of protecting information and communications from attackers and unauthorised third parties.

Its main goals are:

* **Confidentiality** – prevents unauthorised people from reading data.
* **Integrity** – ensures data has not been changed or tampered with.
* **Authenticity** – verifies that data or a communication really comes from the claimed source.

## Where Cryptography Is Used

Cryptography is used every day, often without the user noticing it.

Examples include:

* **Websites:** HTTPS encrypts information sent between the browser and server.
* **SSH:** Creates an encrypted connection for securely accessing remote systems.
* **Online banking:** Digital certificates help verify that the website belongs to the legitimate organisation.
* **File downloads:** Hash functions can be used to check that a downloaded file has not been changed or corrupted.

## Data at Rest and Data in Motion

Sensitive information should be protected both when it is stored and when it is being transmitted.

* **Data at rest** – data stored on devices or systems, such as databases and files.
* **Data in motion** – data being transferred across a network.

## Cryptography and Regulations

Some industries have security requirements for protecting sensitive information.

For example:

* **PCI DSS** – security requirements for payment card data.
* **GDPR** – data protection regulation in the EU.
* **DPA** – UK Data Protection Act.
* **HIPAA** – US healthcare data protection law.
* **HITECH** – US legislation relating to healthcare information technology and security.

### Key Takeaway

Cryptography protects data from being **read, changed, or impersonated by attackers**. It provides confidentiality, integrity and authenticity across many everyday technologies.

## Plaintext, Ciphertext, Cipher and Key

### Plaintext

**Plaintext** is the original, readable data before encryption.

It could be:

* A text message
* An image
* A document
* Credit card information
* Medical records
* Any other data

### Ciphertext

**Ciphertext** is the scrambled, unreadable data produced after encryption.

The goal is that an attacker cannot understand the original plaintext without the correct key.

### Cipher

A **cipher** is an algorithm used to convert plaintext into ciphertext and back again.

### Key

A **key** is a string of bits used by the cipher to encrypt or decrypt data.

The cipher itself can generally be public knowledge, but the secret key must be protected.

### Encryption

**Encryption** converts plaintext into ciphertext using a cipher and a key.

**Plaintext + Key → Encryption → Ciphertext**

### Decryption

**Decryption** converts ciphertext back into the original plaintext using the correct cipher and key.

**Ciphertext + Key → Decryption → Plaintext**

### Simple Example

```text
Plaintext
   ↓
Encryption + Key
   ↓
Ciphertext
   ↓
Decryption + Key
   ↓
Plaintext
```

### Key Takeaway

The **cipher** is the algorithm, while the **key** is the secret value used by the cipher. The plaintext is readable before encryption, and the ciphertext is the unreadable result after encryption.

## Caesar Cipher

The **Caesar Cipher** is a historical substitution cipher that encrypts text by shifting each letter by a fixed number of positions in the alphabet.

### Example

Using a right shift of **3**:

```text
Plaintext:  TRYHACKME
Key:        3
Cipher:     Caesar Cipher

Ciphertext: WUBKDFNPH
```

For example:

* `T` → `W`
* `R` → `U`
* `Y` → `B`

When the shift reaches `Z`, it starts again from `A`.

### Decryption

To decrypt the message, shift each letter in the opposite direction.

```text
Ciphertext → Shift left by 3 → Plaintext
```

### Why Caesar Cipher Is Insecure

There are only **25 possible useful keys**, because shifting by 26 returns every letter to itself.

This makes the cipher vulnerable to a **brute-force attack**, where an attacker tries every possible key until the message makes sense.

By modern standards, the Caesar Cipher is therefore **insecure**.

### Other Historical Ciphers

* **Vigenère Cipher** – 16th century
* **Enigma Machine** – used during World War II
* **One-Time Pad** – associated with Cold War cryptography

### Key Takeaway

The Caesar Cipher is useful for understanding how encryption works, but it is **not secure for protecting real information** because its small key space makes brute-forcing easy.

## Symmetric vs Asymmetric Encryption

There are two main categories of encryption:

* **Symmetric encryption**
* **Asymmetric encryption**

### Symmetric Encryption

Symmetric encryption uses the **same secret key** to encrypt and decrypt data.

```text
Plaintext
   ↓
Encryption + Shared Secret Key
   ↓
Ciphertext
   ↓
Decryption + Same Secret Key
   ↓
Plaintext
```

The main challenge is **securely sharing the key** with the intended recipient. Anyone who obtains the key could potentially decrypt the data.

Examples:

* **DES** – 56-bit key; now insecure.
* **3DES** – applies DES three times; deprecated.
* **AES** – modern symmetric encryption standard using 128, 192, or 256-bit keys.

### Asymmetric Encryption

Asymmetric encryption uses **two different keys**:

* **Public key** – can be shared with everyone.
* **Private key** – must be kept secret.

For confidentiality, the recipient's **public key** is used to encrypt the data, and their **private key** is used to decrypt it.

```text
Plaintext
   ↓
Encryption + Recipient's Public Key
   ↓
Ciphertext
   ↓
Decryption + Recipient's Private Key
   ↓
Plaintext
```

Examples:

* **RSA**
* **Diffie-Hellman**
* **ECC (Elliptic Curve Cryptography)**

Asymmetric encryption is generally **slower** than symmetric encryption and often uses larger keys. ECC can provide strong security with much smaller keys than RSA.

### Key Differences

|                | Symmetric                | Asymmetric                 |
| -------------- | ------------------------ | -------------------------- |
| Keys           | One shared key           | Public + private key       |
| Encryption     | Shared secret key        | Public key                 |
| Decryption     | Same shared key          | Private key                |
| Main challenge | Securely sharing the key | Protecting the private key |
| Speed          | Generally faster         | Generally slower           |
| Examples       | AES, DES, 3DES           | RSA, Diffie-Hellman, ECC   |

### Key Takeaway

**Symmetric = one shared secret key.**

**Asymmetric = public key + private key.**

Symmetric encryption is generally faster, while asymmetric encryption makes secure key exchange easier because the public key can be shared openly.

## Mathematical Foundations of Cryptography

Modern cryptography relies heavily on mathematics. Two useful operations are **XOR** and **modulo**.

### XOR Operation

**XOR (exclusive OR)** compares two binary bits:

| A | B | A ⊕ B |
| - | - | ----- |
| 0 | 0 | 0     |
| 0 | 1 | 1     |
| 1 | 0 | 1     |
| 1 | 1 | 0     |

The rule is simple:

* Same bits → `0`
* Different bits → `1`

### XOR Example

```text
1010
1100
----
0110
```

Each bit is XORed with the corresponding bit.

### Useful XOR Properties

* `A ⊕ A = 0`
* `A ⊕ 0 = A`
* `A ⊕ B = B ⊕ A`
* `(A ⊕ B) ⊕ C = A ⊕ (B ⊕ C)`

### XOR in Encryption

XOR can be used as a basic form of symmetric encryption.

If `P` is the plaintext and `K` is the secret key:

```text
C = P ⊕ K
```

To recover the plaintext:

```text
P = C ⊕ K
```

This works because XORing with the same key twice cancels it out:

```text
(P ⊕ K) ⊕ K = P
```

In real cryptography, XOR is usually part of more complex algorithms rather than being used on its own.

## Modulo Operation

The **modulo** operator gives the remainder after division.

It is written as `%` or `mod`.

Examples:

```text
25 % 5 = 0
23 % 6 = 5
23 % 7 = 2
```

For example:

```text
23 ÷ 6 = 3 remainder 5
```

Therefore:

```text
23 % 6 = 5
```

### Important Property

For a positive divisor `n`, the result of:

```text
a % n
```

is always between:

```text
0 and n - 1
```

Modulo is **not reversible**. For example, if:

```text
x % 5 = 4
```

there are infinitely many possible values of `x`, such as `4`, `9`, `14`, `19`, etc.

### Key Takeaway

* **XOR** compares binary bits and is useful in cryptographic algorithms.
* **Modulo** gives the remainder after division and is widely used in cryptographic mathematics.

## Key Exchange

Symmetric encryption is fast, but it has a problem: **how do we securely share the secret key?**

Asymmetric cryptography can help solve this problem.

### Simple Analogy

Imagine sending a secret code to someone:

* The **secret code** = symmetric encryption cipher and key
* The person's **lock** = their public key
* The person's **key to the lock** = their private key

You can put the secret code inside a box and lock it using their public key. Only the person with the matching private key can unlock it.

### In Cryptography

```text
Symmetric key
      ↓
Encrypt using server's public key
      ↓
Send securely to server
      ↓
Server decrypts using private key
      ↓
Both sides now have the symmetric key
```

After the symmetric key has been securely established, the communication can use **symmetric encryption**, which is much faster.

### Why Use Both?

* **Asymmetric encryption** → useful for securely establishing/exchanging keys.
* **Symmetric encryption** → useful for the actual communication because it is faster.

In real systems, additional cryptography such as **digital signatures and certificates** can be used to verify that you are communicating with the legitimate server.

### Key Takeaway

Asymmetric cryptography can be used to **securely establish a symmetric encryption key**, after which the faster symmetric encryption can protect the communication.

## RSA

**RSA (Rivest–Shamir–Adleman)** is an asymmetric encryption algorithm that allows secure communication over an insecure channel.

### Why Is RSA Secure?

RSA relies on the difficulty of **factoring very large numbers**.

It is easy to multiply two large prime numbers together:

```text
p × q = n
```

However, given a very large `n`, finding the original prime numbers `p` and `q` is extremely difficult.

RSA uses very large prime numbers in real-world applications, making factoring the resulting number computationally impractical.

### RSA Keys

RSA uses a **public key** and a **private key**.

* **Public key:** `(n, e)` → can be shared with others.
* **Private key:** `(n, d)` → must be kept secret.

The public key is used for encryption, while the private key is used for decryption.

### Basic RSA Process

For encryption:

```text
c = m^e mod n
```

For decryption:

```text
m = c^d mod n
```

Where:

| Variable | Meaning                        |
| -------- | ------------------------------ |
| `p`      | Large prime number             |
| `q`      | Large prime number             |
| `n`      | `p × q`                        |
| `e`      | Public exponent                |
| `d`      | Private exponent               |
| `m`      | Original message / plaintext   |
| `c`      | Encrypted message / ciphertext |

### Simplified Example

If:

```text
p = 157
q = 199
```

Then:

```text
n = p × q = 31243
```

The public key is:

```text
(n, e)
```

The private key is:

```text
(n, d)
```

A message is encrypted using the public key and decrypted using the private key.

### RSA in CTFs

RSA appears frequently in cryptography CTF challenges.

You may be given some combination of:

`p`, `q`, `n`, `e`, `d`, `m`, and `c`

and need to calculate missing values or decrypt the ciphertext.

### Key Takeaway

RSA is based on **asymmetric cryptography** and the difficulty of **factoring very large numbers**.

Remember:

**Public key = `(n, e)`**

**Private key = `(n, d)`**

**`m` = plaintext**

**`c` = ciphertext**

## Diffie-Hellman Key Exchange

**Diffie-Hellman (DH)** is a method for two parties to establish a **shared secret key over an insecure communication channel**.

The important part is that the actual shared secret is **never directly sent across the network**.

The shared secret can then be used for **symmetric encryption**.

### Basic Process

Alice and Bob publicly agree on:

* `p` = a large prime number
* `g` = a generator

These values are **public** and can be seen by an attacker.

Each person then chooses their own private number:

* Alice chooses `a`
* Bob chooses `b`

These private values are **never shared**.

### Step 1 — Calculate Public Keys

Alice calculates:

```text
A = g^a mod p
```

Bob calculates:

```text
B = g^b mod p
```

They exchange `A` and `B`.

The public keys can be seen by an attacker, but the private values `a` and `b` remain secret.

### Step 2 — Calculate the Shared Secret

Alice uses Bob's public key and her private key:

```text
B^a mod p
```

Bob uses Alice's public key and his private key:

```text
A^b mod p
```

Both calculations produce the **same shared secret**:

```text
g^(ab) mod p
```

### Example

Public values:

```text
p = 29
g = 3
```

Private values:

```text
Alice: a = 13
Bob:   b = 15
```

Public keys:

```text
Alice: A = 3^13 mod 29 = 19
Bob:   B = 3^15 mod 29 = 26
```

They exchange `19` and `26`.

Alice calculates:

```text
26^13 mod 29 = 10
```

Bob calculates:

```text
19^15 mod 29 = 10
```

Therefore, they both have the same shared secret:

```text
Shared secret = 10
```

### Important Points

* `p` and `g` → public
* `a` and `b` → private
* `A` and `B` → public keys
* The shared secret → calculated independently by both parties
* The shared secret → never directly transmitted

### Diffie-Hellman vs RSA

Diffie-Hellman is mainly used for **key agreement**.

RSA can be used for **authentication, digital signatures and other purposes**.

In real-world security protocols, Diffie-Hellman and RSA or other cryptographic methods can be used together.

### Key Takeaway

**Diffie-Hellman allows two parties to create the same secret key without sending the secret key itself over the network.**

# SSH Authentication

## Authenticating the Server

When connecting to an SSH server for the first time, the SSH client shows the server's public key fingerprint.

```bash
ssh 10.10.244.173
```

You may see:

```text
The authenticity of host '10.10.244.173' can't be established.
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```

This is asking you to verify that you trust the server.

Once you accept the key, SSH stores it in:

```text
~/.ssh/known_hosts
```

On future connections, SSH checks the server's key against the stored key. If the key changes unexpectedly, SSH will warn you. This could indicate a **Man-in-the-Middle (MITM) attack**, where another machine is pretending to be the real server.

---

## Authenticating the Client

After verifying the server, the client also needs to prove its identity.

SSH can authenticate users with passwords, but **key-based authentication** is commonly used because it is more secure.

SSH key authentication uses a pair of keys:

* **Public key** — shared with the server.
* **Private key** — kept secret on the user's machine.

The `ssh-keygen` command can be used to generate an SSH key pair.

```bash
ssh-keygen -t ed25519
```

Common SSH key types include:

* RSA
* DSA
* ECDSA
* Ed25519

---

## SSH Private Keys

The private key must be kept secret and should be treated like a password.

Never share a private SSH key.

A passphrase can be used to encrypt the private key. The passphrase is only used locally to unlock the key and is **not sent to the SSH server**.

Private keys should have restrictive permissions so that only the owner can read or modify them.

```bash
chmod 600 private_key
```

---

## Authorised Keys

SSH keys are normally stored in:

```text
~/.ssh/
```

The server uses the following file to store public keys that are allowed to authenticate:

```text
~/.ssh/authorized_keys
```

The `authorized_keys` file contains the **public keys** that the server trusts.

The private key should remain on the client machine.

---

## Connecting Using an SSH Key

You can specify which private key SSH should use with:

```bash
ssh -i privateKeyFileName user@host
```

For example:

```bash
ssh -i id_ed25519 user@10.10.244.173
```

---

## Key Security

The basic idea is:

```text
Client                         Server
------                         ------

Private key  ────────────────>  Public key
   🔒                              🔑
Keep secret                    Can be shared
```

If someone obtains your private key, they may be able to access systems that trust that key.

**Never commit private SSH keys to GitHub.**

### Key files to remember

```text
~/.ssh/id_ed25519       → Private key
~/.ssh/id_ed25519.pub   → Public key
~/.ssh/authorized_keys  → Public keys trusted by a server
~/.ssh/known_hosts      → Server keys previously trusted by the client
```

# Digital Signatures & Certificates

## Digital Signatures

A digital signature is used to prove the **authenticity and integrity** of a digital message or document.

It can help prove:

* **Who created or signed the file**
* **That the file has not been changed**

Digital signatures use **asymmetric cryptography**.

The sender uses their **private key** to create the signature. The recipient can use the sender's **public key** to verify it.

The private key must remain secret because it is used to prove that the owner signed the document.

### Digital Signature Process

A common approach is:

1. A hash is created from the original document.
2. The hash is signed using the sender's private key.
3. The original document and digital signature are sent to the recipient.
4. The recipient uses the sender's public key to verify the signature.
5. The recipient can calculate the hash of the received document and compare it with the signed hash.

If the hashes match, this provides evidence that the document has not been changed.

### Digital Signature vs Electronic Signature

A digital signature is different from simply placing an image of a handwritten signature onto a document.

An image of a signature can easily be copied and pasted onto another document, so it does not prove the document's integrity.

A digital signature uses cryptography to provide stronger evidence of authenticity and integrity.

---

## Certificates

Digital certificates are another important use of **public-key cryptography**.

Certificates help prove the identity of websites and are commonly used with **HTTPS**.

For example, when visiting a website such as `tryhackme.com`, your browser needs to know that it is communicating with the legitimate website.

The website uses a **TLS certificate** to prove its identity.

---

## Certificate Authorities (CA)

A **Certificate Authority (CA)** is a trusted organisation that issues and signs digital certificates.

Certificates use a **chain of trust**.

For example:

```text
Root CA
   ↓
Trusted organisation / CA
   ↓
Website certificate
   ↓
Website
```

Your operating system and browser come with a list of trusted **Root Certificate Authorities**.

If a website's certificate can be traced back to a trusted Root CA, the browser can trust the certificate.

---

## HTTPS and TLS Certificates

Websites that use HTTPS use **TLS certificates** to help establish secure connections and authenticate the website.

A website owner can obtain a TLS certificate from a Certificate Authority.

**Let's Encrypt** provides free TLS certificates for domains that meet its validation requirements.

### Key Points

* Digital signatures prove **authenticity and integrity**.
* A **private key** is used to create a digital signature.
* A **public key** is used to verify the signature.
* Certificates help prove the identity of websites.
* **Certificate Authorities (CAs)** issue and sign certificates.
* Browsers and operating systems trust certain Root CAs.
* HTTPS uses **TLS certificates**.

# PGP & GPG

## What is PGP?

**PGP (Pretty Good Privacy)** is software used for:

* Encrypting files and messages
* Digital signing
* Protecting the confidentiality and integrity of information

**GnuPG (GPG)** is an open-source implementation of the OpenPGP standard.

GPG is commonly used to protect email messages and can also be used to digitally sign emails.

---

## Generating a GPG Key

A GPG key pair can be generated using:

```bash
gpg --full-gen-key
```

During key generation, you can choose:

* The type of key
* The cryptographic algorithm
* How long the key should remain valid
* Your name
* Your email address
* An optional comment

GPG supports different key types, including RSA, DSA and ECC.

---

## GPG Key Pair

Like other public-key cryptography systems, GPG uses a **public key and private key**.

* **Public key** → can be shared with other people.
* **Private key** → must be kept secret.

If someone wants to send you an encrypted message, they can encrypt it using your **public key**.

You then use your **private key** to decrypt the message.

```text
Sender
   │
   │ Encrypts using your public key
   ↓
Encrypted message
   │
   ↓
You
   │
   │ Decrypt using your private key
   ↓
Original message
```

---

## Protecting GPG Private Keys

GPG private keys can be protected with a **passphrase**, similar to SSH private keys.

A passphrase adds protection if someone obtains the private key.

In CTFs, GPG keys may sometimes need to be cracked if they are protected by a weak passphrase.

Tools such as **gpg2john** and **John the Ripper** can be used to attempt to recover a passphrase.

---

## Importing a GPG Key

If you have a backup of a GPG key, you can import it using:

```bash
gpg --import backup.key
```

This allows you to use the imported key again.

---

## Decrypting a GPG File

A GPG-encrypted file can be decrypted using:

```bash
gpg --decrypt confidential_message.gpg
```

### Key Points

* **PGP** = Pretty Good Privacy
* **GPG/GnuPG** = open-source implementation of OpenPGP
* GPG can encrypt, decrypt and digitally sign information.
* Public keys can be shared.
* Private keys must be kept secret.
* A public key can be used to encrypt a message for the key owner.
* The corresponding private key is used to decrypt it.
* GPG keys can be backed up and imported onto another computer.

# Cryptanalysis & Attacks

## Cryptography

**Cryptography** is the science of protecting communication and data using codes, ciphers and other security techniques.

## Cryptanalysis

**Cryptanalysis** is the study of methods used to break or bypass cryptographic security systems, often without knowing the secret key.

## Brute-Force Attack

A **brute-force attack** tries every possible password or key combination until the correct one is found.

The larger and more complex the password or key, the more difficult a brute-force attack becomes.

## Dictionary Attack

A **dictionary attack** tries words from a list or dictionary instead of trying every possible combination.

This is useful when a password is likely to be a common word or a combination of common words.

### Key Differences

| Attack            | How it works                                        |
| ----------------- | --------------------------------------------------- |
| Brute force       | Tries every possible combination                    |
| Dictionary attack | Tries words and common combinations from a wordlist |

## Key Takeaways

* **Cryptography** → protects data and communication.
* **Cryptanalysis** → attempts to break or bypass cryptographic security.
* **Brute force** → tries every possible combination.
* **Dictionary attack** → tries likely words or combinations from a wordlist.
* Public-key cryptography includes technologies such as **RSA, Diffie-Hellman, SSH keys, digital signatures, certificates and OpenPGP**.
* **Hashing** is a separate topic and is the next area to learn.

