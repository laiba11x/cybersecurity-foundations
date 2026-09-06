# JavaScript Basics

## What is JavaScript?

JavaScript is a popular programming language used mainly for websites. It originally ran in web browsers, but with **Node.js**, JavaScript can also run outside the browser and on servers.

In this room, I learned the basics of JavaScript by creating a simple **Guess the Number** game.

The three main programming concepts covered were:

* Variables
* Conditionals
* Loops

---

## Running JavaScript

JavaScript files can be run using Node.js from the command line:

```bash
node demo.js
```

JavaScript can also run inside a web browser, where I can use the browser's developer tools and console.

---

## Variables

Variables store values that can change while a program is running.

JavaScript uses `let` to declare a variable:

```javascript
let tries = 0;
let guess = 0;
```

The values can later be changed:

```javascript
tries = tries + 1;
```

### Key point

* `let` → declares a variable that can change.

---

## Constants

Constants store values that should not be reassigned.

JavaScript uses `const`:

```javascript
const secret = Math.floor(Math.random() * 20) + 1;
```

The value of `secret` cannot later be reassigned.

### Key point

* `const` → declares a constant.

---

## Generating a Random Number

The game needs a random number between 1 and 20.

```javascript
const secret = Math.floor(Math.random() * 20) + 1;
```

* `Math.random()` → generates a random decimal from 0 up to, but not including, 1.
* `Math.floor()` → rounds a number down.
* `* 20` → creates a range up to 20.
* `+ 1` → shifts the range to 1–20.

---

## Displaying Output

`console.log()` displays text or other output:

```javascript
console.log("I'm thinking of a number between 1 and 20");
```

### Key point

* `console.log()` → displays output on the screen/console.

---

## Getting User Input

The game asks the user to enter a guess:

```javascript
const text = await rl.question("Take a guess: ");
```

The input is initially stored as **text/string**.

To convert it into a whole number:

```javascript
guess = parseInt(text, 10);
```

`parseInt()` converts the text into an integer.

The `10` means the number is interpreted using **base 10 (decimal)**.

For example:

```text
"15" → 15
```

### Key points

* `rl.question()` → gets user input.
* `parseInt(text, 10)` → converts text into a decimal integer.

---

## Counting Attempts

The game keeps track of how many guesses the user makes:

```javascript
tries = tries + 1;
```

Every time the user makes a guess, `tries` increases by 1.

---

# Conditionals

Conditionals allow the program to make decisions.

JavaScript uses:

* `if`
* `else if`
* `else`

For the guessing game:

```javascript
if (guess < 1 || guess > 20) {
    console.log("That number is out of range. Try again.");
} else if (guess < secret) {
    console.log("Too low, try again.");
} else if (guess > secret) {
    console.log("Too high, try again.");
} else {
    console.log("You got it in", tries, "tries!");
}
```

### `if`

Checks the first condition.

```javascript
if (guess < 1 || guess > 20)
```

If the guess is outside the range 1–20, the program says the number is out of range.

### `else if`

Checks another condition if the previous one was false.

```javascript
else if (guess < secret)
```

If the guess is smaller than the secret number, the program says:

```text
Too low, try again.
```

Another condition checks if the guess is greater:

```javascript
else if (guess > secret)
```

This displays:

```text
Too high, try again.
```

### `else`

If all the previous conditions are false, the guess must equal the secret number.

The program then tells the user they got it correct.

---

## The OR Operator

JavaScript uses `||` to mean **OR**.

Example:

```javascript
guess < 1 || guess > 20
```

This means:

**guess is less than 1 OR greater than 20.**

---

# While Loops

At first, the game only allowed the user to make one guess.

A **while loop** allows the user to keep guessing until they get the correct number.

```javascript
while (guess !== secret) {
    // code to repeat
}
```

`while` means the code keeps repeating while the condition is true.

`!==` means **not equal to**.

Therefore:

```javascript
while (guess !== secret)
```

means:

**Keep repeating while the guess is not equal to the secret number.**

Once the user guesses correctly, the condition becomes false and the loop stops.

---

## What Happens Inside the Loop?

Each time the loop runs:

1. Ask the user for a guess.
2. Convert the input from text into a number.
3. Increase the number of attempts.
4. Check whether the number is within the valid range.
5. Check whether the guess is too low or too high.
6. Tell the user if they guessed correctly.
7. Repeat until the correct number is guessed.

---

## Example

If the secret number is `14`:

```text
Guess: 10
Too low, try again.

Guess: 15
Too high, try again.

Guess: 14
You got it in 3 tries!
```

The loop stops once the guess equals the secret number.

---

# Important JavaScript Syntax

| Syntax          | Meaning                               |   |    |
| --------------- | ------------------------------------- | - | -- |
| `let`           | Declare a variable                    |   |    |
| `const`         | Declare a constant                    |   |    |
| `if`            | Check a condition                     |   |    |
| `else if`       | Check another condition               |   |    |
| `else`          | Run if previous conditions are false  |   |    |
| `while`         | Repeat code while a condition is true |   |    |
| `!==`           | Not equal                             |   |    |
| `               |                                       | ` | OR |
| `console.log()` | Display output                        |   |    |
| `rl.question()` | Get user input                        |   |    |
| `parseInt()`    | Convert text into an integer          |   |    |
| `Math.random()` | Generate a random decimal             |   |    |
| `Math.floor()`  | Round down                            |   |    |

---

## Main Takeaways

The main things I learned from this room were:

* JavaScript can run in browsers and with Node.js.
* `let` is used for variables that can change.
* `const` is used for constants.
* `if`, `else if`, and `else` allow a program to make decisions.
* `while` loops repeat code while a condition is true.
* `!==` means not equal.
* `||` means OR.
* `console.log()` displays output.
* `rl.question()` gets user input.
* `parseInt()` converts text into a number.
* `Math.random()` and `Math.floor()` can be used to generate random numbers.
* Programming takes practice, so understanding the code is more important at this stage than memorising or writing the whole program from scratch.
* JavaScript and Python use similar programming concepts, but their syntax is different.
