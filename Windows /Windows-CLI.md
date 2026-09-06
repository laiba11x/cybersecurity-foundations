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
