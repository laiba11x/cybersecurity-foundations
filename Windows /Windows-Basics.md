# Windows Basics – Applications & Security

## Applications

Applications are programs used to perform tasks on a computer.

I can:

* **Install** applications to add software.
* **Update** applications to receive security patches, bug fixes and improvements.
* **Uninstall** applications to remove software I no longer need.

Windows applications can be installed through sources such as the Microsoft Store or by downloading an `.exe` or `.msi` installer from a trusted vendor.

## Windows Update

**Windows Update** keeps Windows and some built-in components up to date.

Updates can include:

* Security patches
* Bug fixes
* Performance improvements

Keeping software updated is important for **security** because updates can fix vulnerabilities.

## Settings & Control Panel

* **Windows Settings:** Modern interface for configuring Windows.
* **Control Panel:** Older/legacy interface that still provides some administrative options.

## Task Manager

**Task Manager** allows me to monitor what is happening on the computer.

Important tabs:

* **Processes:** Running applications and processes.
* **Performance:** CPU, memory and network usage.
* **Users:** Logged-in users.
* **Details:** Detailed process information, including PIDs.
* **Services:** Windows services and their status.

**PID = Process ID**, a number used to identify a running process.

## Windows Security

Windows Security provides built-in protection against threats.

Main sections:

* **Virus & threat protection:** Detects and scans for malware.
* **Firewall & network protection:** Controls network traffic.
* **App & browser control:** Helps protect against unsafe apps and websites.
* **Device security:** Provides hardware-based security features.

## Windows Defender Firewall

A firewall monitors network traffic and uses rules to decide whether connections are **allowed or blocked**.

Network profiles:

* **Domain:** Organisation networks.
* **Private:** Trusted networks such as home networks.
* **Public:** Untrusted networks such as public Wi-Fi.

Firewall advanced settings allow me to view and create **inbound and outbound rules**.

## Key Takeaways

* Keeping applications updated helps protect against security vulnerabilities.
* **Task Manager** is useful for monitoring processes and system performance.
* **Windows Security** provides built-in protection.
* A **firewall** controls network traffic.
* Windows uses **Domain, Private and Public** network profiles.

# Windows Introduction

## Windows

**Windows** is an operating system developed by Microsoft.

It has been widely used on home computers and in corporate networks, making it an important target for **hackers and malware**.

### Windows Versions

Major versions include:

* Windows XP
* Windows Vista
* Windows 7
* Windows 8/8.1
* Windows 10
* Windows 11

Windows 11 is available in **Home** and **Pro** editions.

Microsoft also produces **Windows Server** for server environments.

### Why Windows Security Matters

Because Windows is widely used, it is an important target for cyber attacks. Understanding Windows helps cybersecurity professionals:

* Secure computers and networks
* Identify vulnerabilities
* Investigate suspicious activity
* Defend against malware
* Manage users and permissions

### TryHackMe VM

The Windows VM used in this room runs:

**Windows Server 2019 Standard**

### Key Takeaway

Windows is one of the most widely used operating systems, so understanding how it works is important for **cybersecurity and system administration**.

# Windows Desktop & GUI

The **Windows Desktop** is the main graphical user interface (**GUI**) shown after logging into Windows.

You normally need to log in with valid account credentials, such as a username and password.

## Main Desktop Components

* **Desktop** → contains shortcuts to programs, files and folders.
* **Start Menu** → provides access to apps, programs, files, settings and power options.
* **Search** → searches for apps, files, settings and information.
* **Task View** → helps view and switch between open windows/desktops.
* **Taskbar** → shows open and pinned applications.
* **Toolbars** → provide quick access to certain tools or functions.
* **Notification Area** → displays information such as the time, date, network and volume.

## Desktop

The Desktop contains shortcuts to commonly used programs, files and folders.

Right-clicking the Desktop provides options such as:

* Changing icon size and arrangement
* Creating new folders or files
* Copying and pasting
* Opening Display settings
* Personalising the Desktop

**Display settings** can be used to configure screen resolution, orientation and multiple displays.

**Personalize** allows you to change the background, themes, colours and other appearance settings.

## Start Menu

The **Start Menu** provides access to installed applications, files, settings and power options.

It can be opened by clicking the **Windows logo**.

The Start Menu includes:

* User/account options
* Settings
* Documents and Pictures
* Installed applications
* Recently added applications
* App tiles
* Power options such as restart and shutdown

Applications can be pinned to the Start Menu for quick access.

## Taskbar

The **Taskbar** displays applications that are currently open or have been pinned.

It allows you to:

* Switch between open applications
* Launch pinned applications
* Preview open windows
* Access other system features

## Notification Area

The **Notification Area** is usually located at the bottom-right of the screen.

It can display:

* Date and time
* Network connection
* Volume
* Other system notifications

### Key Takeaway

The Windows GUI makes it easier for users to interact with the operating system using **windows, icons, menus and other visual elements** instead of only using commands.

# Windows File System & NTFS

## NTFS

**NTFS (New Technology File System)** is the main file system used by modern Windows computers and servers.

Older file systems include:

* FAT16/FAT32
* HPFS

NTFS is a **journaling file system**, meaning it keeps a log that helps Windows recover and repair the file system after a failure.

### Advantages of NTFS

* Supports files larger than 4GB
* Allows permissions on files and folders
* Supports file and folder compression
* Supports encryption using **EFS (Encrypting File System)**

## NTFS Permissions

NTFS allows permissions to **allow or deny access** to files and folders.

Common permissions:

* Full control
* Modify
* Read & Execute
* List folder contents
* Read
* Write

To view permissions:
**Right-click → Properties → Security**

## Alternate Data Streams (ADS)

**Alternate Data Streams (ADS)** is a feature of NTFS that allows a file to contain additional hidden streams of data.

Windows Explorer does not normally show ADS.

### Security importance

Attackers and malware can use ADS to **hide data or malicious files**.

ADS is not always malicious. Windows can also use it to store information about files downloaded from the Internet.

### Key takeaway

**NTFS provides Windows with file storage, permissions, encryption, compression and journaling. ADS is an NTFS feature that can hide additional data and is therefore relevant to cybersecurity.**

## Windows System Folders

### C:\Windows

The **Windows folder** contains the files that make up the Windows operating system.

* Usually located at `C:\Windows`
* It can technically be located on another drive or in another folder.
* `%windir%` is the **environment variable** that points to the Windows directory.

### Environment Variables

Environment variables store information about the operating system, such as:

* System paths
* Number of processors
* Location of temporary folders

### System32

`C:\Windows\System32` contains important files and tools that are critical to Windows.

⚠️ **Be careful when modifying System32.** Accidentally deleting or changing important files can make Windows stop working.

Many Windows tools used for administration and cybersecurity are located in **System32**.

## User Accounts

Windows local user accounts are mainly:

* **Administrator** — can make system-level changes, such as adding/removing users, changing settings and modifying groups.
* **Standard User** — has limited permissions and generally cannot make system-level changes.

### User Profiles

User profiles are stored in:

`C:\Users`

For example:

`C:\Users\Max`

Common profile folders include:

* Desktop
* Documents
* Downloads
* Music
* Pictures

### Local Users and Groups

Windows provides **Local Users and Groups** to manage local accounts and groups.

Open it using:

`lusrmgr.msc`

Groups have their own permissions. When a user is added to a group, they **inherit the permissions** assigned to that group.

A user can belong to multiple groups.

### Key takeaway

**Administrators have higher privileges, while Standard Users have limited permissions. Groups can be used to manage permissions for multiple users.**

## User Account Control (UAC)

**UAC (User Account Control)** is a Windows security feature that helps prevent unauthorised system-level changes.

Even when an administrator is logged in, Windows normally does **not** run everything with elevated privileges.

When an action requires higher privileges, UAC asks the user to confirm or provide administrator credentials.

### Why UAC is important

Running with elevated privileges all the time increases the risk of malware compromising the system.

UAC helps reduce this risk by requiring approval for actions that need higher privileges.

### UAC Shield Icon

A **shield icon** on a program indicates that opening or running it may trigger a UAC prompt.

### Important

UAC does **not** normally apply to the built-in local Administrator account in the same way it does to other administrator accounts.

### Key takeaway

**UAC reduces the risk of malware and unwanted changes by requiring approval for actions that need elevated privileges.**

