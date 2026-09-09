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

## UAC Security Levels

The **User Account Control (UAC)** slider has four security levels:

1. **Always notify** — highest security. Windows asks for confirmation whenever apps or users try to make system-level changes. The screen dims.
2. **Notify for apps** — Windows asks when apps try to make changes, but not when you change Windows settings. **This is the default setting.**
3. **Notify without dimming** — same as above, but the screen does not dim.
4. **Never notify** — UAC notifications are disabled. Windows does not warn you about changes.

### Key takeaway

**Always notify = highest security**
**Never notify = lowest security**

The default Windows setting is **Notify for apps**.

## Settings & Control Panel

Windows has two main places for changing system settings:

### Settings

* Modern Windows interface for changing system settings.
* Usually the first place users go to change settings.
* Examples include network, personalisation, accounts and other system options.

### Control Panel

* Older Windows system-management interface.
* Used for more advanced or complex settings.
* Examples include uninstalling programs, managing devices and configuring certain system options.

### Programs and Features

**Control Panel → Programs → Programs and Features** shows installed applications, including:

* Application name
* Publisher
* Version

This can be useful for checking what software is installed on a system.

### Key takeaway

**Settings** is the main modern interface for changing Windows settings, while **Control Panel** provides access to many older and more advanced system-management options.

## Task Manager

**Task Manager** shows information about applications and processes currently running on Windows.

It can also show system resource usage, such as:

* **CPU** usage
* **RAM (Memory)** usage
* Disk usage
* Network usage

### Opening Task Manager

Right-click the **Taskbar** → **Task Manager**

Task Manager initially opens in a simple view. Selecting **More details** shows additional information and tabs.

### Key takeaway

**Task Manager is useful for monitoring running processes, applications and system resource usage.**

## System Configuration (MSConfig)

**System Configuration (MSConfig)** is a Windows utility mainly used for **advanced troubleshooting and diagnosing startup problems**.

It requires **administrator privileges**.

### MSConfig Tabs

* **General** — controls which services and devices Windows loads during startup.
* **Boot** — provides options for how Windows starts.
* **Services** — lists Windows services and whether they are running or stopped.
* **Startup** — startup items; on modern Windows, Task Manager is normally used to manage these.
* **Tools** — provides access to other Windows configuration and diagnostic tools.

### Startup Folder

On Windows Server, startup applications can be checked using:

`shell:startup`

Press **Win + R**, enter `shell:startup`, then press Enter.

## Advanced System Settings

Advanced System Settings can be used to configure **performance and system recovery**.

### Page File

The **page file** provides extra virtual memory on disk when physical RAM becomes full.

It can help prevent:

* Slowdowns
* Application crashes caused by running out of memory

You can view settings such as:

* Drive where the page file is stored
* Initial size
* Maximum size
* Whether Windows manages the size automatically

### Startup and Recovery

Windows can create a **crash dump file** when a critical system error occurs, such as a Blue Screen of Death (BSOD).

Crash dumps help administrators and security analysts investigate what caused a crash.

Common dump types:

* Automatic memory dump
* Kernel memory dump
* Small memory dump (256 KB)
* Complete memory dump
* None

### Key takeaway

**MSConfig helps troubleshoot Windows startup and system configuration, while Advanced System Settings provides controls for performance, virtual memory and crash recovery.**

## Computer Management

**Computer Management (`compmgmt`)** is a Windows utility for managing different parts of the system.

It has three main sections:

### 1. System Tools

* **Task Scheduler** — creates and manages tasks that run automatically at specific times or events.
* **Event Viewer** — records system events and provides an audit trail useful for troubleshooting and investigations.
* **Shared Folders** — shows folders shared over the network and users connected to them.
* **Local Users and Groups** — manages local users and groups.
* **Performance Monitor (`perfmon`)** — monitors system performance in real time or from logs.
* **Device Manager** — views and manages hardware devices.

### 2. Storage

**Disk Management** allows administrators to:

* Set up new drives
* Extend partitions
* Shrink partitions
* Assign or change drive letters

### 3. Services and Applications

**Services** shows Windows services and their status.

Service startup types include:

* **Automatic** — starts when Windows boots.
* **Manual** — starts when triggered by another process or user.
* **Disabled** — cannot run.

Service properties can show the service name, executable path and startup type.

**WMI Control** manages **Windows Management Instrumentation (WMI)**, which allows Windows systems to be managed locally or remotely.

### Cybersecurity relevance

These tools are useful for **troubleshooting, system administration and security investigations**. For example, Event Viewer can reveal suspicious activity, while Task Scheduler and Services can help identify programs configured to run automatically.

### Key takeaway

**Computer Management provides tools for managing tasks, events, users, hardware, storage and Windows services.**

## Microsoft System Information (Msinfo32)

**Microsoft System Information (`msinfo32.exe`)** provides detailed information about a Windows computer's hardware, system components and software environment.

### Main Sections

* **Hardware Resources** — information about hardware resources used by the system.
* **Components** — information about installed hardware devices, such as display and input devices.
* **Software Environment** — information about Windows software, installed software, environment variables and network connections.

### Environment Variables

Environment variables store information used by Windows and applications.

For example:

`%WINDIR%` → location of the Windows installation directory.

### Searching System Information

Msinfo32 includes a search bar that can be used to find specific information, such as **IP addresses**.

### Key takeaway

**Msinfo32 is useful for viewing detailed hardware, software, network and system configuration information.**

## Resource Monitor (Resmon)

**Resource Monitor (`resmon.exe`)** is a Windows tool used to monitor system resources and troubleshoot performance issues.

It provides information about:

* **CPU** — processor usage and processes using the CPU.
* **Memory** — RAM usage.
* **Disk** — disk activity and which processes are accessing the disk.
* **Network** — network activity and connections.

### Resource Monitor Tabs

The main tabs are:

* Overview
* CPU
* Memory
* Disk
* Network

Resource Monitor also provides **real-time graphs** showing resource usage.

### Cybersecurity relevance

Resource Monitor can help identify unusual processes, unexpected network activity or programs consuming large amounts of system resources.

### Key takeaway

**Resource Monitor (`resmon.exe`) helps monitor CPU, memory, disk and network activity in real time.**

## Windows Registry

The **Windows Registry** is a central hierarchical database that stores configuration information used by Windows, applications, users and hardware.

It contains information such as:

* User profiles
* Installed applications
* Application settings
* Hardware information
* Ports being used

### Registry Editor

**Registry Editor (`regedit.exe`)** is used to view and edit the Windows Registry.

⚠️ **Be careful when modifying the Registry.** Incorrect changes can affect normal Windows operation.

### Key takeaway

**The Windows Registry stores important system and application configuration information. `regedit.exe` opens the Registry Editor.**

## Windows Update

**Windows Update** is a Microsoft service that provides:

* Security updates
* Feature updates
* Bug fixes and patches
* Updates for Microsoft products such as Microsoft Defender

### Patch Tuesday

Microsoft typically releases updates on the **second Tuesday of each month**, known as **Patch Tuesday**.

Critical security updates do not have to wait until Patch Tuesday and can be released urgently when needed.

### Windows Update Command

Windows Update can also be opened using:

`control /name Microsoft.WindowsUpdate`

### Why Windows Updates Matter

Keeping Windows updated helps protect systems from known security vulnerabilities.

Windows updates may require a **restart** to complete installation. Modern Windows versions allow updates to be postponed, but they cannot be postponed indefinitely.

### Key takeaway

**Windows Update keeps Windows and Microsoft products patched and protected against known security issues.**

## Windows Security

**Windows Security** is the central place in Windows for managing security tools that protect the device and its data.

### Protection Areas

The main protection areas are:

* **Virus & threat protection** — protects against malware and other threats.
* **Firewall & network protection** — manages firewall and network security.
* **App & browser control** — helps protect against unsafe apps, files and websites.
* **Device security** — provides security features for the device and hardware.

### Status Icons

Windows Security uses colours to show the security status:

* 🟢 **Green** — device is sufficiently protected.
* 🟡 **Yellow** — a security recommendation needs attention.
* 🔴 **Red** — an issue requires immediate attention.

### Key takeaway

**Windows Security provides a central location for monitoring and managing Windows security protections.**

## Virus & Threat Protection

**Virus & threat protection** protects Windows against malware and other threats.

### Current Threats

**Scan options:**

* **Quick scan** — checks common locations where threats are found.
* **Full scan** — checks all files and running programs.
* **Custom scan** — allows you to choose specific files or locations.

**Threat history:**

* **Last scan** — shows information about the most recent scan.
* **Quarantined threats** — isolates detected threats so they cannot run.
* **Allowed threats** — threats that the user has chosen to allow.

### Virus & Threat Protection Settings

* **Real-time protection** — detects and blocks malware as it attempts to run or install.
* **Cloud-delivered protection** — provides faster protection using the latest information from Microsoft's cloud.
* **Automatic sample submission** — sends suspicious sample files to Microsoft for analysis.
* **Controlled folder access** — helps prevent malicious applications from making unauthorised changes to protected folders.
* **Exclusions** — files or folders excluded from antivirus scanning. These can create a security risk if they contain malware.
* **Notifications** — provides alerts about security and device health.

### Virus & Threat Protection Updates

**Check for updates** manually updates Microsoft Defender's security definitions.

### Ransomware Protection

**Controlled folder access** helps protect important files from ransomware and other malicious applications.

### Key takeaway

**Real-time protection detects threats as they happen, while scans can be run manually to check for malware. Be careful when allowing threats or creating antivirus exclusions.**

## Windows Firewall

A **firewall** controls network traffic entering and leaving a device through network ports. It allows or blocks traffic based on configured rules.

### Firewall Profiles

Windows Firewall has three profiles:

* **Domain** – used when the computer can authenticate to an organisation's domain.
* **Private** – used for trusted networks, such as a home network.
* **Public** – used for untrusted networks, such as public Wi-Fi in airports or cafés.

Each profile can be configured to:

* Turn the firewall on or off.
* Block all incoming connections.

**Security tip:** Keep Windows Defender Firewall enabled unless you know exactly what you are doing.

### Allow an App Through Firewall

Windows allows specific applications to communicate through the firewall. Access can be configured separately for **Private** and **Public** networks.

### Advanced Settings

Advanced Firewall settings allow administrators to configure detailed **inbound and outbound rules**.

**Command to open Windows Firewall:** `WF.msc`

### Key Takeaway

A firewall acts as a **barrier between a device and network traffic**, helping prevent unauthorised connections.

## Microsoft Defender SmartScreen

**Microsoft Defender SmartScreen** helps protect Windows against:

* Phishing websites
* Malware websites and applications
* Potentially malicious downloads

SmartScreen can be set to:

* **Warn** – alerts the user about potentially unsafe content.
* **Block** – prevents potentially unsafe content.
* **Off** – disables the protection.

### Check Apps and Files

SmartScreen checks **unrecognised apps and files downloaded from the web** to help protect the device.

## Exploit Protection

**Exploit Protection** is built into Windows and helps protect the device against attacks that attempt to exploit software vulnerabilities.

**Security tip:** Keep the default protection settings unless you know exactly what you are changing.

### Key Takeaway

SmartScreen helps prevent users from opening or downloading **potentially dangerous content**, while Exploit Protection helps defend against **software exploits**.

## Core Isolation

**Core Isolation** is a Windows security feature that helps protect important parts of the operating system from malicious attacks.

### Memory Integrity

**Memory Integrity** helps prevent attackers from inserting malicious code into **high-security processes**.

**Security tip:** Leave the default settings enabled unless you know what you are changing.

## Trusted Platform Module (TPM)

A **Trusted Platform Module (TPM)** is a hardware-based security component designed to perform **cryptographic operations** and protect sensitive security information.

TPM has physical security mechanisms that make it **tamper-resistant**, helping prevent malware from interfering with its security functions.

### Key Takeaway

* **Core Isolation** → protects important Windows processes.
* **Memory Integrity** → helps prevent malicious code from being inserted into high-security processes.
* **TPM** → provides hardware-based security and cryptographic functions.

## BitLocker

**BitLocker** is a Windows feature that **encrypts a drive** to protect data if a computer is lost, stolen, or improperly disposed of.

* It helps prevent unauthorised people from accessing data on the drive.
* BitLocker provides stronger protection when used with a **TPM (Trusted Platform Module)**.
* **TPM** helps protect encryption keys and checks that the computer has not been tampered with while offline.
* BitLocker is available on **Windows Pro** editions, not Windows Home.
* The TryHackMe VM does **not** include BitLocker.

### Key Takeaway

**BitLocker = drive encryption that protects data from unauthorised access.**

## Volume Shadow Copy Service (VSS)

**Volume Shadow Copy Service (VSS)** creates a consistent **snapshot (point-in-time copy)** of data for backup and recovery.

### Shadow Copies

* Shadow Copies are stored in the **System Volume Information** folder on protected drives.
* They can be used to:

  * Create a restore point
  * Perform a system restore
  * Configure restore settings
  * Delete restore points

### Security

Malware, especially **ransomware**, may attempt to delete Shadow Copies so that victims cannot restore their systems.

This is why having **offline or off-site backups** is important.

### Key Takeaway

**VSS → creates snapshots that can help recover data or restore Windows after an incident.**


