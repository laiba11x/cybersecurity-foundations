# Gobuster

## What is Gobuster?

* Gobuster is an open-source offensive security tool written in **Go (Golang)**.
* It is mainly used to **enumerate** web resources by using **brute force and wordlists**.
* Common uses include:

  * Web directories and files
  * DNS subdomains
  * Virtual hosts (VHosts)
  * Amazon S3 buckets
  * Google Cloud Storage buckets
* Commonly used for penetration testing, bug bounty hunting and security assessments.
* Gobuster fits mainly between **reconnaissance and scanning** during ethical hacking.

---

## Enumeration

**Enumeration** means finding and listing available resources on a target.

For example, Gobuster can test many possible directory names to discover hidden web directories.

Example:

```text
Website
├── /
├── /admin
├── /images
├── /login
└── /backup
```

---

## Brute Force

**Brute force** means trying many possibilities until a match is found.

Gobuster uses a **wordlist** containing possible names and tests them against the target.

Example:

```text
Wordlist
   ↓
admin
login
images
backup
   ↓
Gobuster
   ↓
Target website
```

---

## Gobuster Help

To see Gobuster's available commands and options:

```bash
gobuster --help
```

### Main Modes

| Mode    | Purpose                                  |
| ------- | ---------------------------------------- |
| `dir`   | Directory and file enumeration           |
| `dns`   | DNS subdomain enumeration                |
| `vhost` | Virtual host enumeration                 |
| `fuzz`  | Fuzzing URLs, headers and request bodies |
| `s3`    | Amazon S3 bucket enumeration             |
| `gcs`   | Google Cloud Storage enumeration         |
| `tftp`  | TFTP enumeration                         |

For this room, the main modes are:

```text
dir
dns
vhost
```

---

## Common Gobuster Options

| Option              | Purpose                      |
| ------------------- | ---------------------------- |
| `-t` / `--threads`  | Number of concurrent threads |
| `-w` / `--wordlist` | Wordlist to use              |
| `--delay`           | Wait between requests        |
| `--debug`           | Show debugging information   |
| `-o` / `--output`   | Save results to a file       |
| `-q` / `--quiet`    | Reduce extra output          |
| `-v` / `--verbose`  | Show more detailed output    |

### Threads

```bash
-t 64
```

Controls how many requests can be processed concurrently.

More threads can make scans faster, but the appropriate number depends on the target and available resources.

### Wordlist

```bash
-w /path/to/wordlist.txt
```

Tells Gobuster which wordlist to use.

Gobuster tests the entries in the wordlist against the target.

### Delay

```bash
--delay 1500ms
```

Adds a delay between requests.

This can reduce the request rate sent to the server.

### Output

```bash
-o results.txt
```

Saves the scan results to a file.

---

## Directory Enumeration

Basic syntax:

```bash
gobuster dir -u "http://example.thm/" -w /path/to/wordlist.txt
```

Example:

```bash
gobuster dir -u "http://www.example.thm/" -w /usr/share/wordlists/dirb/small.txt -t 64
```

### Breaking Down the Command

```text
gobuster dir
```

Uses directory/file enumeration mode.

```text
-u "http://www.example.thm/"
```

Specifies the target URL.

```text
-w /usr/share/wordlists/dirb/small.txt
```

Specifies the wordlist.

```text
-t 64
```

Uses 64 concurrent threads.

Gobuster takes each word from the wordlist and adds it to the URL.

For example, if the wordlist contains:

```text
images
```

Gobuster tests:

```text
http://www.example.thm/images/
```

---

## Key Things to Remember

* **Gobuster = enumeration using wordlists.**
* **Enumeration** = finding/listing available resources.
* **Brute force** = trying many possibilities.
* `dir` = directories/files.
* `dns` = subdomains.
* `vhost` = virtual hosts.
* `-w` = wordlist.
* `-t` = threads.
* `-o` = save output.
* `--delay` = wait between requests.
* `--debug` = troubleshoot unexpected behaviour.
* Only enumerate systems you are authorised to test.

# Gobuster

## `dir` Mode

Gobuster's **`dir` mode** is used to enumerate:

* Website directories
* Files
* Specific file extensions

It uses a wordlist and checks each possible path against the website.

For example, a WordPress site may contain directories such as:

```text
wordpress/
├── wp-admin/
├── wp-content/
└── wp-includes/
```

Gobuster can help discover these directories from outside the web server.

---

## `dir` Mode Syntax

```bash
gobuster dir -u "http://www.example.thm" -w /path/to/wordlist
```

The two important options are:

| Option | Purpose    |
| ------ | ---------- |
| `-u`   | Target URL |
| `-w`   | Wordlist   |

The URL must include the protocol, such as `http://` or `https://`.

---

## Important `dir` Options

| Flag | Long option                | Purpose                             |
| ---- | -------------------------- | ----------------------------------- |
| `-c` | `--cookies`                | Send cookies with requests          |
| `-x` | `--extensions`             | Search for specific file extensions |
| `-H` | `--headers`                | Add an HTTP header                  |
| `-k` | `--no-tls-validation`      | Ignore TLS certificate validation   |
| `-n` | `--no-status`              | Hide status codes                   |
| `-P` | `--password`               | Password for authenticated requests |
| `-s` | `--status-codes`           | Show selected status codes          |
| `-b` | `--status-codes-blacklist` | Hide selected status codes          |
| `-U` | `--username`               | Username for authenticated requests |
| `-r` | `--followredirect`         | Follow HTTP redirects               |

---

## Basic Directory Scan

```bash
gobuster dir -u "http://www.example.thm" -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -r
```

### Breaking It Down

```text
gobuster dir
```

Uses directory/file enumeration mode.

```text
-u "http://www.example.thm"
```

Specifies the target URL.

```text
-w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
```

Specifies the wordlist.

```text
-r
```

Tells Gobuster to follow redirects such as HTTP `301` or `302` responses.

---

## Status Codes

Gobuster can display the HTTP status code returned for each request.

These codes help show what happened when Gobuster requested a path.

Examples:

| Status | Meaning                |
| ------ | ---------------------- |
| `200`  | Request successful     |
| `301`  | Permanently redirected |
| `302`  | Temporarily redirected |
| `403`  | Forbidden              |
| `404`  | Not found              |

The `-s` option can be used to specify which status codes to display.

```bash
-s 200
```

You can also specify a range:

```bash
-s 300-400
```

`-b` can be used to blacklist status codes instead.

---

## File Extensions

The `-x` option allows Gobuster to search for specific file types.

Example:

```bash
gobuster dir -u "http://www.example.thm" -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x .php,.js
```

This searches for:

```text
.php
.js
```

For example, Gobuster may test:

```text
/login.php
/admin.php
/script.js
```

---

## Important Points

* `dir` mode finds **directories and files**.
* `-u` specifies the **target URL**.
* `-w` specifies the **wordlist**.
* `-r` follows redirects.
* `-x` searches for specific file extensions.
* Gobuster **does not scan recursively**.
* If Gobuster finds an interesting directory, you need to scan that directory separately.
* Using the **hostname** can be important when a server hosts multiple websites on the same IP through virtual hosting.
* Only enumerate websites you are authorised to test.

# Gobuster

## `dns` Mode

Gobuster's **`dns` mode** is used to enumerate **DNS subdomains**.

For example, if a company owns:

```text
example.thm
```

there could also be:

```text
www.example.thm
shop.example.thm
mail.example.thm
```

Finding subdomains is important during security testing because they may contain different applications, services or vulnerabilities.

---

## `dns` Mode Syntax

```bash
gobuster dns -d example.thm -w /path/to/wordlist
```

The two important options are:

| Option | Purpose       |
| ------ | ------------- |
| `-d`   | Target domain |
| `-w`   | Wordlist      |

---

## Common DNS Options

| Flag | Long option    | Purpose                                  |
| ---- | -------------- | ---------------------------------------- |
| `-d` | `--domain`     | Domain to enumerate                      |
| `-w` | `--wordlist`   | Wordlist containing possible subdomains  |
| `-i` | `--show-ips`   | Show IP addresses the domains resolve to |
| `-c` | `--show-cname` | Show CNAME records                       |
| `-r` | `--resolver`   | Use a custom DNS resolver                |

`-c` and `-i` cannot be used together.

---

## DNS Enumeration Example

```bash
gobuster dns -d example.thm -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt
```

Gobuster takes each entry from the wordlist and creates a DNS query.

For example, if the wordlist contains:

```text
shop
```

Gobuster tests:

```text
shop.example.thm
```

If it exists, Gobuster reports it.

Example results:

```text
Found: www.example.thm
Found: shop.example.thm
Found: academy.example.thm
Found: primary.example.thm
```

---

## Showing IP Addresses

Use:

```bash
gobuster dns -d example.thm -w /path/to/wordlist -i
```

The `-i` option displays the IP addresses associated with discovered subdomains.

---

## Using a Custom DNS Resolver

Use:

```bash
gobuster dns -d example.thm -w /path/to/wordlist -r <DNS_SERVER>
```

The `-r` option specifies which DNS server Gobuster should use for resolving names.

This can be useful in lab environments where a specific DNS server is required.

---

## Key Things to Remember

* `dns` = DNS subdomain enumeration.
* `-d` = target domain.
* `-w` = wordlist.
* `-i` = show resolved IP addresses.
* `-c` = show CNAME records.
* `-r` = specify a DNS resolver.
* Gobuster builds possible subdomains from the wordlist and checks whether they exist.
* Finding subdomains can reveal additional applications and services.
* Only enumerate domains you are authorised to test.

# Gobuster

## `vhost` Mode

Gobuster's **`vhost` mode** is used to enumerate **virtual hosts**.

A virtual host is a different website hosted on the **same server/IP address**.

Virtual hosts can look like subdomains, but they work differently:

* **DNS mode** → performs DNS lookups to find subdomains.
* **VHost mode** → sends web requests to the same server while changing the `Host` header.

---

## DNS vs VHost

| Mode    | How it works                                      |
| ------- | ------------------------------------------------- |
| `dns`   | Performs DNS lookups for possible subdomains      |
| `vhost` | Sends HTTP requests with different `Host` headers |

For example, with VHost enumeration, Gobuster may send:

```http
GET / HTTP/1.1
Host: www.example.thm
```

Then:

```http
GET / HTTP/1.1
Host: blog.example.thm
```

The server may respond differently depending on the `Host` header.

---

## Basic Syntax

```bash
gobuster vhost -u "http://example.thm" -w /path/to/wordlist
```

The required options are:

| Option | Purpose           |
| ------ | ----------------- |
| `-u`   | Base URL / target |
| `-w`   | Wordlist          |

---

## Common VHost Options

| Flag               | Long option         | Purpose                                   |
| ------------------ | ------------------- | ----------------------------------------- |
| `-u`               | `--url`             | Base URL                                  |
| `-w`               | `--wordlist`        | Wordlist                                  |
| `--domain`         |                     | Domain to append to wordlist entries      |
| `--append-domain`  |                     | Appends the domain to each wordlist entry |
| `--exclude-length` |                     | Filters responses based on response size  |
| `-m`               | `--method`          | HTTP method such as GET or POST           |
| `-r`               | `--follow-redirect` | Follow HTTP redirects                     |

---

## Example

```bash
gobuster vhost -u "http://10.130.157.241" --domain example.thm -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt --append-domain --exclude-length 250-320
```

### Breaking It Down

```text
gobuster vhost
```

Uses VHost enumeration mode.

```text
-u "http://10.130.157.241"
```

Specifies the server/IP to send requests to.

```text
-w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt
```

Specifies the wordlist.

```text
--domain example.thm
```

Specifies the domain used to construct the hostnames.

```text
--append-domain
```

Adds the domain to each word from the wordlist.

For example:

```text
blog
```

becomes:

```text
blog.example.thm
```

```text
--exclude-length 250-320
```

Filters out responses with those response-body sizes.

This is useful for removing **false positives**.

---

## False Positives

A web server may return the same response for many hostnames that don't actually exist.

For example:

```text
Found: random.example.thm Status: 404 [Size: 279]
Found: test.example.thm Status: 404 [Size: 279]
```

These can be false positives because the server is returning the same response size.

`--exclude-length` can filter these responses.

A genuine virtual host may return something different, such as:

```text
Found: blog.example.thm Status: 200 [Size: 1493]
```

---

## Key Things to Remember

* `vhost` = virtual host enumeration.
* VHosts can host multiple websites on the same IP.
* VHost enumeration changes the **Host header** in HTTP requests.
* `-u` = target URL.
* `-w` = wordlist.
* `--domain` = domain used to construct hostnames.
* `--append-domain` = adds the domain to each word.
* `--exclude-length` = filters response sizes to reduce false positives.
* `dns` finds subdomains through DNS.
* `vhost` tests different hostnames against the same web server.
* Only perform enumeration against systems you are authorised to test.
