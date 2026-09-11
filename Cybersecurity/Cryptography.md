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
