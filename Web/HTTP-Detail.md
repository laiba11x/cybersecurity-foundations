## HTTP & HTTPS

### HTTP

**HTTP (HyperText Transfer Protocol)** is a set of rules used for communication between a web browser and a web server.

It is used to transfer website content such as:

* HTML
* Images
* Videos

### HTTPS

**HTTPS (HyperText Transfer Protocol Secure)** is the secure version of HTTP.

HTTPS:

* **Encrypts data** sent between you and the web server.
* Helps prevent others from reading the data.
* Helps verify that you are communicating with the correct web server.

### Key Takeaway

**HTTP = web communication.**

**HTTPS = secure and encrypted web communication.**

## URLs

**URL (Uniform Resource Locator)** tells your browser **how and where to access a resource** on the Internet.

Example:

`http://user:password@tryhackme.com:80/view-room?id=1#task3`

### Parts of a URL

| Part             | Purpose                                                     |
| ---------------- | ----------------------------------------------------------- |
| **Scheme**       | Protocol used, such as HTTP, HTTPS or FTP                   |
| **User**         | Username/password if authentication is required             |
| **Host**         | Domain name or IP address of the server                     |
| **Port**         | Port used to connect, usually 80 for HTTP and 443 for HTTPS |
| **Path**         | Location of the requested resource                          |
| **Query String** | Extra information sent to the server, e.g. `?id=1`          |
| **Fragment**     | Points to a specific part of a webpage, e.g. `#task3`       |

### HTTP Request

A browser sends a **request** to a web server.

Basic example:

`GET / HTTP/1.1`

Requests can also contain **headers**, which provide extra information to the server.

Common headers include:

* **Host** – website being requested
* **User-Agent** – browser/client being used
* **Referer** – webpage that sent the user to the current page

### HTTP Response

The server sends a **response** back to the browser.

Example:

`HTTP/1.1 200 OK`

Important response information includes:

* **Status Code** – tells us whether the request was successful.
* **Server** – web server software.
* **Content-Type** – type of content being returned, such as HTML or an image.
* **Content-Length** – size of the response data.

`200 OK` means the request was successful.

### Key Takeaway

**URL → tells the browser where/how to access a resource.**

**Request → browser asks the server for something.**

**Response → server sends the requested information back.**

## HTTP Methods

HTTP methods tell the web server **what action the client wants to perform**.

| Method     | Purpose                                              |
| ---------- | ---------------------------------------------------- |
| **GET**    | Retrieve information from a server                   |
| **POST**   | Send data to a server, often to create something new |
| **PUT**    | Update existing information                          |
| **DELETE** | Delete information or records                        |

### Key Takeaway

**GET → Get data**
**POST → Create/send data**
**PUT → Update data**
**DELETE → Delete data**

## HTTP Status Codes

HTTP status codes tell the client **what happened to their request**.

### Status Code Ranges

| Range       | Meaning       |
| ----------- | ------------- |
| **100–199** | Informational |
| **200–299** | Success       |
| **300–399** | Redirection   |
| **400–499** | Client errors |
| **500–599** | Server errors |

### Common Status Codes

| Code    | Meaning                                  |
| ------- | ---------------------------------------- |
| **200** | OK – request successful                  |
| **201** | Created – new resource created           |
| **301** | Moved Permanently                        |
| **302** | Found – temporary redirect               |
| **400** | Bad Request                              |
| **401** | Not Authorised – authentication required |
| **403** | Forbidden – no permission                |
| **404** | Page Not Found                           |
| **405** | Method Not Allowed                       |
| **500** | Internal Server Error                    |
| **503** | Service Unavailable                      |

### Easy Way to Remember

* **2xx = Success**
* **3xx = Redirect**
* **4xx = Your request has a problem**
* **5xx = Server has a problem**

### Key Takeaway

HTTP status codes tell the browser **whether a request succeeded, was redirected, or encountered an error**.

## HTTP Headers

HTTP headers are extra information sent between the browser (client) and web server.

### Request Headers

Sent **from the client → server**:

* **Host** — tells the server which website you want.
* **User-Agent** — tells the server your browser and version.
* **Content-Length** — tells the server how much data is being sent.
* **Accept-Encoding** — tells the server which compression methods the browser supports.
* **Cookie** — sends stored information back to the server, such as login/session data.

### Response Headers

Sent **from the server → client**:

* **Set-Cookie** — tells the browser to store a cookie.
* **Cache-Control** — tells the browser how long to cache the response.
* **Content-Type** — tells the browser what type of data is being returned, such as HTML, CSS, JavaScript, images or PDF.
* **Content-Encoding** — tells the browser how the response data has been compressed.

### Key Takeaway

**Request headers** give the server information about the request, while **response headers** give the browser information about the server's response.
## HTTP Cookies

Cookies are small pieces of data stored by the browser.

* A server sends a **Set-Cookie** header to tell the browser to store a cookie.
* The browser sends the cookie back to the server with future requests.
* HTTP is **stateless**, meaning the server doesn't automatically remember previous requests.
* Cookies allow websites to remember things such as:

  * Login/authentication
  * User preferences
  * Whether you've visited before

### Authentication Cookies

Cookies are commonly used for website authentication.

Instead of storing a password in the cookie, websites usually use a **token** — a unique secret value that identifies the user/session.

### Viewing Cookies

Cookies can be viewed using browser **Developer Tools**:

1. Open Developer Tools.
2. Go to the **Network** tab.
3. Select a request.
4. Look at the **Cookies** section.

### Key Takeaway

Cookies allow websites to remember information about a user between HTTP requests.
