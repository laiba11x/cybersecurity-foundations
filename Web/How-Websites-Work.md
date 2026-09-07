## How Websites Work

When I visit a website, my browser sends a **request** to a web server. The server processes it and sends back a **response**, which the browser uses to display the website.

### Front End (Client-Side)

The part of the website that runs in my browser and that I can see and interact with.

### Back End (Server-Side)

The server-side part that processes requests and sends responses back to the browser.

### Key Takeaway

**Browser → Request → Web Server → Response → Browser**

* **Front end** = what the user sees and interacts with.
* **Back end** = processes requests and provides the data.

## HTML Basics

Websites are mainly built using three technologies:

* **HTML** — creates the structure and content of a webpage.
* **CSS** — controls the appearance and styling.
* **JavaScript** — adds interactivity and more complex features.

### HTML

**HTML (HyperText Markup Language)** is used to create the structure of webpages.

HTML uses **elements/tags** to tell the browser how to display content.

Common HTML elements:

* `<html>` — root of the page.
* `<head>` — contains information about the page, such as its title.
* `<body>` — contains the content displayed on the page.
* `<h1>` — large heading.
* `<p>` — paragraph.
* `<button>` — button.
* `<img>` — image.

### HTML Attributes

Tags can have **attributes** that provide additional information.

Examples:

* `class` — groups elements for styling.
* `id` — uniquely identifies an element.
* `src` — specifies the location of an image.

Example:

```html
<p class="bold-text">Hello</p>
<img src="img/cat.jpg">
```

An element can have multiple attributes.

### Class vs ID

* **Class** — can be used by multiple elements.
* **ID** — should uniquely identify one element.

JavaScript can use IDs to identify specific elements.

### Viewing HTML

I can view a website's HTML by right-clicking the page and selecting **View Page Source**.

### Key Takeaway

**HTML = structure, CSS = styling, JavaScript = interactivity.**

## JavaScript Basics

**JavaScript (JS)** makes websites **interactive and dynamic**.

* **HTML** → website structure and content
* **CSS** → appearance and styling
* **JavaScript** → functionality and interactivity

JavaScript can dynamically change a webpage, such as:

* Changing text
* Changing button styles
* Creating animations
* Responding to user actions

### Adding JavaScript

JavaScript can be added directly using `<script>` tags:

```html
<script>
    // JavaScript code
</script>
```

Or loaded from an external JavaScript file:

```html
<script src="/location/of/javascript_file.js"></script>
```

### Changing HTML with JavaScript

JavaScript can find an HTML element using its **ID** and change its content:

```javascript
document.getElementById("demo").innerHTML = "Hack the Planet";
```

This finds the element with `id="demo"` and changes its content.

### Events

HTML elements can trigger JavaScript when an event happens.

For example, `onclick` runs JavaScript when a button is clicked:

```html
<button onclick='document.getElementById("demo").innerHTML = "Button Clicked";'>
    Click Me!
</button>
```

### Key Takeaway

**JavaScript makes webpages interactive and allows their content and behaviour to change dynamically.**

## Sensitive Data Exposure

**Sensitive Data Exposure** happens when a website accidentally makes sensitive information accessible to users.

Sensitive information can sometimes be found in:

* HTML source code
* JavaScript files
* HTML comments
* Hidden links
* Accidentally exposed login credentials

### Why It's a Security Risk

An attacker can inspect the page source and discover information that developers forgot to remove. This could potentially be used to access other parts of the web application.

### Security Testing

When assessing a website, one of the first things to check is the **page source** for:

* Exposed credentials
* Sensitive information
* Hidden links
* Comments containing secrets

### Key Takeaway

Always check a website's **HTML and JavaScript source code** for accidentally exposed sensitive information.

## HTML Injection

**HTML Injection** happens when a website displays **user input without properly sanitising it**.

If user input is added directly to a webpage, an attacker may be able to enter their own HTML code and change the page's appearance or functionality.

### Example

If a website takes a user's name and displays it on the page, an attacker could enter HTML such as:

```html
<h1>Hello</h1>
```

Instead of displaying it as normal text, the browser may interpret it as HTML.

### Input Sanitisation

**Input sanitisation** means filtering or cleaning user input before using it.

For example, a website could remove HTML tags from user input to prevent HTML injection.

### Security Lesson

**Never trust user input.** Developers should sanitise user input before displaying or processing it.

### Key Takeaway

HTML Injection occurs when **unsanitised user input is interpreted as HTML by the browser**.

## How the Web Works — Summary

When I visit a website:

1. **DNS** finds the IP address of the web server.
2. My computer communicates with the server using **HTTP/HTTPS**.
3. The web server sends back resources such as:

   * HTML
   * CSS
   * JavaScript
   * Images
4. My browser uses these resources to build and display the webpage.

Other technologies and components help websites run efficiently and provide additional features.

### Key Takeaway

**DNS → HTTP/HTTPS → Web Server → HTML/CSS/JavaScript/Images → Browser**

## Web Infrastructure Components

### Load Balancers

A **load balancer** distributes incoming traffic across multiple servers.

Benefits:

* Handles high amounts of traffic.
* Improves **availability**.
* Provides **failover** if a server stops working.

Common methods:

* **Round-robin** — sends requests to each server in turn.
* **Weighted** — sends requests based on server workload/capacity.

**Health checks** regularly check whether servers are working. If a server fails, the load balancer stops sending traffic to it.

### CDN

A **CDN (Content Delivery Network)** stores static website files on servers around the world.

Examples of static files:

* JavaScript
* CSS
* Images
* Videos

Users can download files from a nearby CDN server, reducing loading times and traffic to the main server.

### Databases

Web servers use **databases** to store and retrieve information.

Examples:

* MySQL
* MSSQL
* MongoDB
* PostgreSQL

### WAF

A **WAF (Web Application Firewall)** sits between users and the web server and helps protect the application from attacks.

It can:

* Detect common attacks.
* Block suspicious requests.
* Identify potentially malicious bots.
* Use **rate limiting** to restrict excessive requests from an IP address.

### Key Takeaway

* **Load balancer** → distributes traffic between servers.
* **CDN** → delivers static files from nearby servers.
* **Database** → stores and retrieves information.
* **WAF** → filters and blocks potentially malicious web requests.

## How Web Servers Work

### What is a Web Server?

A **web server** is software that listens for incoming connections and uses **HTTP** to deliver web content to clients.

Common web server software:

* Apache
* Nginx
* IIS
* Node.js

A web server stores website files in a **root directory**.

Examples:

* Linux Apache/Nginx: `/var/www/html`
* Windows IIS: `C:\inetpub\wwwroot`

### Virtual Hosts

A web server can host **multiple websites** using **virtual hosts**.

The server checks the **Host header** in the HTTP request and matches it to the correct website.

If there is no match, the server usually provides the **default website**.

Each website can have its own root directory.

### Static vs Dynamic Content

**Static content** does not change between requests.

Examples:

* Images
* CSS
* JavaScript
* Fixed HTML

**Dynamic content** can change depending on the request or user.

Examples:

* Blog pages showing new posts
* Search results
* Personalised content

Dynamic content is processed by the **backend** before being sent to the browser.

### Backend Languages

Backend programming languages process requests and can:

* Communicate with databases
* Process user input
* Call external services
* Generate dynamic content

Examples:

* PHP
* Python
* Ruby
* Node.js
* Perl

The **backend code runs on the server**, so users normally only receive the final HTML/result, not the backend code itself.

### Frontend vs Backend

* **Frontend** → what I see and interact with in my browser.
* **Backend** → processes requests behind the scenes on the server.

### Key Takeaway

**Web server → receives HTTP request → processes it → returns web content to the browser.**
