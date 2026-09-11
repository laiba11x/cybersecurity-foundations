# Hash Functions

## What is a Hash Function?

A **hash function** takes input data of any size and produces a fixed-size output called a **hash** or **digest**.

Unlike encryption, hashing does not use a key and is designed to be **one-way**. It should be computationally impractical to work backwards from the hash to the original input.

A good hash function should:

* Accept data of any size.
* Produce a fixed-size output.
* Be fast to calculate.
* Be difficult to reverse.
* Produce a significantly different hash when the input changes, even slightly.

This last property is sometimes called the **avalanche effect**.

For example, changing one bit from `T` to `U` produces completely different hashes.

---

## Common Hashing Algorithms

Common hashing algorithms include:

* **MD5**
* **SHA-1**
* **SHA-256**
* **SHA-512**

Linux provides commands for calculating these hashes:

```bash
md5sum file.txt
sha1sum file.txt
sha256sum file.txt
sha512sum file.txt
```

Hash outputs are commonly displayed in **hexadecimal**.

---

## Why is Hashing Important?

Hashing is commonly used for:

* Checking **data integrity**
* Storing and verifying **passwords**
* Detecting whether files have been modified

### Passwords

Secure systems should not store passwords directly.

Instead, they can store a hash of the password.

When a user logs in:

1. The user enters their password.
2. The system hashes the entered password.
3. The resulting hash is compared with the stored password hash.
4. If they match, the password is considered correct.

---

## Hash Collisions

A **hash collision** occurs when two different inputs produce the same hash output.

Hash functions are designed to make collisions extremely difficult to find.

However, collisions are mathematically unavoidable because there can be an unlimited number of possible inputs but a fixed number of possible hash outputs.

This is related to the **pigeonhole principle**.

For example, a 4-bit hash can only have:

```text
2^4 = 16
```

possible outputs.

If there are more than 16 different inputs, at least two inputs must eventually produce the same output.

Good hash functions make the probability of finding a collision extremely small.

---

## MD5 and SHA-1

**MD5** and **SHA-1** are considered insecure for security-sensitive hashing because researchers have demonstrated practical collision attacks against them.

They should not be relied on for protecting passwords or verifying the integrity of important security-sensitive data.

Modern applications should use stronger algorithms such as **SHA-256** where appropriate.

---

## Key Points

* A hash function converts input into a fixed-size hash.
* Hashing is designed to be **one-way**.
* Hashing does not use a key like encryption does.
* A small change to the input should produce a very different hash.
* Hashes can be used to verify **data integrity**.
* Passwords should be stored as secure password hashes rather than plaintext.
* A **collision** occurs when two different inputs produce the same hash.
* MD5 and SHA-1 are considered insecure against collision attacks.

# Hash Functions

## Password Storage

Hashing is commonly used to store passwords securely for authentication.

When logging in, a system does not need to know the original password. It can hash the password entered by the user and compare the result with the stored hash.

### Why plaintext passwords are insecure

Storing passwords in plaintext means the actual password is saved in the database.

If the database is leaked:

* Attackers can immediately see the passwords.
* Users who reuse passwords on other websites are also at risk.

### RockYou breach

RockYou stored passwords in plaintext and suffered a data breach.

The leaked `rockyou.txt` file became a commonly used password wordlist containing millions of passwords.

On Kali Linux, it can be found at:

```bash
/usr/share/wordlists/rockyou.txt
```

Useful commands:

```bash
wc -l /usr/share/wordlists/rockyou.txt
```

Counts the number of lines/passwords.

```bash
head /usr/share/wordlists/rockyou.txt
```

Displays the first few passwords.

---

## Deprecated Encryption

Some companies have stored passwords using old or insecure encryption methods instead of proper password hashing.

Encryption is reversible when the correct key is available, meaning the original password can potentially be recovered.

### Example: Adobe

Adobe's breach involved an old encryption format and plaintext password hints.

Some hints revealed information about the actual passwords, making password recovery easier.

---

## Insecure Hashing

Using a weak or outdated hashing algorithm for passwords is also dangerous.

### Example: LinkedIn

LinkedIn suffered a major data breach in 2012.

Passwords were stored using **SHA-1**, which is now considered unsuitable for secure password storage.

The passwords also lacked **salting**.

---

## Password Salting

A **salt** is a random value added to a password before hashing.

Instead of:

```text
password → hash
```

a system uses:

```text
password + random salt → hash
```

Salting makes password cracking harder because identical passwords will produce different hashes when different salts are used.

### Key points

* Never store passwords in plaintext.
* Avoid deprecated encryption methods.
* Avoid weak/outdated hashing algorithms.
* Passwords should be stored using dedicated password-hashing methods.
* Salts should be unique and random.
* Hashing is useful for authentication because the original password does not need to be recovered.

## Encryption vs Hashing

| Encryption                           | Hashing                                      |
| ------------------------------------ | -------------------------------------------- |
| Reversible                           | Designed to be one-way                       |
| Uses a key                           | Does not use an encryption key               |
| Can decrypt data                     | Cannot normally recover the original input   |
| Used when data needs to be retrieved | Used for password verification and integrity |

# Hash Functions

## Password Hashing

Instead of storing a user's actual password, a website can store a **hash of the password**.

When the user logs in:

```text
Entered password → hash → compare with stored hash
```

The original password does not need to be stored.

### Problem with identical passwords

A normal hash function always produces the same hash for the same input.

For example:

```text
password123 → same hash every time
```

If two users have the same password, they will have the same password hash.

This creates a problem because an attacker who cracks that hash could potentially compromise multiple accounts.

---

## Rainbow Tables

A **rainbow table** is a large lookup table containing:

```text
Hash → Original password
```

Example:

| Hash                               | Password |
| ---------------------------------- | -------- |
| `e10adc3949ba59abbe56e057f20f883e` | `123456` |
| `e99a18c428cb38d5f260853678922e03` | `abc123` |

Instead of calculating hashes repeatedly, an attacker can look up a stolen hash in a precomputed table.

### Important

Rainbow tables are particularly useful against **unsalted password hashes**.

Websites such as CrackStation and Hashes.com have used large databases of previously calculated hashes to perform fast lookups.

---

## Salting

A **salt** is a randomly generated value added to a password before hashing.

Instead of:

```text
password → hash
```

the process becomes:

```text
password + unique salt → hash
```

For example:

```text
Password: AL4RMc10k
Salt: Y4UV*^(=go_!
```

Combined:

```text
AL4RMc10kY4UV*^(=go_!
```

This combined value is then hashed.

### Why use a salt?

If two users have the same password, their hashes can still be different because they have different salts.

```text
User 1:
password + salt1 → hash1

User 2:
password + salt2 → hash2
```

This makes precomputed rainbow tables much less effective.

### Important facts about salts

* Salts should be **unique for each user**.
* Salts should be **random**.
* Salts do **not** need to be secret.
* The salt is normally stored alongside the password hash.
* A unique salt prevents identical passwords from producing identical hashes.

---

## Password Hashing Algorithms

Dedicated password-hashing algorithms include:

* **Argon2**
* **Scrypt**
* **Bcrypt**
* **PBKDF2**

Some of these automatically handle salt generation and storage.

### Secure password-storage process

```text
1. Choose a password-hashing algorithm
2. Generate a unique random salt
3. Add the salt to the password
4. Hash the password + salt
5. Store the hash and salt
```

---

## Why Not Encrypt Passwords?

Encryption is reversible if you have the correct key.

If passwords were encrypted:

```text
Password → Encryption → Encrypted password
```

the application would need to store or access the encryption key.

If an attacker obtains the key, they could decrypt the passwords.

For authentication, the application does not need to recover the original password, so **password hashing is preferred over encryption**.

## Key Takeaways

* Passwords should not be stored in plaintext.
* Passwords should not normally be encrypted for authentication.
* Use dedicated password-hashing algorithms.
* **Salting** protects against precomputed rainbow-table attacks.
* Each user should have a **unique salt**.
* Salts do not need to be secret.
* Examples of password-hashing algorithms: **Argon2, Scrypt, Bcrypt and PBKDF2**.
* Rainbow tables are mainly a problem for **unsalted hashes**.

# Password Hashes & Hash Identification

## Hash Identification

When an attacker finds a password hash, they first need to work out **what type of hash it is** before attempting to crack it.

Tools such as **hashID** can help identify hash types, but they are not always reliable. The best approach is to combine:

* The hash format
* Where the hash was found
* Its length and encoding
* Known prefixes
* Hash identification tools
* Research

For example, if a hash is found in a **web application database**, MD5 may be more likely than NTLM.

---

## Linux Password Hashes

Linux password hashes are normally stored in:

```text
/etc/shadow
```

This file is normally only readable by **root**.

Older Linux systems stored password hashes in `/etc/passwd`, which was readable by everyone.

### Linux Shadow File

Each line contains fields separated by `:`.

The second field contains the password information.

Linux password hashes commonly have this structure:

```text
$prefix$options$salt$hash
```

The four parts are:

* **Prefix** → identifies the hashing algorithm
* **Options** → parameters used by the algorithm
* **Salt** → random value added to the password
* **Hash** → resulting password hash

### Common Linux Hash Prefixes

| Prefix                         | Algorithm     |
| ------------------------------ | ------------- |
| `$y$`                          | yescrypt      |
| `$gy$`                         | gost-yescrypt |
| `$7$`                          | scrypt        |
| `$2b$`, `$2y$`, `$2a$`, `$2x$` | bcrypt        |
| `$6$`                          | sha512crypt   |
| `$md5`                         | SunMD5        |
| `$1$`                          | md5crypt      |

The **prefix makes Linux password hashes easier to identify**.

### Example

A modern Linux shadow entry might look like:

```text
strategos:$y$j9T$76UzfgEM5PnymhQ7TlJey1$/OOSg64dhfF.TigVPdzqiFang6uZA4QA1pzzegKdVm4:...
```

The important part is:

```text
$y$j9T$76UzfgEM5PnymhQ7TlJey1$/OOSg64dhfF.TigVPdzqiFang6uZA4QA1pzzegKdVm4
```

This can be broken down into:

* `$y$` → yescrypt
* `j9T` → algorithm parameter
* `76UzfgEM5PnymhQ7TlJey1` → salt
* The final section → hash value

---

## Windows Password Hashes

Windows uses **NTLM hashes** for password storage.

NTLM is based on **MD4**, so NTLM, MD4 and MD5 hashes can look very similar.

This means **context is important** when identifying them.

Windows password hashes are stored in the **SAM (Security Accounts Manager)**.

Windows protects the SAM from normal users, but attackers may use specialised tools to obtain password hashes.

The hashes found in the SAM can include:

* **NT hashes**
* **LM hashes**

---

## Key Takeaways

* Attackers need to identify a hash type before trying to crack it.
* Hash identification tools are useful but are not always accurate.
* Context can help identify the correct hash type.
* Linux password hashes are normally stored in `/etc/shadow`.
* Linux hashes often have a prefix that identifies the algorithm.
* Windows password hashes are stored in the SAM.
* Windows commonly uses NTLM hashes.
* NTLM can look similar to MD4 and MD5, so context matters.
* Hashcat's example hashes are useful for researching unknown hash formats.

# Password Hash Cracking

## Cracking Hashes

Password hashes **cannot be decrypted** because hashing is not encryption.

To crack a hash, an attacker:

1. Takes a possible password.
2. Hashes it using the correct algorithm.
3. Compares the result with the target hash.
4. Repeats this with many possible passwords.
5. If the hashes match, the original password has been found.

A common wordlist is **rockyou.txt**, which contains many commonly used passwords.

### Salts

A **salt** is a random value added to a password before hashing.

For a salted password, the attacker needs to account for the salt when generating guesses.

Salts make precomputed attacks such as **rainbow tables** much less useful because the same password produces different hashes when different salts are used.

### Common Tools

* **Hashcat** → commonly uses GPUs and can crack many hash types very quickly.
* **John the Ripper** → commonly uses the CPU and is useful for password cracking.

---

## GPU Cracking

GPUs have thousands of processing cores and are very good at performing certain mathematical calculations.

This makes GPUs useful for testing large numbers of password guesses quickly.

Some password-hashing algorithms, such as **bcrypt**, are designed to make GPU cracking less effective.

---

## Cracking Hashes in VMs

Virtual machines normally do not have direct access to the host's GPU.

This means GPU-based cracking can be much slower in a VM.

For Hashcat, running it directly on the **host operating system** is usually better when a suitable GPU is available.

John the Ripper mainly uses the CPU by default, so it can work inside a VM, although running it on the host can still provide better performance.

---

## Hashcat

Basic Hashcat syntax:

```text
hashcat -m <hash_type> -a <attack_mode> hashfile wordlist
```

### Options

| Option     | Meaning                         |
| ---------- | ------------------------------- |
| `-m`       | Hash type                       |
| `-a`       | Attack mode                     |
| `hashfile` | File containing the target hash |
| `wordlist` | List of password guesses        |

For example:

```text
hashcat -m 3200 -a 0 hash.txt /usr/share/wordlists/rockyou.txt
```

Here:

* `3200` = bcrypt
* `0` = straight/dictionary attack
* `hash.txt` = target hash
* `rockyou.txt` = wordlist

Another example:

```text
hashcat -m 1000 -a 0 hash.txt /usr/share/wordlists/rockyou.txt
```

Here `1000` represents **NTLM**.

## Key Takeaways

* Hashes cannot be decrypted.
* Hashes are cracked by testing possible passwords.
* Salts make precomputed rainbow-table attacks less effective.
* `rockyou.txt` is a common password wordlist.
* Hashcat can use GPUs for faster cracking.
* John the Ripper uses the CPU by default.
* VMs can be slower for password cracking because of virtualisation overhead.
* Hashcat's `-m` specifies the hash type.
* Hashcat's `-a` specifies the attack mode.

# Hashing for File Integrity & HMAC

## File Integrity

Hashing can be used to check whether a file has been changed.

The same input always produces the same hash. Even a **small change to one bit** can produce a very different hash.

This means we can:

* Check whether a downloaded file has been modified.
* Confirm a downloaded file matches the official file.
* Detect changes to important files.
* Find duplicate files.

### Example

A website might publish the official SHA-256 hash of a file.

You can calculate the SHA-256 hash of your downloaded file using:

```bash
sha256sum filename.iso
```

If your hash matches the official hash, the file is identical to the one used to generate the published hash.

### Finding Duplicate Files

If two files have the same hash, they contain the same data.

This makes hashing useful for finding duplicate files.

---

## HMAC

**HMAC** = Hash-based Message Authentication Code.

It combines:

* A cryptographic hash function
* A secret key
* A message

HMAC can provide both:

* **Integrity** → shows that the message has not been changed.
* **Authenticity** → the secret key helps prove that the message came from someone who knows the key.

### Basic Idea

```text
Message + Secret Key
        ↓
      HMAC
        ↓
   HMAC value
```

The receiver can calculate the HMAC using the same secret key and compare the result.

If the values match, the message has not been modified and the sender had the correct secret key.

### HMAC Formula

```text
HMAC(K,M) = H((K ⊕ opad) || H((K ⊕ ipad) || M))
```

Where:

* `K` = secret key
* `M` = message
* `H` = hash function
* `⊕` = XOR
* `||` = concatenation
* `ipad` = inner padding
* `opad` = outer padding

## Key Takeaways

* Hashes can detect changes to files.
* The same data produces the same hash.
* Even a tiny change can produce a very different hash.
* `sha256sum` can be used to calculate a SHA-256 file hash.
* Matching hashes indicate the files have the same data.
* Hashing can also help find duplicate files.
* HMAC combines a hash function with a secret key.
* HMAC provides **integrity and authenticity**.

# Hashing vs Encoding vs Encryption

These three concepts are different and should not be confused.

## Hashing

Hashing takes input data and produces a **fixed-size hash value**, also called a **digest**.

```text
Input → Hash function → Hash
```

Important properties:

* Hashing is **one-way**.
* You cannot normally reverse a hash to get the original data.
* The same input produces the same hash.
* A small change to the input should produce a very different hash.
* Used for **password storage**, **data integrity**, and checking whether data has changed.

Examples:

* MD5
* SHA-1
* SHA-256
* SHA-512

---

## Encoding

Encoding converts data into another format so it can be stored or transmitted correctly.

Encoding is **not a security mechanism**.

Examples of character encodings:

* ASCII
* UTF-8
* UTF-16
* UTF-32
* ISO-8859-1
* Windows-1252

Other common encoding formats include:

* Base32
* Base64

### Base64 example

```bash id="v5f5af"
echo "TryHackMe" | base64
```

Output:

```text id="v7c0dj"
VHJ5SGFja01lCg==
```

Decode it with:

```bash id="k2jq9b"
echo "VHJ5SGFja01lCg==" | base64 -d
```

Output:

```text id="3v5c4z"
TryHackMe
```

Encoding is **reversible**. Anyone with the correct encoding/decoding method can convert the data back.

---

## Encryption

Encryption protects **confidentiality**.

```text
Plaintext + Key → Encryption → Ciphertext
```

The encrypted data can be decrypted when the correct key and encryption method are available.

Encryption is used when we need to keep information **secret**.

---

## Quick Comparison

|                   | Hashing                           | Encoding            | Encryption        |
| ----------------- | --------------------------------- | ------------------- | ----------------- |
| Main purpose      | Integrity / password verification | Data representation | Confidentiality   |
| Reversible?       | No                                | Yes                 | Yes, with the key |
| Uses a key?       | No                                | No                  | Yes               |
| Protects secrecy? | No                                | No                  | Yes               |
| Example           | SHA-256                           | Base64              | AES               |

### Easy way to remember

**Hashing = one-way**

**Encoding = format conversion**

**Encryption = secret + key**
