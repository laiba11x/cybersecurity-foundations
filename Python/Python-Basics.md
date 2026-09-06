
Python Basics

Python is a high-level, general-purpose programming language. It can be used for automation, web applications, data science, machine learning and cybersecurity.

Variables

Variables are used to store information in a program.

secret = 10
tries = 0
guess = 0

The variable name is on the left and the value is stored on the right.

Comments

Comments explain what code does and are ignored by Python.

# This is a comment
Importing Libraries

Python has libraries that provide additional functionality.

import random

This imports the random library.

To generate a random number:

random.randint(1, 20)

This generates a random integer between 1 and 20.

Output

The print() function displays information on the screen.

print("Hello")
User Input

The input() function allows the user to enter information.

guess = input("Take a guess: ")

input() returns the user's input as text (a string).

If I need the input as a whole number, I can use int():

guess = int(input("Take a guess: "))

int() converts a value into an integer.

Conditional Statements

Conditional statements allow a program to make decisions.

if condition:
    # code
elif another_condition:
    # code
else:
    # code
if checks the first condition.
elif checks another condition if the previous condition was false.
else runs if none of the conditions were true.
Comparison Operators
Operator	Meaning
<	Less than
>	Greater than
==	Equal to
!=	Not equal to

or means either condition can be true.

Example:

if guess < 1 or guess > 20:
    print("Out of range")
elif guess < secret:
    print("Too low")
elif guess > secret:
    print("Too high")
else:
    print("You got it")
Loops

Loops allow code to be repeated.

A while loop continues running while its condition is true:

while condition:
    # code to repeat

For example:

while guess != secret:
    guess = int(input("Take a guess: "))

This keeps asking for a guess while the guess does not equal the secret number.

If:

secret = 10
guess = 5

then:

guess != secret

is true, so the loop continues.

If the user eventually guesses 10, the condition becomes false and the loop stops.

Indentation

Python uses indentation to show which code belongs to an if, elif, else or loop.

if guess < secret:
    print("Too low")

The indented print() belongs to the if statement.

Updating Variables

Variables can be updated while a program is running.

tries = tries + 1

This increases tries by 1.

It is useful for counting how many attempts a user has made.

Guess the Number Example

The room combines these concepts to create a simple guessing game:

Python randomly chooses a number between 1 and 20.
The user enters a guess.
The input is converted from text to an integer.
The program compares the guess with the secret number.
if / elif / else gives the user a hint.
A while loop allows the user to keep guessing.
The number of attempts is tracked using tries.

Example:

import random

secret = random.randint(1, 20)
tries = 0
guess = 0

print("I'm thinking of a number between 1 and 20")

while guess != secret:
    guess = int(input("Take a guess: "))
    tries = tries + 1

    if guess < 1 or guess > 20:
        print("That number is out of range. Try again.")
    elif guess < secret:
        print("Too low, try again.")
    elif guess > secret:
        print("Too high, try again.")
    else:
        print("You got it in", tries, "tries!")

## Key Takeaways

- Python is a general-purpose programming language.
- **Variables** store data.
- `print()` displays output.
- `input()` receives user input.
- `int()` converts text into an integer.
- `import` allows libraries to be used.
- `if / elif / else` makes decisions.
- Comparison operators compare values.
- `while` repeats code while a condition is true.
- `!=` means "not equal to".
- **Indentation is important in Python.**
- Loops and conditional statements can be combined to create useful programs.
