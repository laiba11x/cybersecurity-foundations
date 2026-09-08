# Linux CLI Basics

## What is the Terminal?

The **terminal** is a text-based interface used to interact with a Linux operating system by typing commands.

The CLI is useful in cybersecurity because it provides **speed, control and access to many security tools**.

## Navigating the Linux Filesystem

### `pwd`

Shows my current directory.

```bash
pwd
```

**pwd = Print Working Directory**

### `ls`

Lists files and folders in the current directory.

```bash
ls
```

### `ls -l`

Shows detailed information about files and folders, including permissions, ownership, size and dates.

```bash
ls -l
```

### `ls -al`

Shows detailed information including **hidden files**.

```bash
ls -al
```

Linux hides files beginning with `.` by default.

### `cd`

Changes to another directory.

```bash
cd Documents
```

### `cd ..`

Moves up one directory.

```bash
cd ..
```

## Finding Files

### `find`

Searches for files and directories.

```bash
find ~ -name filename
```

`~` represents my **home directory**.

Example:

```bash
find ~ -name day1_report.txt
```

## Reading Files

### `cat`

Displays the contents of a file.

```bash
cat filename
```

Example:

```bash
cat mission_brief.txt
```

## System Information

### `whoami`

Shows the username of the current user.

```bash
whoami
```

### `uname -a`

Shows detailed system information, including the **kernel version, hostname and system architecture**.

```bash
uname -a
```

### `uname`

Shows the name of the operating system kernel.

```bash
uname
```

### `df -h`

Shows disk space usage.

```bash
df -h
```

The `-h` means **human-readable**, displaying sizes such as `68G` and `11G`.

## Linux Distribution Information

Linux stores useful system information in `/etc`.

The `/etc/os-release` file contains information about the Linux distribution.

```bash
cat /etc/os-release
```

For example, it can show that the system is running **Ubuntu 24.04.1 LTS**.

## Important Linux Concepts

* **Terminal/CLI** → interact with Linux using typed commands.
* **Filesystem** → the structure used to organise files and directories.
* **Home directory (`~`)** → the user's main directory.
* **Hidden files** → files beginning with `.` that are hidden by default.
* **`/etc`** → contains many system configuration and information files.

## Key Takeaways

* `pwd` = shows where I am.
* `ls` = shows what's around me.
* `cd` = moves between directories.
* `cd ..` = moves up one directory.
* `find` = searches for files.
* `cat` = reads files.
* `whoami` = shows who I am logged in as.
* `uname -a` = shows detailed system information.
* `df -h` = shows disk space.
* `/etc/os-release` = shows Linux distribution information.

These commands are the basic building blocks for working with Linux through the command line and will be useful for later **cybersecurity tools and investigations**.

## Who Are You on This Machine?

Linux is commonly used for **servers and cybersecurity systems**. Cybersecurity professionals often interact with Linux through the **terminal (CLI)**.

### Commands

| Command  | Purpose                |
| -------- | ---------------------- |
| `whoami` | Shows the current user |
| `echo`   | Outputs text           |

Examples:

```bash
whoami
echo TryHackMe
echo "hello world"
```

### Why `whoami` is useful

Knowing which user you are is important because different users have different **permissions and access**.

In cybersecurity, you may switch between users, so checking the current user helps you understand what you can access.

### Terminal Output

**Output** is the information the computer gives back after you run a command.

For example:

```bash
echo TryHackMe
```

outputs:

```text
TryHackMe
```

### Useful Tip

Use the **up and down arrow keys** to move through commands you have previously entered.

### Key takeaway

`whoami` → tells you **who you are**

`echo` → **outputs text**

The Linux terminal is an important cybersecurity skill because many security tools and tasks are performed through the command line.

## Finding Files and Searching Text

Linux has commands that can quickly search for files and text instead of manually looking through them.

| Command | Purpose                                 | Example                            |
| ------- | --------------------------------------- | ---------------------------------- |
| `find`  | Searches for files by name              | `find -name passwords.txt`         |
| `grep`  | Searches inside files for specific text | `grep "password123" passwords.txt` |

### `find`

Use `find` when you want to **find a file**.

```bash
find -name passwords.txt
```

### `grep`

Use `grep` when you want to **search inside a file** for specific text.

```bash
grep "password123" passwords.txt
```

### Example

If a web server log called `access.log` contains hundreds of lines, `grep` can search through it for specific text instead of checking every line manually.

### Key takeaway

**`find` → searches for files**

**`grep` → searches inside files for text**

## Shell Operators

Linux uses **operators** to combine commands or redirect their output.

| Operator | Purpose                                                                    |
| -------- | -------------------------------------------------------------------------- |
| `&`      | Runs a command in the background without waiting for it to finish          |
| `&&`     | Runs the second command only after the first command finishes successfully |
| `>`      | Sends output to a file and **overwrites** existing content                 |
| `>>`     | Sends output to a file and **adds** to the existing content                |

### Output Redirection

The `>` operator can save command output into a file.

```bash
echo "hey" > welcome
```

This creates a file called `welcome` containing `hey`.

Use `cat` to view the file:

```bash
cat welcome
```

### `>` vs `>>`

`>` **overwrites** the file:

```bash
echo "Hello" > test
```

`>>` **adds to the end** of the file:

```bash
echo "World" >> test
```

The file will now contain both lines.

### TryHackMe Practical

To complete the task:

```bash
echo "TryHackMe" > thm
```

Then add more text using:

```bash
echo "thm" >> thm
```

Check the contents with:

```bash
cat thm
```

### Key takeaway

`&` → background

`&&` → run commands in order

`>` → overwrite output into a file

`>>` → append output to a file

