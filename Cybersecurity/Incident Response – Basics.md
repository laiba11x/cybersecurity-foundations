# Incident Response – Basics

## What is Incident Response?

**Incident Response (IR)** is the process of handling a **cyber security incident** from beginning to end.

It includes preparing for incidents, responding when they happen, and reducing their impact.

## Why is Incident Response Important?

Organisations can suffer significant damage from cyber security incidents, including:

* Financial losses
* Data loss
* System disruption
* Damage to the organisation

Incident response provides a structured approach to dealing with these incidents.

## Incident Response Covers

Incident response can include:

* **Preparation** – Put security measures, plans and resources in place before an incident occurs.
* **Detection** – Identify when a security incident has happened.
* **Response** – Take action to contain and manage the incident.
* **Impact Reduction** – Minimise the damage caused by the incident.
* **Recovery** – Restore affected systems and return to normal operations.

## Easy Memory

> **Incident Response = prepare, detect, respond, minimise impact and recover.**

The main idea is to have a **planned process for dealing with a cyber security incident from start to finish**.

# Events, Alerts and Incident Severity

## Events and Logs

Processes running on devices such as laptops and mobile phones generate **events** whenever they perform an action.

There are two main types of processes:

* **Interactive processes** – Require user interaction, such as playing a game or watching a video.
* **Non-interactive processes** – Run in the background without requiring direct user interaction.

The large number of processes running on a device means that **huge numbers of events** can be generated.

These events are recorded as **logs** and can be ingested into security solutions for analysis.

## Alerts

When a security solution identifies an event, or group of events, that may indicate harmful activity, it generates an **alert**.

The security team then investigates the alert to determine whether it is actually malicious.

```text
Process
   ↓
Event
   ↓
Log
   ↓
Security solution analyses logs
   ↓
Potentially harmful activity detected
   ↓
Alert generated
   ↓
Security team investigates
```

## False Positives and True Positives

### False Positive

A **false positive** is an alert that appears to indicate harmful activity but is actually **benign**.

**Example:**

A security solution detects a large amount of data being transferred to an external IP address.

After investigation, the security team discovers that the transfer was part of a legitimate cloud backup.

### True Positive

A **true positive** is an alert that correctly identifies **harmful or malicious activity**.

**Example:**

A security solution detects a phishing email.

The security team investigates and confirms that the email is genuinely attempting to compromise a user's system.

## Incidents

A confirmed **true positive** may be classified as a **security incident**.

Once an alert is confirmed as an incident, it needs to be assigned a **severity level**.

## Incident Severity

Severity indicates the potential **impact** of an incident and helps the security team decide which incidents need attention first.

The common severity levels are:

| Severity     | Priority  |
| ------------ | --------- |
| **Critical** | Highest   |
| **High**     | Very high |
| **Medium**   | Moderate  |
| **Low**      | Lowest    |

A **critical** incident receives the highest priority, followed by **high**, **medium**, and **low**.

## Easy Memory

> **Event = something happened**

> **Log = recorded event**

> **Alert = possible harmful activity detected**

> **False positive = alert is not actually harmful**

> **True positive = alert is genuinely harmful**

> **Incident = confirmed harmful activity**

> **Severity = how serious/impactful the incident is**

# Common Types of Security Incidents

Security incidents can be categorised into different types. A single incident can involve **one or multiple types** at the same time.

## Malware Infections

**Malware** is malicious software that can cause harm to a system, network or application.

Malware infections are commonly caused by malicious files, such as:

* Documents
* Executable files
* Other files

There are different types of malware, each with different capabilities and effects.

## Security Breaches

A **security breach** occurs when an unauthorised person gains access to **confidential information**.

Confidential information should only be accessible to authorised people.

## Data Leaks

A **data leak** occurs when confidential information is exposed to **unauthorised entities**.

Data leaks can happen:

* Intentionally, through an attack
* Unintentionally, because of human error or misconfiguration

### Difference from a Security Breach

> **Security breach** = unauthorised access to confidential data

> **Data leak** = confidential data is exposed to unauthorised entities

## Insider Attacks

An **insider attack** is an attack carried out by someone **inside an organisation**.

For example, an unhappy employee could intentionally introduce malware into the network using a USB device.

Insiders can be particularly dangerous because they may already have legitimate access to organisational resources.

## Denial of Service (DoS) Attacks

A **Denial of Service (DoS)** attack attempts to make a system, network or application unavailable to legitimate users.

The attacker can send a large number of requests, consuming the system's available resources.

```text id="r2j4u1"
Large number of requests
          ↓
Resources become exhausted
          ↓
System becomes unavailable
          ↓
Legitimate users are affected
```

## Incident Severity

Different types of incidents cannot automatically be considered more or less severe than one another.

The impact depends on the **organisation and its circumstances**.

For example, a data leak may have limited impact on one organisation but be extremely damaging to another. Similarly, a DoS attack could have a major impact on an organisation that relies heavily on its website.

## Easy Memory

> **Malware infection** = malicious software

> **Security breach** = unauthorised access

> **Data leak** = confidential data exposed

> **Insider attack** = attack from within the organisation

> **DoS** = makes services unavailable

> **Severity depends on the impact on the organisation**

# Incident Response Frameworks

Different security incidents require different responses, so organisations use **Incident Response Frameworks** to provide a structured approach to handling incidents.

Two widely used frameworks are:

* **SANS Incident Response Framework**
* **NIST Incident Response Framework**

---

# SANS Incident Response Framework

The SANS framework has **6 phases**.

A useful way to remember them is **PICERL**:

> **Preparation → Identification → Containment → Eradication → Recovery → Lessons Learned**

| Phase               | Purpose                                                 |
| ------------------- | ------------------------------------------------------- |
| **Preparation**     | Prepare people, processes and technology for incidents  |
| **Identification**  | Detect and identify suspicious activity                 |
| **Containment**     | Limit the impact and stop the incident spreading        |
| **Eradication**     | Remove the threat from the environment                  |
| **Recovery**        | Restore affected systems and return to normal operation |
| **Lessons Learned** | Review the incident and improve future responses        |

### 1. Preparation

Prepare the organisation to deal with incidents.

Examples include:

* Creating an incident response team
* Developing an incident response plan
* Deploying security solutions
* Training employees

### 2. Identification

Look for abnormal behaviour that could indicate an incident.

Security tools and investigation techniques can be used to identify suspicious activity.

### 3. Containment

Limit the impact of an identified incident.

Examples include:

* Isolating a compromised machine
* Disabling compromised accounts
* Preventing the attacker from moving to other systems

### 4. Eradication

Remove the threat from the affected environment.

For example:

* Removing malware
* Cleaning compromised systems

### 5. Recovery

Restore affected systems and return them to normal operation.

This may involve:

* Restoring backups
* Rebuilding systems
* Testing recovered systems

### 6. Lessons Learned

Review the incident after it has been handled.

The organisation identifies:

* What happened
* What went wrong
* Gaps in detection or response
* Improvements needed for future incidents

---

# NIST Incident Response Framework

The **NIST Incident Response Framework** has **4 phases**.

The framework is similar to the SANS approach but combines some of the activities into fewer phases.

The four phases are:

1. **Preparation**
2. **Detection and Analysis**
3. **Containment, Eradication and Recovery**
4. **Post-Incident Activity**

## SANS vs NIST

| SANS            | NIST                                  |
| --------------- | ------------------------------------- |
| Preparation     | Preparation                           |
| Identification  | Detection and Analysis                |
| Containment     | Containment, Eradication and Recovery |
| Eradication     | Containment, Eradication and Recovery |
| Recovery        | Containment, Eradication and Recovery |
| Lessons Learned | Post-Incident Activity                |

---

# Incident Response Plan

An **Incident Response Plan (IRP)** is a formal document that defines how an organisation will respond to security incidents.

It describes procedures to follow **before, during and after an incident**.

The plan is formally approved by senior management.

## Key Components

An Incident Response Plan can include:

* **Roles and responsibilities**
* **Incident response methodology**
* **Communication plan** with stakeholders and law enforcement
* **Escalation path**

## Easy Memory

### SANS — PICERL

> **P**reparation
> **I**dentification
> **C**ontainment
> **E**radication
> **R**ecovery
> **L**essons Learned

### NIST

> **Preparation → Detection & Analysis → Containment, Eradication & Recovery → Post-Incident Activity**

> **Incident Response Plan = the formal document describing how an organisation handles incidents.**
