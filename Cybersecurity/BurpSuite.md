# Burp Suite

## What is Burp Suite?

* **Burp Suite** is a Java-based framework used for **web application penetration testing**.
* It is widely used for testing:

  * Web applications
  * Mobile applications
  * APIs
* Its main purpose is to **capture, view and modify HTTP/HTTPS traffic** between a browser and a web server.
* This allows security testers to inspect and manipulate requests and responses during manual testing.

### Basic flow

**Browser → Burp Suite → Web Server**

Burp can:

* Intercept requests before they reach the server.
* View request and response data.
* Modify requests before sending them.
* Modify responses before they reach the browser.
* Send captured requests to different Burp tools for further testing.

## Burp Suite Editions

| Edition          | Main purpose                                                 |
| ---------------- | ------------------------------------------------------------ |
| **Community**    | Free version for learning and manual testing                 |
| **Professional** | Advanced manual testing and automated vulnerability scanning |
| **Enterprise**   | Continuous automated web application scanning                |

### Burp Suite Professional

Includes additional features such as:

* Automated vulnerability scanner
* Unrestricted fuzzer/brute-forcer
* Project saving and report generation
* Built-in API
* More extension support
* Burp Collaborator

### Burp Suite Enterprise

* Designed mainly for **continuous automated scanning**.
* Runs on a server and periodically scans web applications for vulnerabilities.
* Unlike Community/Professional, it is focused on automated scanning rather than interactive testing from a local machine.

## Key point

The **Community Edition** provides the core Burp Suite features needed to learn manual web application security testing.

# Burp Suite

## What is Burp Suite?

* **Burp Suite** is a Java-based framework used for **web application penetration testing**.
* It is widely used for testing web applications, mobile applications and APIs.
* Its main purpose is to **capture, view and modify HTTP/HTTPS traffic** between a browser and web server.

### Basic flow

**Browser → Burp Suite → Web Server**

Burp can:

* Intercept requests before they reach the server.
* View request and response data.
* Modify requests and responses.
* Send captured requests to different Burp tools for further testing.

## Burp Suite Editions

| Edition          | Main purpose                                                 |
| ---------------- | ------------------------------------------------------------ |
| **Community**    | Free version for learning and manual testing                 |
| **Professional** | Advanced manual testing and automated vulnerability scanning |
| **Enterprise**   | Continuous automated web application scanning                |

### Burp Suite Professional

Includes:

* Automated vulnerability scanner
* Unrestricted fuzzer/brute-forcer
* Project saving and report generation
* Built-in API
* More extension support
* Burp Collaborator

### Burp Suite Enterprise

* Designed mainly for **continuous automated scanning**.
* Runs on a server and periodically scans web applications for vulnerabilities.

## Main Burp Suite Tools

### Proxy

* One of Burp Suite's main features.
* Intercepts HTTP/HTTPS requests and responses.
* Allows requests and responses to be viewed and modified.

### Repeater

* Captures, modifies and **resends requests repeatedly**.
* Useful for testing endpoints and trying different payloads.
* Commonly used when testing vulnerabilities such as **SQL injection (SQLi)**.

### Intruder

* Sends repeated requests to an endpoint.
* Useful for **fuzzing** and testing authentication or input handling.
* Community Edition has **rate limitations**.

### Decoder

* Used to **encode and decode data**.
* Useful when examining captured data or preparing payloads.

### Comparer

* Compares two pieces of data at **word or byte level**.
* Useful for identifying differences between requests or responses.

### Sequencer

* Tests the randomness of generated values such as **session tokens and cookies**.
* Weak randomness can make tokens predictable and potentially exploitable.

## Burp Extensions

Burp Suite supports extensions that add extra functionality.

* **Extender** allows extensions to be loaded into Burp Suite.
* The **BApp Store** provides third-party extensions.
* Extensions can be developed using languages such as **Java, Python and Ruby**.
* Some extensions require Burp Suite Professional, but many work with Community Edition.
* **Logger++** is an example of an extension that provides enhanced logging.

### Key point

The main Burp tools to remember are:

**Proxy → Repeater → Intruder → Decoder → Comparer → Sequencer**

These tools support different stages of manual web application security testing.

# Burp Suite

## Navigation

Burp Suite is mainly navigated using **two menu bars**:

### Main Menu Bar

* The **top menu bar** contains the main Burp modules.
* Click a module to switch between it.
* Examples include:

  * Dashboard
  * Target
  * Proxy
  * Intruder
  * Repeater

### Sub-Tabs

* A **second menu bar** appears below the main menu bar.
* It contains tabs specific to the selected module.
* For example, selecting **Proxy** provides sub-tabs such as **Intercept**.

### Detaching Tabs

* Tabs can be opened in separate windows.
* Go to **Window → Detach**.
* Detached tabs can be reattached using the same menu.

## Keyboard Shortcuts

| Shortcut           | Tab       |
| ------------------ | --------- |
| `Ctrl + Shift + D` | Dashboard |
| `Ctrl + Shift + T` | Target    |
| `Ctrl + Shift + P` | Proxy     |
| `Ctrl + Shift + I` | Intruder  |
| `Ctrl + Shift + R` | Repeater  |

### Key point

**Top bar = modules → Second bar = module sub-tabs**

Keyboard shortcuts can be used to quickly switch between commonly used Burp tabs.

## Burp Suite Settings

Burp Suite has two main types of settings:

### Global / User Settings

* Apply to the **entire Burp Suite installation**.
* Act as the baseline configuration.
* Apply whenever Burp Suite is started.

### Project Settings

* Apply only to the **current project/session**.
* In **Burp Suite Community Edition**, projects cannot be saved.
* Project-specific settings are therefore lost when Burp is closed.

## Opening Settings

* Click **Settings** in the top navigation bar.
* This opens a separate settings window.

The settings window contains:

### Search

* Search for specific settings using keywords.
* Useful when you know what setting you want but don't know where it is located.

### Type Filter

Allows you to filter between:

* **User settings** – affect the whole Burp installation.
* **Project settings** – apply only to the current project/session.

### Categories

* Organises settings into different categories.
* Allows you to navigate to settings for specific parts of Burp Suite.

### Tool-Specific Settings

Some Burp modules provide shortcuts to their relevant settings.

For example:

* **Proxy → Proxy settings** opens the settings window directly to the Proxy configuration.

### Key point

**User settings = persistent global configuration**

**Project settings = current project/session configuration**

The **Settings search** is useful for quickly finding a specific configuration option.

## Burp Proxy

The **Burp Proxy** is one of the main Burp Suite tools. It allows testers to **capture, inspect and modify HTTP/HTTPS traffic** between a browser and a web server.

### Intercepting Requests

When interception is enabled:

1. A request is made by the browser.
2. Burp Proxy intercepts and holds the request.
3. The tester can:

   * **Forward** it to the server.
   * **Drop** it.
   * **Edit** it.
   * Send it to another Burp tool.
4. The request only reaches the server when it is forwarded.

* **`Intercept is on`** = requests are paused for inspection.
* Turning interception off allows requests to pass through normally.

### Capture and Logging

* Burp logs HTTP requests passing through the Proxy by default.
* Requests can still be logged even when interception is turned off.
* This allows previous traffic to be reviewed later.

### HTTP History

* **HTTP history** stores captured HTTP requests and responses.
* Useful for reviewing previous traffic.
* Requests can be sent to other Burp tools for further testing.

### WebSockets History

* Burp can also capture and log **WebSocket communication**.
* The **WebSockets history** tab allows previous WebSocket traffic to be reviewed.

## Proxy Settings

Proxy-specific configuration can be accessed using **Proxy settings**.

### Response Interception

* Server responses are **not normally intercepted by default**.
* Response interception can be enabled using rules.
* This allows specific server responses to be captured and modified before reaching the browser.

### Match and Replace

* Uses **regular expressions (regex)** to modify HTTP requests and responses.
* Can be used for dynamic changes such as:

  * Modifying the **User-Agent**
  * Changing **cookies**
  * Replacing other parts of HTTP traffic

### Key point

**Proxy = intercept → inspect → modify → forward/drop**

**HTTP history = previous HTTP traffic**

**WebSockets history = previous WebSocket traffic**

Burp Target

The Target tab helps you understand and manage the web application being tested.

It has three main sub-tabs:

1. Site Map
Displays the target web application in a tree structure.
Pages visited while Burp Proxy is active are automatically added.
Useful for mapping a web application during enumeration.
API endpoints accessed by the application can also appear in the site map.
Professional Edition can perform automated crawling.
Community Edition can still build a site map while you browse manually.
2. Issue Definitions
Contains information about vulnerabilities that Burp's scanner can detect.
Community Edition can access the vulnerability definitions even though it does not have the full automated scanner.
Includes:
Vulnerability descriptions
References
Information useful when documenting findings
3. Scope Settings
Defines which targets are in scope for testing.
Can include or exclude specific:
Domains
IP addresses
Helps prevent unnecessary traffic from being captured and keeps testing focused on the intended target.
Key point

Site Map → map the application

Issue Definitions → research vulnerabilities

Scope → control what is being tested

## Burp Browser

Burp Suite includes a built-in **Chromium browser** that is already configured to use the Burp Proxy.

### Opening Burp Browser

* Go to the **Proxy** tab.
* Click **Open Browser**.
* A Chromium window will open.
* Traffic from this browser automatically passes through Burp Proxy.

This avoids manually configuring a normal browser to use the proxy.

### Burp Browser Settings

Burp Browser has additional settings under:
**Settings → Tools → Burp's browser**

These settings can be customised depending on your testing setup.

### Burp Browser on Linux / AttackBox

When Burp Suite is running as the **root user**, such as on the TryHackMe AttackBox, the browser may fail to start because Chromium cannot create its normal sandbox.

There are two options:

**Recommended:**

* Create a normal, low-privilege user.
* Run Burp Suite under that account.

**Alternative:**

* Go to **Settings → Tools → Burp's browser**.
* Enable **Allow Burp's browser to run without a sandbox**.

⚠️ Running without the browser sandbox reduces security because a compromised browser could potentially access the machine. It is generally safer to use a non-root account.

### Key point

**Burp Browser = built-in Chromium + automatically configured Burp Proxy**

## Burp Proxy Scoping

**Scoping** controls which traffic Burp Suite focuses on during testing.

Without a scope, Burp can capture and log a large amount of traffic, making it difficult to focus on the web application being tested.

### Adding a Target to Scope

1. Go to **Target**.
2. Find the target in the list on the left.
3. Right-click the target.
4. Select **Add To Scope**.
5. Burp will ask whether to stop logging traffic that is outside the scope.
6. Usually select **Yes** when you only want to analyse the target.

### Viewing the Scope

Go to:

**Target → Scope settings**

Here you can:

* **Include** specific domains/IPs.
* **Exclude** specific domains/IPs.
* Control exactly which targets are considered in scope.

### Logging vs Intercepting

Stopping logging of out-of-scope traffic **does not stop Burp from intercepting it**.

To prevent Burp from intercepting out-of-scope requests:

1. Go to **Proxy → Proxy settings**.
2. Find **Intercept Client Requests**.
3. Select **And URL Is in target scope**.

This means Burp will only intercept requests that match the defined target scope.

### Key point

**Scope = what you want to test**

**Logging scope = what Burp records**

**Intercept scope = what Burp pauses for inspection**

For a cleaner setup:

**Target → Add To Scope → Stop logging out-of-scope traffic → Proxy settings → Intercept only in-scope URLs**

## Burp Proxy and TLS Certificates

When Burp intercepts **HTTPS/TLS traffic**, the browser may show a certificate error because it does not automatically trust Burp Suite's **PortSwigger Certificate Authority (CA)**.

### Why does this happen?

* Burp acts as a proxy between the browser and HTTPS website.
* Burp generates certificates for intercepted HTTPS connections.
* The browser needs to trust the **PortSwigger CA certificate** before it will accept these certificates.

### Installing the PortSwigger CA Certificate

With Burp Proxy active:

1. Open the browser through Burp.
2. Visit:
   `http://burp/cert`
3. Download the **`cacert.der`** certificate.
4. In Firefox, open:
   `about:preferences`
5. Search for **certificates**.
6. Click **View Certificates**.
7. In Certificate Manager, click **Import**.
8. Select the downloaded `cacert.der` file.
9. Enable:
   **Trust this CA to identify websites**
10. Click **OK**.

After this, the browser should trust Burp's CA and HTTPS websites can be accessed through the Burp Proxy without the certificate warning.

### Key point

**HTTPS → Burp intercepts traffic → Browser sees Burp's certificate → Browser must trust PortSwigger CA**
## Practical Example – Reflected XSS

A common use of Burp Proxy is testing web applications for vulnerabilities such as **Cross-Site Scripting (XSS)**.

### Reflected XSS

* **XSS** involves injecting client-side code, usually JavaScript, into a web page so that it executes.
* **Reflected XSS** occurs when the injected input is reflected by the web application and affects the person making the request.

### TryHackMe Example

Target support form:

`http://10.128.166.42/ticket/`

The **Contact Email** field has a client-side filter that prevents special characters from being entered directly.

Example XSS payload:

```html
<script>alert("Succ3ssful XSS")</script>
```

The browser-side filter prevents this from being entered normally.

### Bypassing the Client-Side Filter

Client-side validation can sometimes be bypassed because the request can be intercepted and modified before it reaches the server.

1. Make sure **Burp Proxy** is active.
2. Turn **Intercept** on.
3. Enter valid information into the support form, for example:

   * Email: `pentester@example.thm`
   * Query: `Test Attack`
4. Submit the form.
5. Burp intercepts the request.
6. Modify the email field in the intercepted request to:

```html
<script>alert("Succ3ssful XSS")</script>
```

7. Select the payload.
8. Press **Ctrl + U** to URL-encode it.
9. Click **Forward**.

If the application is vulnerable, the browser displays an alert showing:

**`Succ3ssful XSS`**

### Key point

Client-side validation happens in the browser, so it should **not be relied upon as the only security control**. Intercepting the request with Burp allows a tester to see whether the server properly validates the modified input.
