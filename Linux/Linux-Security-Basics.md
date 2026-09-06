# Linux Security Basics

## Remote Access & User Accounts

* `ssh username@IP` — connects to a remote Linux machine using SSH.
* `whoami` — shows the current user.
* `su - username` — switches to another user.
* `su - root` — switches to the root account.
* `root` — the Linux superuser with unrestricted access.

## Useful Commands

* `ls` — lists files and folders.
* `cat filename` — displays the contents of a file.
* `history` — shows commands previously entered by the user.
* `cd /root` — moves to the root user's home directory.
* `cat /root/flag.txt` — reads a file inside the root directory.

## Security Lessons

Weak or reused passwords can allow attackers to gain access to accounts.

Command history can sometimes expose sensitive information if a user accidentally enters a password or other secret into the terminal.

Poor password practices and exposed credentials can allow an attacker to move from a normal user account to a more privileged account.
