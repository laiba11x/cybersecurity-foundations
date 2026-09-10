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

