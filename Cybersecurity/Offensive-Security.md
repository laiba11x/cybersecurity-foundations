# Offensive Security

## What is Offensive Security?

**Offensive security** focuses on proactively testing systems by attempting to find and exploit weaknesses before real attackers can.

The goal is to identify vulnerabilities so they can be fixed and systems can be made more secure.

### Ethical Hacking

Ethical hacking is the **legal and authorised** practice of testing systems for security weaknesses.

A penetration tester thinks like an attacker but works with permission.

## Questions an Attacker Asks

When testing a system, an attacker may ask:

* What is exposed?
* What can be accessed?
* What assumptions does the system make?
* How does the system respond to unexpected input?

Testing is performed methodically to discover weaknesses.

## Why Offensive Security is Important

Offensive security helps organisations:

* Find vulnerabilities before attackers do.
* Understand how an attacker could compromise a system.
* Improve security controls.
* Reduce the risk of successful attacks.

## Key Terms

* **Offensive Security** — proactively finding and testing security weaknesses.
* **Ethical Hacking** — legally hacking systems with permission to improve security.
* **Penetration Testing** — authorised security testing that attempts to identify and exploit vulnerabilities.

## Practical Environment

TryHackMe provides a **safe, permission-based environment** where offensive security techniques can be practised legally.

### Prerequisites

Basic knowledge of:

* How computers work.
* Using a command-line interface (CLI).
* Basic networking and web technologies.

## Key Takeaway

**Offensive security = think like an attacker to find weaknesses before real attackers can exploit them.**

# Offensive Security

## Core Terminology

* **Red Teaming** — an authorised attack that simulates a real attacker to test security defences.
* **Penetration Test** — an authorised security assessment that attempts to find and exploit vulnerabilities within a defined scope.
* **Vulnerability** — a weakness or flaw that an attacker could take advantage of.
* **Exploit** — a technique used to take advantage of a vulnerability.
* **Scope** — defines what systems and actions are allowed to be tested and what is off-limits.
* **Ethical Hacking** — legally testing systems with explicit permission to identify security weaknesses.

### ⚠️ Permission is Essential

Ethical hacking must always be **authorised** and performed within the agreed **scope**.

The goal is to find weaknesses and help improve security, **not to cause damage**.

## Web Application Assessment

A basic assessment can start by looking for **hidden pages** that should not be publicly accessible.

For example, you can manually test different paths:

```text
http://www.onlineshop.thm/sitemap
http://www.onlineshop.thm/mail
http://www.onlineshop.thm/register
http://www.onlineshop.thm/login
http://www.onlineshop.thm/admin
```

A page that does not exist usually returns a **404 Not Found** response.

## Gobuster

**Gobuster** is a command-line tool that can automatically discover hidden directories and files on a web server.

Example:

```bash
gobuster dir --url http://www.onlineshop.thm/ -w /usr/share/wordlists/dirbuster/directory-list.txt
```

### Command Breakdown

* `gobuster` → starts Gobuster.
* `dir` → directory/file enumeration mode.
* `--url` → specifies the target website.
* `-w` → specifies the wordlist containing possible directory/file names.

### Key Takeaway

Instead of manually testing hundreds of possible URLs, tools such as **Gobuster** can automate the discovery of hidden web content.

**Offensive security process:**
`Find → Investigate → Exploit → Report → Fix`
# Chaining Weaknesses

## Chaining Vulnerabilities

A single weakness may not be very dangerous by itself, but multiple weaknesses can be **chained together** to create a bigger security risk.

Example:

**Hidden login page → weak password → unauthorised login → access to admin features**

### Think Like a Hacker

Ethical hackers ask:

* What if a feature doesn't work as intended?
* Can unexpected inputs cause problems?
* Can small weaknesses be combined?
* How would an attacker approach the target?

## Why Credentials Are Valuable

Attackers may try to obtain usernames and passwords because authenticated access can provide access to:

* **Sensitive functionality** — restricted actions or data.
* **User data** — names, emails and account information.
* **Administrative features** — managing users and settings.
* **Further attack opportunities** — additional weaknesses inside the application.

## Dictionary Attack

A **dictionary attack** automatically tries a list of possible passwords against a login.

Instead of manually testing hundreds of passwords, a tool can test a **wordlist** automatically.

## Hydra

**Hydra** is a tool that can automate login attempts using a wordlist.

Example:

```bash
hydra -l admin -P passlist.txt www.onlineshop.thm http-post-form "/login:username=^USER^&password=^PASS^:F=incorrect" -V
```

### Command Breakdown

* `-l admin` → username to test.
* `-P passlist.txt` → password wordlist.
* `www.onlineshop.thm` → target website.
* `http-post-form` → login uses an HTTP POST form.
* `F=incorrect` → tells Hydra what indicates a failed login.
* `-V` → shows each login attempt.

### Key Takeaway

**Dictionary attack = automatically trying many possible passwords from a wordlist.**

Hydra can make this process much faster during an **authorised penetration test**.

⚠️ Password testing should only be performed against systems you have permission to test.


## Key Terminology

* **Scope** — the exact systems and actions allowed during a security test.
* **Vulnerability** — a weakness in a system that an attacker could exploit.
* **Exploit** — a method or technique used to take advantage of a vulnerability.
* **Enumeration** — collecting information about a system, users and services to identify possible weaknesses.
* **Credentials** — login details such as usernames and passwords.
* **Authentication** — checking whether someone or something is really who they claim to be.
* **Dictionary Attack** — trying passwords from a predefined wordlist.

## Career Opportunities

* **Penetration Tester / Ethical Hacker** — safely identifies and tests vulnerabilities within an authorised scope.
* **Vulnerability Researcher** — identifies and validates previously unknown weaknesses in software or hardware.
* **Red Team Operator** — simulates real-world attacks to test an organisation's detection and response.

## Continuing Cybersecurity Learning

Cybersecurity has many different areas, including:

* Offensive security
* Defensive security
* Networking
* Web security
* Vulnerability research

A good way to improve is to practise regularly using hands-on labs and gradually build skills in areas that interest you.

### Key Takeaway

Ethical hacking involves **finding vulnerabilities, understanding how they can be exploited, and helping organisations fix them before real attackers do.**
