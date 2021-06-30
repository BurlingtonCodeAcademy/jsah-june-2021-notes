# Scope

- A **SCOPE** is all the variables and functions that are visible from a given location in your code

- The sever forms of scope are _Global, Local, and Private_

- **Globally scoped** variables can be seen from anywhere in the program

- Locally scoped\*\* variables can be seen only *nearby* where they are defined -- usually inside the same *function* or *code block*

- **Private** variables can only be seen by a specific part of your code, JavaScript does not have *native* support for private variables. There are changes in the works.

```js
// sum is globally defined and can be read anywhere in the program
let sum;

function add(x, y) {
  // x and y are local variables that can only be seen *inside* the function add
  return x + y;
}

sum = add(1, 2);

console.log(sum);
```

> Scope is a one-way mirror -- inner scopes can see out, but outer scopes cannot see in.

![Mr. Bean Scope](https://bootcamp.burlingtoncodeacademy.com/images/one-way-mirror.gif)

---

# Global Scope

If you declare a variable without a keyword (`var`, `let`, `const`) then it is a *global variable* and can be seen and used by *any line of code in your entire program*

> Global variables can **sometimes** be useful, but are also **dangerous**.

A mistake in *any* part of your program accessing a global variable could introduce a bug in *any other* part of your program referencing that same variable.

---
# Block Scope

`let` and `const` are *block-scoped*: any block of code surrounded by { curly braces } can have its own set of local `let` variables

```js
let name = 'Global';
{
  let name = 'Mr. Bean';
    {
      let name = 'Detective';
      console.log(name); // Detective
    }
    console.log(name); // Mr. Bean
}
console.log(name); // Global
```
If a variable name can't be found in the *current scope*, then JavaScript looks in the *next outer scope*, and so on.

---
# Guess the Variable

Which fruit would be logged below?
```js
let fruit = 'Apple';
{
    let fruit = 'Blueberry';
    {
        let fruit = 'Cantaloupe';
    }
    console.log(fruit); // What is this fruit?
}
```
> Blueberry would be console.logged

---
# Functions default to Global
> Unless a function definition is nested within another function, or a code block, it will be global.

```js
let name = 'Alice';   // global

// alpha can see variable 'name'
// alpha can see function named 'beta'
let alpha = function() {
  console.log(name);  
  beta();
}

// 'alpha' must be called after defined
alpha();

// the 'beta' definition is hoisted
function beta() {
  // this 'name' is local to 'beta'
  let name = 'Bob';   
  console.log(name);
}

console.log(name);
```
---
# Parameters are local to their function
```js
let opinion = 'i love cheese';
console.log(rant(opinion));

function rant(message) {
  let loudMessage = message.toUpperCase() + '!!';
  return loudMessage;
}
```
`rant` function has *two* locally scoped variables:

* the local variable `loudMessage`
* the parameter `message`
---
# Scope Error

> When you try to use a variable that is out of scope, you will get an error
```js
function gamma() {
  let x = 'declared inside gamma';
  console.log('Inside gamma: x is ' + x);
}

console.log(x);  // ReferenceError: x is not defined
```
---
# Closure Scope

JavaScript also supports *lexical* scope (aka "closure scope" or "nested scope") which means that variables defined above the current function may also be visible...
```js
function sing() {             // outer function
  let numberOfBottles = 99

  function bottlesOfBeer() {  // inner function
    let message = '' + numberOfBottles
      + ' bottles of beer on the wall';
    return message;
  }

  while (numberOfBottles > 0) {
    console.log(bottlesOfBeer())
    numberOfBottles -= 1
  }

}
```
`bottlesOfBeer` is **enclosed** within sing, so it inherits sing's scope

`numberOfBottles` is visible inside **both** `sing()` **and** `bottlesOfBeer()`
---
# Nested Scopes
Every time you call a function, JS creates a *new scope*

that scope *points* to the current scope

and so on recursively

(and -- strangely enough -- variables that are defined inside a nested function are *still alive* after that function returns (?!?!?!) -- more on this at the very end of this lesson)

---
# Why Nested Scopes?
* Nested 'callbacks' can access local variables just like their neighboring code can
```js
function countLetters(words) {
  let letterCount = 0;

  words.forEach(function(word) {
    letterCount += word.length;
  });

  return letterCount;
}
```
`total` is visible inside the *inner* (callback) function as well as the outer (`countLetters`), so `forEach` can behave like other loops.

---

# Why Nested Scopes? (cont)
This will not work:
```js
function addLetterCount(word) {
  letterCount += word.length;
}

function countLetters(words) {
  let letterCount = 0;
  words.forEach(addLetterCount);
  return letterCount;
}
```
...because `addLetterCount` is not nested inside `countLetters`