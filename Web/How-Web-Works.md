## DNS (Domain Name System)

**DNS** translates human-readable **domain names** into **IP addresses**.

For example:

`tryhackme.com` → `104.26.10.229`

This means we can use easy-to-remember domain names instead of remembering IP addresses.

### Key Takeaway

**DNS = translates domain names into IP addresses.**

## Domain Hierarchy

A domain name is organised into different levels.

### TLD (Top-Level Domain)

The **TLD** is the rightmost part of a domain name.

Example:

`tryhackme.com`

* `.com` = TLD
* `.com` is a **gTLD (Generic TLD)**.
* **ccTLDs** represent countries, such as `.uk` or `.ca`.

### Second-Level Domain

The **Second-Level Domain (SLD)** is directly before the TLD.

Example:

`tryhackme.com`

* `tryhackme` = Second-Level Domain
* `.com` = TLD

### Subdomain

A **subdomain** is placed before the Second-Level Domain.

Example:

`admin.tryhackme.com`

* `admin` = Subdomain
* `tryhackme` = Second-Level Domain
* `.com` = TLD

Multiple subdomains can be used, for example:

`jupiter.servers.tryhackme.com`

### Key Takeaway

**Domain structure:**

`subdomain.second-level-domain.tld`

Example:

`admin.tryhackme.com`

## DNS Record Types

DNS has different **record types** that provide different types of information.

| Record    | Purpose                                                                                 |
| --------- | --------------------------------------------------------------------------------------- |
| **A**     | Resolves a domain to an **IPv4 address**                                                |
| **AAAA**  | Resolves a domain to an **IPv6 address**                                                |
| **CNAME** | Resolves a domain to **another domain name**                                            |
| **MX**    | Identifies the **mail servers** for a domain                                            |
| **TXT**   | Stores **text-based information**, often used for email security or domain verification |

### Key Takeaway

* **A → IPv4**
* **AAAA → IPv6**
* **CNAME → another domain**
* **MX → email servers**
* **TXT → text information / verification**

## What Happens When You Make a DNS Request?

When you enter a domain name, DNS finds the IP address for that domain.

The process is generally:

1. **Your computer checks its local DNS cache.**
2. If there is no result, it asks a **Recursive DNS Server**.
3. If the Recursive DNS Server doesn't have the answer cached, it asks the **Root DNS Server**.
4. The Root Server directs it to the correct **TLD server** (such as `.com`).
5. The TLD server directs it to the domain's **Authoritative DNS Server** (nameserver).
6. The Authoritative Server provides the correct DNS record/IP address.
7. The result is sent back to the Recursive DNS Server and then to your computer.
8. The result is **cached** for future requests.

### DNS Caching

DNS records have a **TTL (Time To Live)** value.

TTL tells devices how long they can keep a DNS response in their cache before requesting it again.

Caching makes DNS faster and reduces unnecessary DNS requests.

### Key Takeaway

**Computer → Recursive DNS → Root → TLD → Authoritative DNS → IP address**

DNS caching can avoid this process when the answer is already stored locally.

# Web Application Components

A web application has different components working together. These can be divided into **Front End** and **Back End**.

## Front End

The Front End is the part of a web application that the user can see and interact with through a web browser.

### HTML

**HTML (HyperText Markup Language)** defines the structure and content of a web page.

It tells the browser what elements to display, such as:

* Headings
* Paragraphs
* Images
* Links
* Forms

### CSS

**CSS (Cascading Style Sheets)** controls how a web page looks.

It can define:

* Colours
* Fonts
* Sizes
* Layouts
* Spacing

### JavaScript

**JavaScript (JS)** adds functionality and interaction to web pages.

It can allow a web page to:

* Respond to user actions
* Make decisions
* Change content dynamically
* Perform actions without reloading the whole page

### Simple comparison

```text
HTML        → Structure
CSS         → Appearance
JavaScript  → Behaviour / Interaction
```

---

## Back End

The Back End contains the components that users normally cannot see directly but that are needed for the web application to work.

### Database

A **database** stores, modifies and retrieves information.

A web application might use a database to store:

* User accounts
* Preferences
* Posts
* Products
* Other application data

### Infrastructure

Web applications rely on infrastructure such as:

* Web servers
* Application servers
* Storage
* Networking devices
* Other software and systems

These components support the web application and allow it to operate.

### Web Application Firewall (WAF)

A **WAF (Web Application Firewall)** is an optional security component.

It filters web requests and can block potentially dangerous requests before they reach the web server.

A WAF can help protect web applications from attacks.

---

## Front End vs Back End

| Front End                         | Back End                          |
| --------------------------------- | --------------------------------- |
| Visible to the user               | Mostly hidden from the user       |
| Runs in the browser               | Runs on servers/systems           |
| HTML                              | Web server                        |
| CSS                               | Application server                |
| JavaScript                        | Database                          |
| User interface and interaction    | Data and application processing   |
| WAF/infrastructure can support it | WAF/infrastructure can support it |

## Key Takeaways

* **Front End** = what the user sees and interacts with.
* **HTML** = structure.
* **CSS** = appearance.
* **JavaScript** = behaviour and interaction.
* **Back End** = components working behind the scenes.
* **Database** = stores and retrieves application data.
* **Infrastructure** = servers, storage, networking and supporting software.
* **WAF** = filters potentially dangerous web requests.

## Uniform Resource Locator (URL)

A **URL (Uniform Resource Locator)** is the web address used to access a resource on the Internet, such as a webpage, image, video or other content.

### Anatomy of a URL

A URL can contain several parts:

```text
scheme://user@host:port/path?query#fragment
```

### 1. Scheme

The **scheme** specifies the protocol used to access the resource.

Common examples:

* `http` → HyperText Transfer Protocol
* `https` → HTTP Secure

HTTPS encrypts communication between the browser and website.

### 2. User

The **user** can contain login information, usually a username.

Example:

```text
https://user@example.com
```

Including credentials in URLs is uncommon because it can expose sensitive information.

### 3. Host / Domain

The **host/domain** identifies the website or server being accessed.

Example:

```text
example.com
```

From a security perspective, check domains carefully for **typosquatting**, where attackers create domains that look very similar to legitimate websites.

### 4. Port

The **port** identifies the service on the server that should receive the connection.

Ports range from **1 to 65,535**.

Common web ports:

* `80` → HTTP
* `443` → HTTPS

### 5. Path

The **path** identifies the specific resource being requested.

Example:

```text
/login
```

Paths may point to different pages, files or application resources.

Sensitive paths should be protected so unauthorised users cannot access them.

### 6. Query String

The **query string** starts with `?` and is commonly used to send parameters to a web application.

Example:

```text
/search?q=cybersecurity
```

Here:

* `q` → parameter
* `cybersecurity` → value

Query parameters can be modified by users, so applications must validate and handle them securely.

### 7. Fragment

The **fragment** starts with `#` and usually identifies a specific section of a webpage.

Example:

```text
/page#contact
```

The browser can use the fragment to jump to the `contact` section.

### URL Example

```text
https://example.com:443/search?q=cybersecurity#results
```

| Part     | Example            | Purpose        |
| -------- | ------------------ | -------------- |
| Scheme   | `https`            | Protocol       |
| Host     | `example.com`      | Website/server |
| Port     | `443`              | Service        |
| Path     | `/search`          | Resource       |
| Query    | `?q=cybersecurity` | Parameter      |
| Fragment | `#results`         | Page section   |

### Security Notes

* Check URLs carefully for **typosquatting**.
* HTTPS encrypts the connection.
* User-controlled query parameters should be handled securely.
* Sensitive resources should have proper access controls.

## HTTP Messages

HTTP messages are the data exchanged between a **client** (such as a web browser) and a **web server**.

There are two types:

* **HTTP Request** → sent by the client to the server.
* **HTTP Response** → sent by the server back to the client.

### HTTP Request

A request tells the server what the client wants to do.

For example, a browser might send a request to log in to a website.

### HTTP Response

A response is the server's reply to the client's request.

It contains information about whether the request was successful and may contain the requested webpage or other data.

---

## Structure of an HTTP Message

HTTP requests and responses contain four main parts:

```text
Start Line
Headers

Body
```

### 1. Start Line

The **start line** gives important information about the message.

For a request, it includes:

* HTTP method
* Requested path/URL
* HTTP version

Example:

```text
GET /index.html HTTP/1.1
```

For a response, it includes:

* HTTP version
* Status code
* Status message

Example:

```text
HTTP/1.1 200 OK
```

### 2. Headers

**Headers** are key-value pairs containing additional information about the request or response.

Examples include:

* Content type
* Cookies
* Host
* User-Agent
* Authentication information

Example:

```text
Content-Type: text/html
```

### 3. Empty Line

An **empty line** separates the headers from the body.

It tells the client or server that the headers have finished.

### 4. Body

The **body** contains the actual data being sent.

For example:

* A request body can contain login or form data.
* A response body can contain HTML, JSON or other requested content.

Not every HTTP message has a body.

---

## Simple Structure

```text
HTTP Request
     ↓
Client ─────────→ Web Server
     ↑
HTTP Response
```

### Key Takeaways

* **Request** = client → server
* **Response** = server → client
* **Start line** = describes the request/response
* **Headers** = additional information
* **Empty line** = separates headers from body
* **Body** = actual data being sent
* Understanding HTTP messages is important for **web development, troubleshooting and web security**.

## HTTP Requests

An **HTTP request** is sent by a client, such as a web browser, to a web server to request a resource or perform an action.

### Request Line

The first line of an HTTP request is the **request line**.

It contains:

```text id="m2s0rt"
METHOD /path HTTP/version
```

For example:

```text id="f9g2sl"
GET /login HTTP/1.1
```

The request line contains:

* **Method** → what action the client wants to perform
* **Path** → the resource being requested
* **HTTP version** → version of HTTP being used

---

## HTTP Methods

### GET

Requests data from the server.

```text id="0oj6by"
GET /users HTTP/1.1
```

Security consideration: sensitive information such as passwords or tokens should not be placed in GET requests because URLs can be logged or exposed.

### POST

Sends data to the server, commonly to create or update something.

```text id="83j04q"
POST /login HTTP/1.1
```

User input should be properly validated to prevent attacks such as **SQL injection** and **XSS**.

### PUT

Replaces or updates a resource.

The server should check that the user is **authorised** to make the change.

### DELETE

Deletes a resource.

The server should verify that the user has permission to delete it.

### PATCH

Updates part of an existing resource rather than replacing the entire resource.

### HEAD

Similar to GET but returns the **headers without the response body**.

Useful for checking information about a resource without downloading the full content.

### OPTIONS

Shows which HTTP methods are available for a resource.

### TRACE

Used mainly for debugging and can show how a request is processed.

It is commonly disabled when not required because of security concerns.

### CONNECT

Used to establish a tunnel through an HTTP proxy, commonly for HTTPS connections.

---

## URL Path

The **URL path** tells the server which resource the client wants.

Example:

```text id="3c8qwu"
https://example.com/api/users/123
```

The path is:

```text id="xk44za"
/api/users/123
```

Web applications should properly validate and protect paths to prevent issues such as:

* Unauthorised access
* Path manipulation
* Injection attacks

---

## HTTP Versions

| Version  | Main Features                             |
| -------- | ----------------------------------------- |
| HTTP/0.9 | Basic GET requests                        |
| HTTP/1.0 | Headers and improved content support      |
| HTTP/1.1 | Persistent connections and better caching |
| HTTP/2   | Multiplexing and header compression       |
| HTTP/3   | Uses QUIC for faster connections          |

### Key Takeaways

* HTTP requests are sent **client → server**.
* The **request line** contains the method, path and HTTP version.
* **GET** retrieves data.
* **POST** sends data.
* **PUT** updates/replaces a resource.
* **DELETE** removes a resource.
* **PATCH** partially updates a resource.
* **HEAD** returns headers without the body.
* **OPTIONS** shows available methods.
* **TRACE** is mainly used for debugging.
* **CONNECT** establishes a tunnel through a proxy.
* User input and paths should be validated and protected.
