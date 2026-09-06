# HTTP & HTTPS

## What I learned

I learned that HTTP and HTTPS are protocols used for communication between a web browser (client) and a web server.

When I visit a website, my browser sends a request to the server, and the server sends a response back.

### HTTP is stateless

HTTP is stateless, which means each request is treated independently. The server does not automatically remember previous requests.

Websites can use things like cookies and session IDs to keep track of a user's session. This is why I can log into a website and continue browsing without having to log in again on every page.

## HTTP Methods

HTTP has different methods for communicating with a server. Some of the main methods are:

* GET
* POST
* PUT
* DELETE
* PATCH
* HEAD
* OPTIONS
* CONNECT
* TRACE

### GET

I learned that **GET** is used to request or retrieve a resource from a web server.

For example, when I enter a website into my browser, the browser can send a GET request to retrieve the webpage.

## HTTP Request and Response

The basic process is:

**Client → Request → Server → Response → Client**

The response contains:

* **Response headers** — information about the response
* **Response body** — the actual content requested

## Useful fields

When inspecting a request in browser developer tools, I can see information such as:

* **Scheme** — HTTP or HTTPS
* **Host** — the website/server being contacted
* **Filename/Path** — the resource being requested
* **Address** — the IP address of the server
* **Status** — tells me whether the request was successful

### Status Code

**200 OK** means the request was successful.

## Practical Learning

I used browser developer tools and the Network tab to inspect GET requests made when loading a webpage. This helped me understand what happens behind the scenes when I visit a website.
