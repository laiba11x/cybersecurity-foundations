# Active Directory (AD)

## Windows Domains

A **Windows domain** is a group of users and computers managed by an organisation.

Instead of manually configuring every computer, a domain allows administrators to manage users, computers and security policies **centrally**.

### Active Directory

**Active Directory (AD)** is Microsoft's directory service used to centrally manage resources within a Windows domain.

It provides:

* **Centralised identity management** – administrators can manage user accounts centrally.
* **Security policy management** – policies can be applied to users and computers across the network.
* **Centralised authentication** – users can use their domain credentials on multiple computers.

### Domain Controller (DC)

A **Domain Controller (DC)** is a server that runs Active Directory services.

It handles tasks such as:

* Authenticating users
* Managing user accounts
* Managing computers
* Applying security policies

### Real-World Example

A university may allow students to use the same username and password on different computers across campus.

The computer sends the authentication request to **Active Directory**, where the user's credentials are checked.

Administrators can also use Active Directory policies to restrict what users can do, such as preventing access to certain settings or removing administrative privileges.

## Key Terms

| Term                       | Meaning                                                   |
| -------------------------- | --------------------------------------------------------- |
| **Domain**                 | Group of users and computers managed by an organisation   |
| **Active Directory (AD)**  | Central system for managing users, computers and policies |
| **Domain Controller (DC)** | Server that runs Active Directory services                |
| **Domain credentials**     | Credentials used to authenticate to the domain            |

### Key Takeaway

**Active Directory = centralised management of users, computers and security policies within a Windows domain.**

**Domain Controller = the server that runs Active Directory.**

## Active Directory Domain Services (AD DS)

**Active Directory Domain Services (AD DS)** is the core service of a Windows domain. It acts as a **catalogue** containing information about objects on the network.

Common AD objects include:

* Users
* Groups
* Machines
* Printers
* Shared resources

## Users

Users are **security principals**, meaning they can be authenticated and given permissions to access network resources.

Users can represent:

* **People** – employees who need network access.
* **Services** – accounts used by services such as IIS or MSSQL.

Service accounts should generally have only the permissions required to run their specific service.

## Machine Accounts

When a computer joins an Active Directory domain, a **machine account** is created for it.

Machine accounts:

* Are security principals.
* Have limited rights within the domain.
* Normally have passwords automatically rotated by Windows.
* Use the computer name followed by `$`.

Example:

`DC01$`

## Security Groups

**Security groups** allow administrators to assign permissions to multiple users or computers at once.

Users can belong to **multiple groups** and inherit the permissions assigned to those groups.

### Important Default Groups

| Group                  | Purpose                                     |
| ---------------------- | ------------------------------------------- |
| **Domain Admins**      | Administrative privileges across the domain |
| **Server Operators**   | Can administer Domain Controllers           |
| **Backup Operators**   | Can access files for backup purposes        |
| **Account Operators**  | Can create or modify domain accounts        |
| **Domain Users**       | Contains domain user accounts               |
| **Domain Computers**   | Contains domain computer accounts           |
| **Domain Controllers** | Contains Domain Controllers                 |

## Active Directory Users and Computers (ADUC)

**Active Directory Users and Computers (ADUC)** is a management tool used to manage:

* Users
* Groups
* Computers
* Organisational Units

It can be opened from the Domain Controller.

## Organisational Units (OUs)

An **Organisational Unit (OU)** is a container used to organise users and computers within Active Directory.

OUs are commonly organised around departments, such as:

* IT
* Sales
* Marketing
* Management

OUs are mainly used to **apply policies and configurations** to groups of users or computers.

A user or computer can only belong to **one OU at a time**.

## Default AD Containers

Some containers are created automatically by Windows:

* **Builtin** → default groups available to Windows hosts.
* **Computers** → computers joining the domain are placed here by default.
* **Domain Controllers** → contains Domain Controllers.
* **Users** → default domain users and groups.
* **Managed Service Accounts** → accounts used by services.

## Security Groups vs OUs

The key difference is:

**OU → used to organise objects and apply policies.**

**Security Group → used to grant permissions to resources.**

For example:

* Use an **OU** to apply a security policy to everyone in the IT department.
* Use a **Security Group** to give selected users access to a shared folder.

A user can belong to **multiple security groups**, but can only be in **one OU at a time**.

### Key Takeaway

**AD objects → Users, machines and groups.**

**OUs → Organise objects and apply policies.**

**Security Groups → Grant permissions.**

## OU Management

### Deleting an OU

Active Directory protects OUs against **accidental deletion** by default.

To delete a protected OU:

1. Open **Active Directory Users and Computers**.
2. Select **View → Advanced Features**.
3. Right-click the OU → **Properties**.
4. Open the **Object** tab.
5. Uncheck **Protect object from accidental deletion**.
6. Delete the OU.

Deleting an OU also deletes the **users, groups and OUs contained within it**, so this should be done carefully.

## Delegation

**Delegation** allows specific users to perform certain administrative tasks without giving them full **Domain Administrator** privileges.

A common example is allowing an IT support employee to **reset users' passwords**.

### Example

An administrator can:

1. Right-click an OU.
2. Select **Delegate Control**.
3. Select the user who should receive the delegated permissions.
4. Choose the required task, such as **Reset user passwords and force password change at next logon**.
5. Complete the wizard.

The delegated user can then perform that specific task on users within the OU without being a Domain Administrator.

## PowerShell Password Reset

An authorised delegated user can reset a user's password with:

`Set-ADAccountPassword`

A password reset can also be configured to require the user to change their password at the next login using:

`Set-ADUser -ChangePasswordAtLogon $true`

### Key Takeaway

**Delegation = giving a user specific administrative permissions without giving them full domain administrator access.**

## Computer OUs

When a computer joins an Active Directory domain, it is normally placed in the **Computers** container by default.

However, keeping every computer together makes it harder to apply different policies to different types of devices.

### Common Computer Categories

**Workstations**

* Computers used by normal employees.
* Used for everyday work and browsing.
* Privileged users should not normally log into workstations.

**Servers**

* Provide services to users or other computers.
* Should have different security policies from normal workstations.

**Domain Controllers**

* Manage the Active Directory domain.
* Are highly sensitive because they contain information used to authenticate domain users.
* Domain Controllers are already placed in their own OU by Windows.

### Organising Computers

A common structure is to create:

* **Workstations OU** → personal computers and laptops.
* **Servers OU** → servers.
* **Domain Controllers OU** → Domain Controllers.

The OUs can then have different **security policies** applied to them.

### Key Takeaway

**Separate computers by their purpose → apply appropriate policies to each group.**

## Group Policy Objects (GPO)

**Group Policy Objects (GPOs)** are collections of settings that can be applied to users and computers in an Active Directory domain.

GPOs allow administrators to apply **security policies and configurations centrally** instead of configuring every computer individually.

### Creating and Linking a GPO

1. Create a GPO under **Group Policy Objects**.
2. Configure the required policies.
3. **Link the GPO** to the relevant OU or domain.

A GPO applies to the OU it is linked to and can be **inherited by child OUs**.

### GPO Scope

The **Scope** section shows where the GPO is linked.

**Security Filtering** can restrict which users or computers receive the GPO.

By default, GPOs generally apply to **Authenticated Users**.

### Computer vs User Configuration

GPOs can contain:

* **Computer Configuration** → policies affecting computers.
* **User Configuration** → policies affecting users.

## Password Policy

Password policies can be configured through:

`Computer Configuration → Policies → Windows Settings → Security Settings → Account Policies → Password Policy`

Examples include:

* Minimum password length
* Password complexity
* Account lockout policies

## SYSVOL

**SYSVOL** is a network share on Domain Controllers used to distribute Group Policy files throughout the domain.

The default location is:

`C:\Windows\SYSVOL\sysvol\`

Computers periodically retrieve updated GPO settings from SYSVOL.

### Force a GPO Update

To immediately update Group Policies on a computer:

`gpupdate /force`

## Example GPOs

### Restrict Control Panel Access

A GPO can prevent users from accessing the **Control Panel and PC settings**.

This can be applied to specific user OUs, such as:

* Marketing
* Management
* Sales

The IT OU can be excluded so IT users retain access.

### Auto Lock Screen

A GPO can automatically lock computers after a period of inactivity.

For example, setting the inactivity limit to **5 minutes** helps prevent someone from accessing an unattended computer.

This can be applied at the **domain level**, allowing computer OUs underneath it to inherit the policy.

### Key Takeaway

**GPO = centralised security and configuration policies.**

**OU = where policies can be targeted.**

**SYSVOL = where Group Policy files are distributed from Domain Controllers.**

**`gpupdate /force` = forces a computer to refresh its Group Policies.**

## Windows Domain Authentication

When using a Windows domain, user credentials are managed by the **Domain Controller (DC)**.

Two main authentication protocols are used:

* **Kerberos** → default authentication protocol in modern Windows domains.
* **NetNTLM** → older/legacy protocol kept for compatibility.

## Kerberos

**Kerberos** uses **tickets** as proof that a user has already authenticated.

### Basic Process

1. The user authenticates to the **Key Distribution Center (KDC)**, usually running on the Domain Controller.
2. The KDC provides a **Ticket Granting Ticket (TGT)** and a **Session Key**.
3. When the user wants to access a service, they use the TGT to request a **Ticket Granting Service (TGS)**.
4. The TGS is specific to the requested service.
5. The user sends the TGS to the service to authenticate.

### Important Terms

* **KDC** → creates and manages Kerberos tickets.
* **TGT** → allows a user to request tickets for specific services.
* **TGS** → ticket used to access a specific service.
* **SPN (Service Principal Name)** → identifies the service and server being accessed.
* **Session Key** → used to securely communicate during authentication.

## NetNTLM

**NetNTLM** uses a **challenge-response** authentication process.

### Basic Process

1. Client requests authentication.
2. Server sends a random **challenge**.
3. Client uses its NTLM password hash and the challenge to calculate a response.
4. Client sends the response to the server.
5. Server sends the challenge and response to the Domain Controller.
6. The Domain Controller verifies the response.
7. Authentication is either accepted or denied.

The user's actual password is **not sent across the network**.

### Domain vs Local Accounts

For a **domain account**, the Domain Controller verifies the NetNTLM response.

For a **local account**, the server can verify the response itself using the password hash stored locally in the **SAM (Security Account Manager)**.

## Kerberos vs NetNTLM

| Kerberos                          | NetNTLM                       |
| --------------------------------- | ----------------------------- |
| Modern/default protocol           | Legacy protocol               |
| Uses tickets                      | Uses challenge-response       |
| Uses TGT and TGS                  | Uses a challenge and response |
| Default in modern Windows domains | Kept mainly for compatibility |

### Key Takeaway

**Kerberos → authentication using tickets.**

**NetNTLM → authentication using challenge-response.**

# Active Directory – Trees, Forests & Trust Relationships

## Trees

* A **Tree** is a collection of Active Directory domains that share the same **namespace**.
* Trees are useful when an organisation needs separate domains for different countries, branches or departments.
* Example:

  * Root domain: `thm.local`
  * UK domain: `uk.thm.local`
  * US domain: `us.thm.local`
* Each domain can have its own:

  * Domain Controller
  * Users
  * Computers
  * GPOs
  * Domain Administrators
* **Domain Admins** can manage their own domain but not the other domains.
* **Enterprise Admins** can administer all domains within the enterprise.

## Forests

* A **Forest** is a collection of multiple AD trees that use **different namespaces**.
* Example:

  * Company A: `thm.local`
  * Company B: `mht.local`
* The trees can exist within the same overall Active Directory environment.
* Forests are useful when organisations have separate domain structures, such as after a company acquisition.

## Trust Relationships

* A **Trust Relationship** allows users from one domain to be authorised to access resources in another domain.
* A trust does **not automatically give users access** to everything in the trusted domain.
* Permissions still need to be assigned to specific users or groups.

### One-Way Trust

If **Domain AAA trusts Domain BBB**:

* Users from **BBB** can potentially be authorised to access resources in **AAA**.
* The direction of the trust is opposite to the direction of access.

### Two-Way Trust

* Both domains trust each other.
* Users from either domain can potentially be authorised to access resources in the other.
* Domains joined within a tree or forest have two-way trust relationships by default.

## Key Terms

| Term                  | Meaning                                                           |
| --------------------- | ----------------------------------------------------------------- |
| **Tree**              | Multiple domains sharing the same namespace                       |
| **Forest**            | Multiple trees using different namespaces                         |
| **Trust**             | Allows users between domains to be authorised to access resources |
| **Domain Admins**     | Administrators for a single domain                                |
| **Enterprise Admins** | Administrators across all domains in an enterprise                |

### Simple hierarchy

**Forest → Trees → Domains → Users / Computers / Groups**

The important distinction is: **Tree = same namespace; Forest = different namespaces.**
