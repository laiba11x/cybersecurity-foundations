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

# Linux Security – Users and File Permissions

## File Permissions

Linux uses **permissions** to control who can access files and folders.

The three basic permissions are:

| Permission | Meaning | Value |
| ---------- | ------- | ----: |
| `r`        | Read    |     4 |
| `w`        | Write   |     2 |
| `x`        | Execute |     1 |

### Permission Groups

Permissions are split into three groups:

```text
rwx rwx rwx
│   │   │
│   │   └── Others
│   └────── Group
└────────── Owner
```

### Numeric Permissions

Add the values together for each group.

For example:

```text
rwxrwxrwx
```

becomes:

```text
777
```

Because:

* `rwx` = 4 + 2 + 1 = **7**
* `rwx` = 4 + 2 + 1 = **7**
* `rwx` = 4 + 2 + 1 = **7**

### Common Examples

| Symbolic    | Numeric | Meaning                                            |
| ----------- | ------: | -------------------------------------------------- |
| `rwxr-xr-x` |   `755` | Owner has full access; others can read and execute |
| `rw-r--r--` |   `644` | Owner can read/write; others can read              |
| `rwx------` |   `700` | Only the owner has access                          |

## Users and Groups

Linux allows permissions to be assigned to:

* **Owner** – the user who owns the file
* **Group** – a group of users
* **Others** – everyone else

This allows organisations to give different users different levels of access.

## Switching Users

The `su` command allows you to **switch to another user**.

```bash
su user2
```

You normally need the user's password.

Using:

```bash
su -l user2
```

or:

```bash
su --login user2
```

starts a login shell and gives you the new user's environment and home directory.

You can check your current user with:

```bash
whoami
```

## Changing Permissions

`chmod` can be used with numeric permissions to change access.

Example:

```bash
chmod 750 system_overview.txt
```

This gives:

* **Owner:** `rwx` → full access
* **Group:** `r-x` → read and execute
* **Others:** `---` → no access

## Why Permissions Matter in Cybersecurity

Understanding permissions helps you:

* Identify who can access sensitive files
* Prevent unauthorised access
* Detect insecure permissions
* Control access to files and directories
* Understand privilege and user access

### Key takeaway

**Linux permissions control who can read, write and execute files.**

`r = 4` | `w = 2` | `x = 1`

Permissions are applied to **Owner, Group and Others**.
