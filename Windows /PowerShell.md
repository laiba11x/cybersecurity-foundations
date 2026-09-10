# Windows PowerShell

## What is PowerShell?

* **PowerShell** is a Microsoft tool for **task automation and configuration management**.
* It provides:

  * A command-line shell
  * A scripting language
  * A configuration management framework
* It was originally designed for Windows but **PowerShell Core** is cross-platform and works on Windows, macOS and Linux.
* PowerShell is particularly useful for system administration and automation.

## PowerShell vs CMD

* CMD mainly works with **text-based output**.
* PowerShell works with **objects**.
* Objects contain:

  * **Properties** → information/characteristics
  * **Methods** → actions that can be performed
* Working with objects makes it easier to filter, manipulate and manage complex information without manually parsing text.

## History

* PowerShell was developed to overcome limitations of traditional Windows command-line tools and batch files.
* It was released in **2006**.
* **PowerShell Core** was released in **2016** as an open-source, cross-platform version.

## Key Terms

| Term           | Meaning                                            |
| -------------- | -------------------------------------------------- |
| **PowerShell** | Microsoft's command-line and scripting environment |
| **Cmdlet**     | A PowerShell command                               |
| **Object**     | Data containing properties and methods             |
| **Property**   | A characteristic/value of an object                |
| **Method**     | An action an object can perform                    |

### Key Takeaway

**CMD → mainly text**

**PowerShell → objects**

PowerShell's object-based approach makes system administration, automation and scripting more powerful and flexible.

# PowerShell – Basic Commands

## Launching PowerShell

PowerShell can be opened in several ways:

* Start Menu → search **PowerShell**
* `Win + R` → type `powershell`
* From **Command Prompt**, type `powershell`
* File Explorer address bar → type `powershell`

### PowerShell Prompt

```powershell
PS C:\Users\captain>
```

`PS` shows that the current shell is PowerShell.

---

## Cmdlets

PowerShell commands are called **cmdlets** (command-lets).

They normally follow the:

**Verb-Noun** format

Examples:

* `Get-Content` → gets the contents of a file
* `Set-Location` → changes the current directory
* `Get-Date` → gets the current date and time

The **Verb** describes the action and the **Noun** describes what the action operates on.

---

## Get-Command

`Get-Command` lists commands available in the current PowerShell session.

```powershell
Get-Command
```

You can filter commands by type:

```powershell
Get-Command -CommandType "Function"
```

---

## Get-Help

`Get-Help` provides information about how to use a cmdlet.

```powershell
Get-Help Get-Date
```

Useful options include:

```powershell
Get-Help Get-Date -Examples
Get-Help Get-Date -Detailed
Get-Help Get-Date -Full
```

---

## Aliases

PowerShell has **aliases**, which are shortcuts or alternative names for commands.

```powershell
Get-Alias
```

Examples:

| Alias | Cmdlet           |
| ----- | ---------------- |
| `cd`  | `Set-Location`   |
| `dir` | `Get-ChildItem`  |
| `cat` | `Get-Content`    |
| `%`   | `ForEach-Object` |
| `?`   | `Where-Object`   |

---

## PowerShell Modules

**Modules** are collections of PowerShell commands/cmdlets.

`Find-Module` searches online repositories such as the **PowerShell Gallery**:

```powershell
Find-Module -Name "PowerShell*"
```

`Install-Module` downloads and installs a module:

```powershell
Install-Module -Name "PowerShellGet"
```

**Note:** These commands require an internet connection. The TryHackMe machine may not have internet access, so they may not work in the lab.

# PowerShell – File and Directory Management

PowerShell uses cmdlets to navigate and manage files and directories.

| Cmdlet          | What it does                  | CMD equivalent          |
| --------------- | ----------------------------- | ----------------------- |
| `Get-ChildItem` | Lists files and directories   | `dir`                   |
| `Set-Location`  | Changes the current directory | `cd`                    |
| `New-Item`      | Creates a file or directory   | `mkdir` / file creation |
| `Remove-Item`   | Deletes files or directories  | `del` / `rmdir`         |
| `Copy-Item`     | Copies files or directories   | `copy`                  |
| `Move-Item`     | Moves files or directories    | `move`                  |
| `Get-Content`   | Displays file contents        | `type`                  |

### Examples

List the current directory:

```powershell
Get-ChildItem
```

Change directory:

```powershell
Set-Location -Path .\Documents
```

Create a directory:

```powershell
New-Item -Path .\folder -ItemType Directory
```

Create a file:

```powershell
New-Item -Path .\file.txt -ItemType File
```

Delete a file or directory:

```powershell
Remove-Item -Path .\file.txt
```

Copy an item:

```powershell
Copy-Item -Path .\file.txt -Destination .\file2.txt
```

Move an item:

```powershell
Move-Item -Path .\file.txt -Destination .\Documents
```

Read a file:

```powershell
Get-Content -Path .\file.txt
```

### Key takeaway

PowerShell often uses **one cmdlet for both files and directories**, such as `New-Item` and `Remove-Item`.

# PowerShell – Piping and Filtering

## Piping

The **pipe `|`** sends the output of one command to another command.

PowerShell is especially powerful because it passes **objects**, not just text. Objects contain data, properties, and methods.

Example:

```powershell
Get-ChildItem | Sort-Object Length
```

This gets files and sorts them by their `Length` (size).

---

## Sort-Object

Sorts objects based on a property.

```powershell
Get-ChildItem | Sort-Object Length
```

Sort largest first:

```powershell
Get-ChildItem | Sort-Object Length -Descending
```

---

## Where-Object

Filters objects based on a condition.

Show only `.txt` files:

```powershell
Get-ChildItem | Where-Object -Property Extension -eq .txt
```

Useful comparison operators:

| Operator | Meaning                  |
| -------- | ------------------------ |
| `-eq`    | Equal to                 |
| `-ne`    | Not equal to             |
| `-gt`    | Greater than             |
| `-ge`    | Greater than or equal to |
| `-lt`    | Less than                |
| `-le`    | Less than or equal to    |
| `-like`  | Matches a pattern        |

Example:

```powershell
Get-ChildItem | Where-Object -Property Name -like ship*
```

---

## Select-Object

Selects specific properties or limits the number of objects returned.

```powershell
Get-ChildItem | Select-Object Name,Length
```

To display only the first result:

```powershell
Select-Object -First 1
```

Example — find the largest file:

```powershell
Get-ChildItem | Sort-Object Length -Descending | Select-Object -First 1
```

---

## Select-String

Searches for text inside files.

```powershell
Select-String -Path .\captain-hat.txt -Pattern hat
```

It can also use **regular expressions (regex)** for more advanced text searching.

## Key takeaway

PowerShell pipelines can combine multiple cmdlets to **retrieve, filter, sort and display exactly the information you need**.

# PowerShell – System and Network Information

## Get-ComputerInfo

Retrieves detailed information about the computer, including:

* Operating system
* Hardware
* BIOS
* Windows version and edition

```powershell
Get-ComputerInfo
```

It provides more information than the traditional `systeminfo` command.

---

## Get-LocalUser

Lists local user accounts on the computer.

```powershell
Get-LocalUser
```

It shows information such as:

* Username
* Whether the account is enabled
* Description

---

## Get-NetIPConfiguration

Displays detailed network configuration, including:

* IP addresses
* DNS servers
* Default gateway
* Network interfaces

```powershell
Get-NetIPConfiguration
```

Similar to `ipconfig`.

---

## Get-NetIPAddress

Displays IP addresses configured on the system, including inactive addresses.

```powershell
Get-NetIPAddress
```

It can show:

* IPv4 and IPv6 addresses
* Interface
* Address family
* Prefix length
* Address state

## Key takeaway

PowerShell provides cmdlets for quickly retrieving **system, user account and network information**.

# PowerShell – Processes, Services and Network Connections

## Get-Process

Displays currently running processes, including information such as:

* Process name
* CPU usage
* Memory usage
* Process ID (PID)

```powershell
Get-Process
```

Useful for monitoring processes and troubleshooting.

---

## Get-Service

Displays services on the computer and their current status.

```powershell
Get-Service
```

Services can be:

* `Running`
* `Stopped`
* `Paused`

Useful for system administration and investigating unusual services.

---

## Get-NetTCPConnection

Displays active TCP connections, including local and remote addresses and ports.

```powershell
Get-NetTCPConnection
```

Useful for:

* Network monitoring
* Incident response
* Investigating suspicious connections

---

## Get-FileHash

Generates a hash for a file. This can be used to verify file integrity or detect changes.

```powershell
Get-FileHash -Path .\file.txt
```

The default algorithm is **SHA256**.

---

## Alternate Data Streams (ADS)

PowerShell can be used to view Alternate Data Streams attached to NTFS files.

```powershell
Get-Item -Path C:\file.txt -Stream *
```

`:$DATA` is the normal/default data stream.

An additional named stream can be an **Alternate Data Stream (ADS)**.

ADS can be relevant during security investigations because hidden data can be stored in these streams.

## Key takeaway

PowerShell can retrieve detailed information about **processes, services, network connections and files**, making it useful for system administration, incident response and threat hunting.

# PowerShell – Scripting

## What is Scripting?

**Scripting** means writing a series of commands in a text file (a script) so they can be executed automatically.

It helps:

* Automate repetitive tasks
* Save time
* Reduce human error
* Perform complex tasks efficiently

---

## PowerShell in Cybersecurity

### Blue Team

PowerShell scripts can be used for:

* Log analysis
* Detecting anomalies
* Extracting Indicators of Compromise (IOCs)
* Malware analysis
* Scanning systems for signs of intrusion

### Red Team

PowerShell can be used for:

* System enumeration
* Executing commands remotely
* Automating penetration testing tasks
* Testing security controls

### System Administration

PowerShell scripting can automate:

* System integrity checks
* Configuration management
* Security policies
* Network monitoring
* Security responses

---

## Invoke-Command

`Invoke-Command` runs commands on **local or remote computers**.

Example:

```powershell id="v5lqkw"
Invoke-Command -ComputerName Server01 -ScriptBlock { Get-Culture }
```

`-ComputerName` specifies the remote computer.

`-ScriptBlock` specifies the command(s) to execute.

It can also run a script file remotely:

```powershell id="ekqj79"
Invoke-Command -FilePath C:\scripts\test.ps1 -ComputerName Server01
```

## Key takeaway

PowerShell scripting allows cybersecurity professionals to **automate tasks**, while `Invoke-Command` can execute commands remotely.
