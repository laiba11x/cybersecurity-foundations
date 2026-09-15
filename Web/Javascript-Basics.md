# JavaScript Basics

## Variables

Variables are containers used to **store data values** so they can be used later.

JavaScript has three ways to declare variables:

* `var` → function-scoped
* `let` → block-scoped
* `const` → block-scoped and cannot be reassigned

Example:

```javascript
let username = "Laiba";
const age = 20;
```

## Data Types

Data types describe the type of value stored in a variable.

Common JavaScript data types include:

* **String** → text
* **Number** → numbers
* **Boolean** → `true` or `false`
* **Null** → intentionally empty value
* **Undefined** → value has not been assigned
* **Object** → more complex data, such as objects and arrays

Example:

```javascript
let name = "Laiba";       // String
let age = 20;             // Number
let loggedIn = true;      // Boolean
let result = null;        // Null
```

## Functions

A **function** is a block of code designed to perform a specific task.

Functions can accept **parameters** and be called whenever the task needs to be performed.

Example:

```javascript
function PrintResult(rollNum) {
    alert("Username with roll number " + rollNum + " has passed the exam");
}

PrintResult(101);
```

Instead of writing the same code repeatedly, the function can be reused with different values.

## Loops

Loops allow a block of code to run **multiple times while a condition is true**.

Common JavaScript loops:

* `for`
* `while`
* `do...while`

Example:

```javascript
for (let i = 0; i < 3; i++) {
    console.log(i);
}
```

This runs the code three times.

Loops are useful when working with lists or when the same task needs to be repeated.

## Request-Response Cycle

The **request-response cycle** is the process where:

1. The browser (client) sends a request to a web server.
2. The server processes the request.
3. The server sends a response back to the browser.

The response could contain a webpage, data, or another resource.

### Quick Summary

* **Variables** store data.
* `var`, `let`, and `const` declare variables.
* **Data types** describe the type of stored value.
* **Functions** perform reusable tasks.
* **Loops** repeat code.
* **Request-response cycle** = client sends request → server sends response.

## First JavaScript Program

JavaScript (JS) is an **interpreted language**, meaning it can be executed directly by the browser without being compiled beforehand.

A simple JavaScript program can include variables, data types, conditions and functions.

```javascript
// Hello World
console.log("Hello, World!");

// Variable
let age = 25;

// Condition
if (age >= 18) {
    console.log("You are an adult.");
} else {
    console.log("You are a minor.");
}

// Function
function greet(name) {
    console.log("Hello, " + name + "!");
}

// Call the function
greet("Bob");
```

### Running JavaScript in Chrome

JavaScript can be run directly using the **Chrome Developer Console**.

1. Open Google Chrome.
2. Press **Ctrl + Shift + I** or right-click the page and select **Inspect**.
3. Select the **Console** tab.
4. Enter JavaScript code into the console.
5. Press **Enter** to execute it.

### Simple Calculation

Example:

```javascript
let x = 5;
let y = 10;
let result = x + y;

console.log("The result is: " + result);
```

Output:

```text
The result is: 15
```

Here:

* `x` and `y` are variables storing numbers.
* `x + y` is an expression that adds the numbers.
* `console.log()` prints the result to the console.

### Key Takeaways

* JavaScript can run directly in a web browser.
* The **Chrome Console** allows JavaScript to be executed and tested.
* `console.log()` displays information in the console.
* JavaScript can use variables, conditions, functions and expressions.

## JavaScript in HTML

JavaScript can be integrated into HTML in two main ways:

1. **Internal JavaScript**
2. **External JavaScript**

JavaScript usually works alongside HTML and CSS to make web pages **dynamic and interactive**.

### Internal JavaScript

Internal JavaScript is written directly inside the HTML document using `<script>` tags.

Example:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Internal JS</title>
</head>
<body>
    <p id="result"></p>

    <script>
        let x = 5;
        let y = 10;
        let result = x + y;

        document.getElementById("result").innerHTML =
            "The result is: " + result;
    </script>
</body>
</html>
```

The JavaScript:

* Creates variables `x` and `y`.
* Adds them together.
* Finds the HTML element with `id="result"`.
* Changes its content using `innerHTML`.

The `<script>` tag can be placed in the `<head>` or `<body>` depending on when the script needs to run.

### External JavaScript

External JavaScript is stored in a separate `.js` file.

Example `script.js`:

```javascript
let x = 5;
let y = 10;
let result = x + y;

document.getElementById("result").innerHTML =
    "The result is: " + result;
```

The JavaScript file is connected to the HTML using the `src` attribute:

```html
<script src="script.js"></script>
```

### Internal vs External JavaScript

| Internal JS                        | External JS                            |
| ---------------------------------- | -------------------------------------- |
| JavaScript is inside the HTML file | JavaScript is in a separate `.js` file |
| Uses `<script>` tags               | Uses `<script src="...">`              |
| Simple for small pages             | Better for larger projects             |
| HTML and JS are together           | Keeps HTML and JS organised separately |

### Identifying JavaScript During Web Testing

When inspecting a web application, you can use **View Page Source** to check how JavaScript is loaded.

```html
<script>
    // Internal JavaScript
</script>
```

No `src` attribute means the JavaScript is **internal**.

```html
<script src="script.js"></script>
```

A `src` attribute means the JavaScript is **external**.

### Key Takeaways

* `<script>` tags are used to include JavaScript in HTML.
* **Internal JS** is written directly in the HTML.
* **External JS** is stored in a separate `.js` file.
* The `src` attribute loads an external JavaScript file.
* Page source can be inspected to identify internal and external JavaScript.

## JavaScript Dialogues & User Interaction

JavaScript can interact with users through built-in dialogue box functions:

### `alert()`

Displays a message with an **OK** button.

```javascript
alert("Hello THM");
```

Used for messages, warnings, or notifications.

### `prompt()`

Asks the user to enter information. It returns the value entered, or `null` if the user selects Cancel.

```javascript
name = prompt("What is your name?");
alert("Hello " + name);
```

### `confirm()`

Asks the user to confirm an action. It returns:

* `true` → user clicks OK
* `false` → user clicks Cancel

```javascript
confirm("Do you want to proceed?");
```

## Security

JavaScript dialogue functions can also be abused by attackers.

For example, malicious JavaScript could repeatedly display alert boxes:

```javascript
for (let i = 0; i < 3; i++) {
    alert("Hacked");
}
```

Changing the loop to a much larger number could repeatedly interrupt the user's browser.

**Security takeaway:** Only run JavaScript or HTML files from trusted sources, as malicious JavaScript can cause unwanted behaviour and may be used in attacks such as XSS.

## JavaScript Control Flow

Control flow determines the **order in which JavaScript code is executed** based on conditions or repetition.

Common control flow structures include:

* `if-else` → makes decisions based on conditions
* `switch` → chooses between multiple cases
* `for` → repeats code a set number of times
* `while` → repeats code while a condition is true
* `do...while` → runs code at least once, then repeats while a condition is true

### If-Else Statements

`if-else` allows different code to run depending on whether a condition is true or false.

```javascript
age = prompt("What is your age");

if (age >= 18) {
    document.getElementById("message").innerHTML = "You are an adult.";
} else {
    document.getElementById("message").innerHTML = "You are a minor.";
}
```

If the age is **18 or above**, the first block runs. Otherwise, the `else` block runs.

## Client-Side Login Checks

JavaScript can be used to implement login checks in a webpage.

For example, a page might check whether the username is `admin` and whether the password matches a specific value.

If authentication is performed **only in client-side JavaScript**, the code can potentially be inspected or modified by the user.

**Security takeaway:** Sensitive authentication and authorisation decisions should be enforced on the **server**, not trusted solely to client-side JavaScript.

## JavaScript Minification & Obfuscation

### Minification

**Minification** reduces the size of JavaScript code by removing unnecessary characters such as:

* Spaces
* Line breaks
* Comments
* Sometimes shortening variable names

The code still works the same way, but it becomes harder for humans to read.

**Main purpose:** reduce file size and improve loading performance.

### Obfuscation

**Obfuscation** changes JavaScript to make it difficult for humans to understand.

It can:

* Rename variables and functions to meaningless names
* Add confusing or unnecessary code
* Make the code look like random or "gibberish" characters

The browser can still execute the code normally.

**Main purpose:** make the code harder to understand or analyse.

### Example

Readable JavaScript:

```javascript
function hi() {
    alert("Welcome to THM");
}
hi();
```

After obfuscation, the same functionality may look much more complicated, with names such as:

```text
_0x114713
_0x2246f2
_0x51a830
```

Even though the code looks completely different, it can still display the same alert.

### Viewing JavaScript

JavaScript loaded by a webpage can be viewed through browser developer tools:

**Chrome → Inspect → Sources → select the `.js` file**

This is useful when analysing a web application during security testing.

### Deobfuscation

Obfuscated JavaScript can be processed with a **JavaScript deobfuscator** to make it easier to understand.

**Security takeaway:** Minification and obfuscation make JavaScript harder to read, but they do **not** make client-side code secret or secure. Code sent to the browser can generally be inspected by the user.

## JavaScript Security Best Practices

### Don't Rely Only on Client-Side Validation

JavaScript can validate form input on the client side, but users can **disable or manipulate JavaScript**.

Important validation should also happen on the **server side**.

**Rule:** Never rely on client-side validation alone.

### Don't Use Untrusted Libraries

JavaScript can load external scripts using the `src` attribute:

```html
<script src="example.js"></script>
```

Only use libraries from **trusted and verified sources**. Attackers can create malicious libraries with names that look similar to legitimate ones.

### Don't Hardcode Secrets

Never store sensitive information directly in JavaScript, such as:

* API keys
* Access tokens
* Passwords
* Credentials

Example of bad practice:

```javascript
const privateAPIKey = 'pk_TryHackMe-1337';
```

Client-side JavaScript can be inspected by users, so anything stored in it should be considered exposed.

### Minify and Obfuscate JavaScript

**Minification** reduces the size of JavaScript and can improve loading performance.

**Obfuscation** makes the code harder for humans to understand.

Both can make reverse engineering more difficult, although obfuscation **does not make secrets secure**.

**Security takeaway:**

* Validate on the server as well as the client.
* Use trusted JavaScript libraries.
* Never hardcode secrets in client-side JavaScript.
* Minify and obfuscate production JavaScript where appropriate.

