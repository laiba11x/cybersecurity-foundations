# Hydra

## What is Hydra?

* **Hydra** is an online **brute-force password testing tool**.
* It automates trying usernames and passwords against authentication services.
* Instead of manually trying passwords, Hydra can use a **password list** to test many possibilities quickly.

### Common uses

Hydra can test authentication services such as:

* SSH
* FTP
* HTTP/HTTPS login forms
* SMB
* RDP
* SMTP
* SNMP
* MySQL
* PostgreSQL
* VNC
* Telnet

Hydra supports many different protocols and authentication methods.

## How Hydra Works

Basic idea:

**Username + Password List → Hydra → Authentication Service → Test credentials**

Hydra tries combinations from the supplied lists and identifies credentials that successfully authenticate.

## Why Strong Passwords Matter

Brute-force attacks are more effective against weak or commonly used passwords.

Weak passwords may be:

* Commonly used.
* Short.
* Missing special characters.
* Based on predictable words or patterns.
* Left as the application's default password.

For example, default credentials such as:

```text id="n7p4k2"
admin:password
```

should always be changed.

### Key point

Hydra demonstrates why **strong, unique passwords and changing default credentials** are important security controls.

Hydra should only be used against systems where you have permission to test.

Hydra Commands

The Hydra command depends on the service/protocol being tested.

FTP Example

hydra -l user -P passlist.txt ftp://MACHINE_IP

-l = username

-P = password list

ftp:// = FTP service

MACHINE_IP = target machine

SSH Brute Force

hydra -l <username> -P <password-list> MACHINE_IP -t 4 ssh

Options

Option

Meaning

-l

Username to test

-P

Password list

-t 4

Use 4 parallel threads

ssh

Service being tested

Example:

hydra -l root -P passwords.txt MACHINE_IP -t 4 ssh

Hydra will try the passwords from the list against the specified SSH username.

Web Form Brute Force

Hydra can also test web login forms.

First determine whether the form uses GET or POST. This can be checked using browser developer tools/network information or the page source.

POST Form Syntax

hydra -l <username> -P <wordlist> MACHINE_IP http-post-form "/:username=^USER^&password=^PASS^:F=incorrect" -V

Important Parts

Part

Meaning

-l

Username

-P

Password wordlist

http-post-form

Web form uses HTTP POST

/:

Path of the login form

username=^USER^

^USER^ is replaced with the username

password=^PASS^

^PASS^ is replaced with each password

F=incorrect

Text that appears when login fails

-V

Shows each attempt

Example Structure

/:username=^USER^&password=^PASS^:F=incorrect

The three main sections are:

/path : login fields : failure condition

Non-Default Web Port

If the web server uses a port other than the default:

hydra -l <username> -P <wordlist> MACHINE_IP http-post-form "/:username=^USER^&password=^PASS^:F=incorrect" -s <port> -V

-s <port> = specify the target service port.

Key Things to Remember

Hydra automates testing many username/password combinations.

-l = single username.

-P = password list.

-t = number of parallel tasks/threads.

-V = verbose output.

^USER^ and ^PASS^ are placeholders Hydra replaces during attempts.

For web forms, you need to know the form path, field names, HTTP method, and failure response.

Only use Hydra against systems you are authorised to test.
