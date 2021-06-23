# Looping With User Input

Loops are good for more than just counting. For example we could create a loop that asks a question over and over until the user enters a specific response.

Let's build a simple application that echos back a users input until the user says "Stop copying me!"

---

# Code-Along: The Setup

Since we are going to be asking users for input we will want to import the `readline` library, and create  the `ask` function

```js
const readline = require('readline');
const readlineInterface = readline.createInterface(process.stdin, process.stdout);

function ask(questionText) {
  return new Promise((resolve, reject) => {
    readlineInterface.question(questionText, resolve);
  });
}
```

---

# Code-Along: Stop Copying Me!

When setting up a loop we will want to set up a variable to check against. Then inside the loop we can use the ask function store the user input, and reassign the variable we're checking against.

Since the ask function returns a promise we will also need to contain our loop inside an `async` function so we can `await` the *actual value* of the ask function.

```js
async function copyCat() {
  let answer = 'Hello! How are you doing?'

  while(answer.toLowerCase() !== "stop copying me!") {
    answer = await ask(answer + " >_")
  }
  process.exit()
}
copyCat()
```

---