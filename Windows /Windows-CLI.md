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

# Windows Command Prompt (CMD)

## CLI vs GUI

* **GUI (Graphical User Interface):** Uses windows, menus, buttons and icons.
* **CLI (Command-Line Interface):** Uses typed commands to interact with a computer.
* GUIs are generally easier for beginners, while CLIs become faster and more efficient once commands are familiar.

## Advantages of a CLI

### Lower Resource Usage

* CLIs use fewer system resources than graphics-heavy GUIs.
* Useful for older hardware, systems with limited memory and cloud systems.

### Automation

* Commands can be placed into scripts or batch files.
* This makes repetitive tasks easier to automate.

### Remote Management

* CLI tools such as **SSH** can be used to manage remote systems.
* Useful for servers, routers and IoT devices, especially over slower connections.

## Windows Command Prompt

* **Command Prompt (`cmd.exe`)** is the default command-line interpreter in Windows.
* It can be used to:

  * Display system information
  * Check and troubleshoot network configuration
  * Manage files and folders
  * Check running processes

## SSH

**SSH (Secure Shell)** allows you to securely connect to and manage a remote computer through a command line.

Example:

```bash
ssh user@10.130.142.186
```

The general format is:

```bash
ssh username@IP-address
```

On the first connection, SSH may ask you to confirm that you trust the remote host.

## Key Takeaway

A CLI can be faster, use fewer resources, be automated with scripts, and make remote system management easier.

## Windows CMD: Basic Commands

### PATH

* The **PATH** is a list of folders where Windows looks for executable commands.
* Use `set` to view environment variables, including the `Path` variable.

```cmd
set
```

### `ver`

* Displays the Windows operating system version.

```cmd
ver
```

### `systeminfo`

* Displays detailed information about the system, including:

  * OS information
  * Host name
  * Processor
  * Memory
  * System configuration

```cmd
systeminfo
```

### `| more`

* The **pipe (`|`)** sends the output of one command into another command.
* `more` displays long output **one page at a time**.

Example:

```cmd
driverquery | more
```

* Press **Spacebar** to view the next page.
* Press **Ctrl + C** to stop.

### `help`

* Displays help information for a command.

```cmd
help
```

### `cls`

* Clears the Command Prompt screen.

```cmd
cls
```

## Windows CMD: Network Commands

### `ipconfig`

Displays basic network configuration, including:

* IPv4 address
* IPv6 address
* Subnet mask
* Default gateway

```cmd
ipconfig
```

### `ipconfig /all`

Displays more detailed network information, including:

* MAC address
* DHCP status
* DNS servers
* IP address
* Default gateway

```cmd
ipconfig /all
```

### `ping`

Tests whether a target can be reached over the network using ICMP.

```cmd
ping example.com
```

It shows replies, packet loss and response time.

### `tracert`

**Tracert (Trace Route)** shows the network path taken to reach a target.

```cmd
tracert example.com
```

It shows the different network hops/routers along the route.

### `nslookup`

Looks up a domain name and returns its IP address using a DNS server.

```cmd
nslookup example.com
```

You can specify a DNS server:

```cmd
nslookup example.com 1.1.1.1
```

### `netstat`

Displays current network connections and listening ports.

```cmd
netstat
```

Useful options:

| Option | Purpose                                             |
| ------ | --------------------------------------------------- |
| `-a`   | Shows all connections and listening ports           |
| `-b`   | Shows the programme associated with connections/ports |
| `-o`   | Shows the process ID (PID)                          |
| `-n`   | Shows addresses and ports numerically               |

These can be combined:

```cmd
netstat -abon
```

This can show which programmes are using particular ports and their associated PIDs.

## Windows CMD: Files & Directories

### `cd`

Shows the current directory when used without a parameter.

```cmd
cd
```

Move into a directory:

```cmd
cd Users
```

Move up one level:

```cmd
cd ..
```

### `dir`

Lists files and folders in the current directory.

```cmd
dir
```

Useful options:

* `dir /a` → includes hidden and system files
* `dir /s` → includes files in subdirectories

### `tree`

Displays folders and subfolders in a tree structure.

```cmd
tree
```

### `mkdir`

Creates a new directory (folder).

```cmd
mkdir backup_files
```

### `rmdir`

Deletes a directory.

```cmd
rmdir backup_files
```

### `type`

Displays the contents of a text file.

```cmd
type file.txt
```

For longer files, use `more` to view the contents page by page.

### `copy`

Copies a file to another location.

```cmd
copy test.txt test2.txt
```

### `move`

Moves a file to another location.

```cmd
move test2.txt ..
```

### `del` / `erase`

Deletes a file.

```cmd
del test.txt
```

or

```cmd
erase test.txt
```

### Wildcards

The `*` wildcard can represent multiple files.

Example:

```cmd
copy *.md C:\Markdown
```

This copies all `.md` files into `C:\Markdown`.

## Quick Reference

| Command         | Purpose                     |
| --------------- | --------------------------- |
| `cd`            | Change/show directory       |
| `dir`           | List files and folders      |
| `tree`          | Show folder structure       |
| `mkdir`         | Create a folder             |
| `rmdir`         | Delete a folder             |
| `type`          | Display a text file         |
| `copy`          | Copy files                  |
| `move`          | Move files                  |
| `del` / `erase` | Delete files                |
| `*`             | Wildcard for multiple files |

## Process Management

### `tasklist`

Lists the currently running processes on a Windows system.

```cmd
tasklist
```

### Filtering Processes

You can filter the results to find a specific process.

```cmd
tasklist /FI "imagename eq sshd.exe"
```

* `/FI` = applies a filter
* `imagename eq` = image name equals
* `sshd.exe` = process being searched for

### `taskkill`

Terminates a running process using its **Process ID (PID)**.

```cmd
taskkill /PID 4567
```

Replace `4567` with the PID of the process you want to terminate.

## Quick Reference

| Command         | Purpose                           |
| --------------- | --------------------------------- |
| `tasklist`      | List running processes            |
| `tasklist /FI`  | Filter processes                  |
| `taskkill /PID` | Terminate a process using its PID |

## Additional Commands

Some useful commands not covered in detail:

* `chkdsk` → Checks the file system and disk volumes for errors and bad sectors.
* `driverquery` → Lists installed device drivers.
* `sfc /scannow` → Scans system files for corruption and attempts to repair them.

## Getting Help

Most Windows commands support:

```cmd
command /?
```

This displays the command's help page and available options.

## `more`

`more` can be used in two ways:

```cmd
more file.txt
```

Displays a text file one page at a time.

```cmd
some_command | more
```

Pipes long command output into `more`, allowing it to be viewed page by page.

## Key Takeaway

Windows CMD can be used to:

* View system information
* Check network configuration
* Navigate and manage files
* View and manage running processes
* Troubleshoot systems

Knowing how to use `/?` is useful when learning an unfamiliar command.

