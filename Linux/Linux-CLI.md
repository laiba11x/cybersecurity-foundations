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

## SSH (Secure Shell)

**SSH (Secure Shell)** is a protocol used to **connect to and interact with a remote computer through the command line**.

### How SSH Works

SSH uses **encryption** to protect data sent between two devices.

When you enter a command:

1. You enter the command on your computer.
2. SSH encrypts the data.
3. The encrypted data travels across the network.
4. The remote machine decrypts it and executes the command.
5. The response is sent back securely.

### Why SSH Is Useful

SSH allows you to:

* Remotely execute commands on another computer
* Manage remote Linux servers
* Securely communicate over a network
* Protect data from being easily read while travelling across the network

## Flags and Switches

Many Linux commands accept **arguments** that change or extend their normal behaviour.

These are often called **flags** or **switches** and usually start with a hyphen (`-`) or double hyphen (`--`).

### Example: `ls`

Normally:

```bash
ls
```

lists the files and folders in the current directory.

To also show hidden files:

```bash
ls -a
```

`-a` means **all**.

Files and folders beginning with `.` are normally hidden.

Example:

```text
.hiddenfolder
folder1
```

### `--help`

Many commands have a `--help` option that shows available flags and a short explanation of what they do.

```bash
ls --help
```

This is useful when learning a new command.

## Man Pages

**Man pages (manual pages)** provide detailed documentation about Linux commands and applications.

Use:

```bash
man <command>
```

For example:

```bash
man ls
```

This shows information about `ls`, including its available options and how to use them.

To exit a man page, press:

```text
q
```

### Key takeaway

* **Flags/switches** → change how a command behaves
* `-a` → show hidden files with `ls`
* `--help` → shows available options
* `man <command>` → opens the command's detailed manual


### Key takeaway

**SSH = secure remote command-line access.**

## Managing Files and Folders

Linux provides commands for creating, moving, copying and deleting files and folders.

| Command | Purpose                         |
| ------- | ------------------------------- |
| `touch` | Create a blank file             |
| `mkdir` | Create a directory/folder       |
| `cp`    | Copy a file or folder           |
| `mv`    | Move or rename a file or folder |
| `rm`    | Remove a file or folder         |
| `file`  | Determine the type of a file    |

### Creating Files and Folders

Create a blank file:

```bash
touch note
```

Create a folder:

```bash
mkdir mydirectory
```

`touch` only creates the file. You can use `echo` or a text editor such as `nano` to add content.

### Removing Files and Folders

Remove a file:

```bash
rm note
```

Remove a directory and its contents:

```bash
rm -R mydirectory
```

`-R` means **recursive**.

### Copying Files

`cp` takes the existing file and the name/location of the copy.

```bash
cp note note2
```

This creates `note2` as a copy of `note`.

### Moving and Renaming

`mv` can move a file/folder or rename it.

Rename a file:

```bash
mv note2 note3
```

Move a file into another folder:

```bash
mv note mydirectory/
```

### Determining File Type

The `file` command tells you what type of file something is.

```bash
file note
```

Example output:

```text
note: ASCII text
```

A file does **not** necessarily need a file extension such as `.txt`.

### Key takeaway

* `touch` → create
* `mkdir` → create folder
* `cp` → copy
* `mv` → move/rename
* `rm` → remove
* `file` → identify file type


It allows you to control a remote machine while encrypting the data sent between the devices.
