# Linux Shell Basics

## GUI vs CLI

* **GUI (Graphical User Interface):** Uses windows, buttons and menus to interact with the operating system.
* **CLI (Command-Line Interface):** Uses commands typed into a terminal to interact with the operating system.
* CLI can be more **efficient** and **resource-friendly** than using a GUI.
* CLI gives users more **power and control** over the operating system.

## What is a Shell?

* A **shell** is a program that lets you interact with the operating system through commands.
* It provides features that make working with the CLI easier.
* Linux has several different shells available.

## Shell Scripts

* A **shell script** is a file containing a series of commands that can be executed together.
* Shell scripts can automate tasks instead of entering commands manually.

## Learning Goals

* Interact with a Linux shell.
* Use basic Linux shell commands.
* Explore different Linux shells.
* Write basic shell scripts.

# Linux Shell Commands

* **Bash (Bourne Again Shell)** is the default shell for most Linux distributions.

### Basic Commands

| Command | Purpose                                      |
| ------- | -------------------------------------------- |
| `pwd`   | Shows the current working directory          |
| `cd`    | Changes directory                            |
| `ls`    | Lists the contents of a directory            |
| `cat`   | Displays the contents of a file              |
| `grep`  | Searches for a word or pattern inside a file |

### Examples

```bash
pwd
cd Desktop
ls
cat filename.txt
grep THM dictionary.txt
```

* `pwd` stands for **Print Working Directory**.
* `cd` stands for **Change Directory**.
* `grep` is useful for finding specific keywords or patterns in large files.

# Linux Shell Types

You can check your current shell with:

```bash
echo $SHELL
```

Available shells are listed in:

```bash
cat /etc/shells
```

### Bash

**Bash (Bourne Again Shell)** is the default shell for most Linux distributions.

Features:

* Widely used and supports scripting.
* Tab completion.
* Command history using the arrow keys or `history`.
* Compatible with many existing scripts and documentation.

### Fish

**Fish (Friendly Interactive Shell)** focuses on being user-friendly.

Features:

* Simple syntax.
* Automatic spelling correction.
* Customisable prompts and themes.
* Built-in syntax highlighting.
* Tab completion and command history.

### Zsh

**Zsh (Z Shell)** is a modern, highly customisable shell.

Features:

* Advanced tab completion.
* Automatic spelling correction.
* Supports scripting.
* Extensive customisation.
* Command history.
* Can use plugins for additional features such as syntax highlighting.

### Changing Shells

To switch temporarily:

```bash
zsh
```

To permanently change the default shell:

```bash
chsh -s /usr/bin/zsh
```

### Quick Comparison

| Shell | Main Strength                       |
| ----- | ----------------------------------- |
| Bash  | Compatibility and scripting         |
| Fish  | User-friendliness                   |
| Zsh   | Customisation and advanced features |

# Bash Scripting

A **shell script** is a file containing multiple commands that can be executed together. Shell scripts are useful for **automating repetitive tasks**.

## Creating a Bash Script

Bash scripts normally use the `.sh` extension.

```bash
nano first_script.sh
```

Every Bash script starts with a **shebang**:

```bash
#!/bin/bash
```

The shebang tells the system which interpreter to use.

## Variables and User Input

* Variables store values that can be reused in a script.
* `read` takes input from the user.
* `echo` displays output.
* `$name` retrieves the value stored in the `name` variable.

Example:

```bash
#!/bin/bash
echo Hey, whats your name?
read name
echo Welcome, $name
```

## Running a Script

Give the script execution permission:

```bash
chmod +x first_script.sh
```

Run the script from the current directory:

```bash
./first_script.sh
```

`./` tells the shell to execute the file from the **current directory**.

## Loops

Loops repeat commands.

Example:

```bash
for i in {1..10};
do
    echo $i
done
```

This displays numbers from 1 to 10.

* `for` starts the loop.
* `do` starts the commands that repeat.
* `done` ends the loop.

## Conditional Statements

Conditional statements execute code depending on whether a condition is true or false.

```bash
if [ "$name" = "Stewart" ]; then
    echo Welcome Stewart!
else
    echo Not authorized
fi
```

* `if` checks a condition.
* `then` starts the code to run if the condition is true.
* `else` runs when the condition is false.
* `fi` ends the condition.

## Comments

Comments explain code and do not affect how the script runs.

Use `#` to create a comment:

```bash
# This is a comment
```

### Key Commands

| Command            | Purpose                   |
| ------------------ | ------------------------- |
| `nano file.sh`     | Create/edit a script      |
| `chmod +x file.sh` | Give execution permission |
| `./file.sh`        | Execute the script        |
| `read`             | Get user input            |
| `echo`             | Display output            |

## Combining Variables, Loops and Conditions

Shell scripting can combine **variables, loops and conditional statements** to automate tasks such as authentication.

Example uses:

* Variables store the username, company name and PIN.
* A `for` loop asks for each piece of information.
* An `if` statement checks whether all entered details are correct.
* `&&` means **all conditions must be true**.
* If the details are correct, access is granted; otherwise, access is denied.

Example:

```bash
#!/bin/bash

username=""
companyname=""
pin=""

for i in {1..3}; do
    if [ "$i" -eq 1 ]; then
        echo "Enter your Username:"
        read username
    elif [ "$i" -eq 2 ]; then
        echo "Enter your Company name:"
        read companyname
    else
        echo "Enter your PIN:"
        read pin
    fi
done

if [ "$username" = "John" ] && [ "$companyname" = "Tryhackme" ] && [ "$pin" = "7385" ]; then
    echo "Authentication Successful."
else
    echo "Authentication Denied!!"
fi
```

### Key Points

* `for` → repeats a section of code.
* `if / elif / else` → makes decisions.
* `read` → gets user input.
* `&&` → requires multiple conditions to be true.
* `[ "$variable" = "value" ]` → compares a variable with a value.
