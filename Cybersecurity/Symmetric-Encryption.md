# Symmetric Encryption

### Basic Terms

* **Plaintext** → the original readable message.
* **Ciphertext** → the scrambled/encrypted message.
* **Key** → secret value used by the encryption algorithm.
* **Algorithm** → the set of rules used to encrypt and decrypt data.

### Encryption & Decryption

**Encryption:**

Plaintext + Algorithm + Key → Ciphertext

**Decryption:**

Ciphertext + Algorithm + Key → Plaintext

### Symmetric Encryption

**Symmetric encryption uses the same key to encrypt and decrypt data.**

The sender and receiver both need a copy of the same secret key.

For example:

`HELLO` → encryption → `KHOOR` → decryption → `HELLO`

The algorithm can be publicly known. **The key must remain secret.**

### Caesar Cipher

The **Caesar cipher** shifts each letter by a fixed number of positions.

For example, with a key of **3**:

* A → D
* B → E
* C → F

So:

`HELLO` → `KHOOR`

To decrypt it, shift the letters backwards by 3.

The Caesar cipher is useful for learning but **is not secure enough for real-world use** because the possible keys can easily be brute-forced.

### Real-World Symmetric Encryption

A real example is **AES (Advanced Encryption Standard)**.

Symmetric encryption is:

* **Fast**
* **Efficient**
* Suitable for encrypting large amounts of data, files and network traffic.

### Key Distribution Problem

The main problem is **how to safely share the secret key**.

If someone intercepts the key, they can decrypt the encrypted data.

This is known as the **key distribution problem**.

Asymmetric encryption helps solve this problem by using two different keys.

# Asymmetric Encryption

## Key Distribution Problem

Symmetric encryption uses the **same secret key** to encrypt and decrypt data.

The problem is safely sharing that key between people who have never communicated before.

**Asymmetric encryption** solves this by using two different keys.

## Public and Private Keys

* **Public key** → can be shared with anyone.
* **Private key** → must be kept secret by the owner.

If a message is encrypted with someone's **public key**, only their **private key** can decrypt it.

### Example

Alice wants to send Bob a secret message:

**Alice → Bob's public key → Encrypted message → Bob's private key → Original message**

Alice does not need to secretly send Bob a key first.

## Mailbox Analogy

* **Public key** = open mail slot that anyone can use.
* **Private key** = key that only the mailbox owner has.

Anyone can put a message in, but only the owner can retrieve it.

## HTTPS

HTTPS uses both asymmetric and symmetric encryption.

1. Asymmetric encryption helps establish a secure connection and agree on a shared secret.
2. Symmetric encryption is then used for the rest of the session because it is much faster.

This is called a **hybrid approach**.

## Digital Certificates

A **certificate** is a digital document that:

* Contains a website's public key.
* Identifies who the key belongs to.
* Is digitally signed by a trusted **Certificate Authority (CA)**.

Browsers check that the certificate:

* Was signed by a trusted CA.
* Is still valid.
* Has not been revoked.

This helps ensure that you are communicating with the real website.

## Symmetric vs Asymmetric

| Feature     | Symmetric                        | Asymmetric                             |
| ----------- | -------------------------------- | -------------------------------------- |
| Keys        | One shared key                   | Public + private key                   |
| Key sharing | Secret key must be shared        | Public key can be shared openly        |
| Speed       | Fast                             | Slower                                 |
| Main use    | Encrypting large amounts of data | Secure key exchange and authentication |
| Example     | AES                              | RSA                                    |

## Key Takeaways

* **Symmetric encryption** = one shared secret key.
* **Asymmetric encryption** = public key + private key.
* Public keys can be shared openly.
* Private keys must remain secret.
* Asymmetric encryption solves the **key distribution problem**.
* HTTPS combines asymmetric and symmetric encryption.
* **Certificates** help prove that a public key belongs to the correct website.
* **CA (Certificate Authority)** = trusted organisation that signs certificates.


### Key Takeaway

**Symmetric encryption = one shared secret key for both encryption and decryption.**

The algorithm can be public, but the **key must remain secret**.
