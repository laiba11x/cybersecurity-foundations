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

### Key Takeaway

**Symmetric encryption = one shared secret key for both encryption and decryption.**

The algorithm can be public, but the **key must remain secret**.
