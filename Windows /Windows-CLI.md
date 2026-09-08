# Windows CLI Basics

## What is the Windows CLI?

The Windows Command Line (CMD) is a text-based way of interacting with Windows. Instead of using the graphical interface, I can type commands to navigate the system, find files, read files, and gather system information.

Command-line skills are useful in cybersecurity because they can be faster, give more control, and are commonly used by security tools.

## Navigating Files and Folders

* `cd` — shows my current directory.
* `cd folder_name` — moves into a folder.
* `cd ..` — moves back one directory.
* `dir` — lists files and folders in the current directory.
* `dir /a` — lists files and folders, including hidden items.

### Finding and Reading Files

* `dir /s filename` — searches the current directory and its subfolders for a file.
* `type filename` — displays the contents of a text file in CMD.

Example:

```cmd
dir /s task_brief.txt
type task_brief.txt
```

## Gathering System Information

I can use the command line to quickly find information about the Windows system.

* `whoami` — shows the username of the current account.
* `hostname` — shows the computer's name.
* `systeminfo` — displays detailed Windows and system information.
* `ipconfig` — displays basic network configuration.

When using `systeminfo`, useful information includes:

* **OS Name** — Windows version/name
* **OS Version** — Windows version/build
* **System Type** — e.g. 64-bit

When using `ipconfig`, I can look for:

* **IPv4 Address** — the machine's IP address
* **Default Gateway** — the address used to reach other networks

## Key Takeaways

I learned how to:

* Navigate Windows folders using CMD.
* Find files without knowing their location.
* View hidden files and folders.
* Read text files directly from the terminal.
* Identify the current user and computer name.
* Check Windows system information.
* View basic network information.

These are useful foundational skills for IT and cybersecurity investigations.

## Windows Command Prompt (CMD)

**Command Prompt (`cmd`)** is a text-based interface used to interact with and manage Windows using commands.

### Basic Commands

| Command    | Purpose                                                    |
| ---------- | ---------------------------------------------------------- |
| `hostname` | Displays the computer name                                 |
| `whoami`   | Displays the currently logged-in user                      |
| `ipconfig` | Displays network configuration                             |
| `cls`      | Clears the Command Prompt screen                           |
| `netstat`  | Displays network statistics and current TCP/IP connections |
| `net`      | Manages network resources                                  |

### Getting Help

Most CMD commands support:

`/?`

For example:

`ipconfig /?`

This displays the command's help information and available options.

The `net` command uses different syntax:

`net help`

For a specific sub-command:

`net help user`

Other useful `net` sub-commands include:

* `user`
* `localgroup`
* `use`
* `share`
* `session`

### Cybersecurity relevance

CMD commands can quickly provide information about a Windows system, its users, network configuration and active network connections.

### Key takeaway

**CMD allows users and security professionals to interact with Windows and gather system and network information using commands.**

