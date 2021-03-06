# Input and Output

- Computers have many senses -- keyboard, mouse, network card, camera, joystick, etc. Collectively, these are called **INPUT**.

- Computers can also express themselves in many ways -- text, graphics, sound, networking, printing, etc. Collectively, these are called **OUTPUT**.

- Input and Output together are called **I/O**.

- the only part of your laptop that is _really_ a computer is the CPU and the RAM; all the other parts (keyboard, trackpad, display, disk drive, etc.) are technically I/O devices

---

# Memory vs I/O

- Performing _calculations_ and accessing _memory_ is **very fast**
- ...but reading and writing to I/O devices is **slow**
  - (at least as far as the CPU is concerned)
  - I/O operations can take _seconds_ or _milliseconds_; CPU operations take _nanoseconds_
- Every time you ask JavaScript to do an I/O operation, it _pauses your program_
  - this allows the CPU to spend time doing other things, not just sitting idle waiting for a key to be pressed or a file to be written
- In NodeJS, you have to write a function for JavaScript to run once it _resumes_
  - this function is named an _asynchronous callback_
  - _asynchronous_ is Greek for "out of time" or "not together in time"

---

# Terminal I/O

- In JavaScript,

  - `console.log` means "print a line to the terminal"

- In NodeJS,

  - `process.stdin` means "input coming from the terminal"

  - Reading a line in NodeJS is **weird**; here's one way to do it

```js
function handleInput(input) {
  let inputAsString = input.toString();
  console.log("The input is: ", inputAsString);
}

process.stdin.once("data", handleInput);

console.log("Waiting for input...");
```

---

# Input Output Decoded

Let's break down the code we just wrote

```js
function handleInput(input) {
  let inputAsString = input.toString();
  console.log("The input is: ", inputAsString);
}

process.stdin.once("data", handleInput);

console.log("Waiting for input...");
```

> `once` is a special type of function, called an *event listener*, that takes two parameters,

> it's first parameter is a type of event that will happen, in this case _getting some data_ which is indicated by the event `'data'`

> and its second parameter is **another function**

In other words, the function `handleInput` is *what to do* when the event occurs. That is, when `'data'` is received it triggers `handleinput` to run.

| phrase                        | meaning                       |
| ----------------------------- | ----------------------------- |
| `process.stdin`               | hey terminal input,           |
| `.once('data', ...)`          | when you get some data,       |
| `function handleInput(input)` | please name it input          |
| `{ ... }`                     | send it to this block of code |
| `input.toString()`            | convert it to a string        |
| `console.log(inputAsString)`  | and print it to the terminal  |

---

# Event Listeners

`.once` is a special type of function in JavaScript called an _event listener_

Event Listeners are one of the main ways of handling user input for your programs. They:

- are attached to a specific element, or interface
  - In this case the terminal
- wait for a specific type of interaction or event
  - represented by the first argument to the function
  - In this case a _data entry_ event
- run a function, that is supplied as the second argument to the event listener

---

# Welcome to Callback City!

The previous code is equivalent to this:

```js
process.stdin.once("data", function handleInput(input) {
  let inputAsString = input.toString();
  console.log(inputAsString);
});
```

The `handleInput` function itself is called a _callback_ (since you are asking the I/O device to _call the function_ when it receives input).

---

# Readline

- NodeJS is more than a *JavaScript interpreter*
- It's also a collection of *JavaScript libraries*
- One of the libraries is called `readline`
  - `readline` makes it easier to read lines, naturally :-)
  - the "books" in this library are functions
    - (and classes and other things too)

---

# Using readline
> Warning: this code uses features we have not yet covered! Copy and paste it verbatim during the codealong below, and don't worry if it doesn't make much sense yet.

To use readline, include the following lines in the top of your source file:
```js
const readline = require('readline');
const readlineInterface = readline.createInterface(process.stdin, process.stdout);

function ask(questionText) {
  return new Promise((resolve, reject) => {
    readlineInterface.question(questionText, resolve);
  });
}
```

> This is called "boilerplate code" -- you don't need to fully understand it before using it.
---

# using readline - explanation

| code                                                        | explanation                                                                                                                             |
|-------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| `const readline = require('readline');`                     | load the `readline` package and name it `readline`                                                                                      |
| `const readlineInterface = readline.createInterface({...})` | create an *interface* to readline using the following settings:                                                                         |
| `  process.stdin,`                                | for input, use the *standard input stream* (i.e. terminal keyboard input)                                                               |
| `  process.stdout`                               | for output, use the *standard output stream* (i.e. terminal console output)                                                             |
| `function ask(questionText) {...}`                          | a function named *ask* that uses the [Promise API](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises) to asynchronously ask a question and wait for a reply |

(We will cover the Promise API in much more detail later; for now, all you really need to know is that Promises allow us to use `async` and `await` in the next slide.)

---


# Code-Along: using readline and await some more

Please follow along with the instructor and create a file named `quest.js`, and in that file define the `ask` function, then accept a few different inputs, and use them to construct our output:

```javascript
// boiler plate code
const readline = require('readline');
const readlineInterface = readline.createInterface(process.stdin, process.stdout);

function ask(questionText) {
  return new Promise((resolve, reject) => {
    readlineInterface.question(questionText, resolve);
  });
}

// prompt user for inputs to construct output

async function start() {
  let name = await ask('What is your name? ');
  let quest = await ask('What is your quest? ');
  let color = await ask('What is your favorite color? ');
  console.log('Hello ' + name + '! ' +
    'Good luck with ' + quest + ', ' +
    'and here is a ' + color + ' flower for you.');
  process.exit();
}


start();
```

* run it from the command line using `node quest.js`
---
# Async Await

* We will learn a lot more about callbacks, promises, and `async/await` later
* For now, follow these two rules when using `async` and `await`:
1. await means *"wait for the following thing to happen"*
2. when you use await inside a function, you **must use async** to define that function
> WARNING: `async` functions don't play nicely with for loops! (Fortunately, there are other ways to loop that do work well.)
