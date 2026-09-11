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
