# Loops

Computers are like robots. They are good at doing things over and over and over and over again.

A LOOP is when we ask a program to do until a certain condition is met.

---

# The While Loop

The simplest loop in JavaScript is `while`.

```js
while (someCondition) {
    someAction()
}
```

In English this reads, "While some condition is true, do some action".

The program will continue to do some action until the condition is false.

---

# while true

If you want something to keep going forever, set the condition to `true`:

```js
while (true) {
  console.log("Hello")
}
```

This means "While true is true, say 'Hello'". Obviously `true` will always be true, so it goes forever.

To stop an operation in your terminal, hold down the CONTROL key and press the C key.

---

# Infinite Loops

Loops that run forever are called infinite loops. They most often happen when you set a condition for your loop that is always true. There are several common ways people create infinite loops

- Hard coding the condition as a truthy value
- Assignment instead of comparison
- Forgetting to update the variable your checking against from inside the loop

---

# Format Your Code!!!!

**Note well!** The lines between `{` and `}` are INDENTED. Indentation is very important to you and other humans. It lets our eyes follow the patterns and helps us quickly see what parts of the program go with each other.

**Always make sure your code is formatted**

---

# Infinite Counting

Let's write a program that counts from 0 to infinity. Put this in a file called `count.js`.

```js
let count = 0;
while (true) {
    console.log(count);
    count = count + 1;
}
```

Run the program with `node count.js`.

> Remember, CONTROL-C means "Stop everything!!!"

---

# Who wants to loop forever?

Next, we will change your `count.js` program so that it only counts to 100.

Please try this yourself first! We will go over a solution in just a minute.

---

# `while`

* The `while` statement keeps checking the expression

  * if it's `true` then it loops back
  * if it's `false` then it stops looping and goes on to the rest of the program

This is fairly complicated, so let's stop here and make sure we understand everything that's happening in this little program.

---

# `while` breakdown (pt.1)

    let count = 1

creates a *variable* named `count` and sets its value to `1`.

    while (count <= 100)

starts a loop and immediately compares `count` to `100`.

`1` is less than `100`, so the expression is `true`, so we continue with the block of code starting with the `{`.

---

# `while` breakdown (pt.2)

      console.log(count);

prints the current value of count.

      count = count + 1

*increments* the `count` variable... it was `1`, so now it's `2`

    }

goes *back to the `while` line* and checks again

---

# `while` breakdown (pt.3)

```js
while (count <= 100)
```

compares `count` to `100`.

`2` is less than `100`, so the expression is `true`, so we continue with the loop.

Eventually, `count` becomes `101`, and the `while` expression is `false`, and so we stop looping and go on.

---

# break dancing

The key word `break` stops a loop immediately.

Here's a more verbose way of counting to 100:

```js
let count = 0;
while (true) {
    console.log(count);
    count = count + 1;
    if (count > 100) {
        break;
    }
}
```

---

# Different Kinds of Loops

While the `while` loop is arguably the most straightforward, and widely used loop in JavaScript it's not the only type of loop.

JavaScript inherited the `for` loop from C; it can be cumbersome and confusing but you should learn to recognize it.

```js
for (let count=0; count < 100; count++) {
  console.log(count);
}
```
---
# For vs While

There are the same amount of *steps* happening in a `for` loop as a `while` loop, they're just written in slightly different ways.

#### For
```js
for (
  // initialize variable
  let count=0;
  // test the variable 
  count < 100; 
  // change the variable
  count++) {
    
    console.log(count);
}
```
#### While
```js
// initialize variable
let count = 0;
// test the variable
while (count < 100>) {
    console.log(count);
    // change the variable
    count = count + 1;
}
```
---

# Flavors of For

There are also a couple variations on the `for` loop that can be used to iterate over different data structures.

These types of loops are known collectively as *iterators*, the most common of which are the `for ...in` loop, and the `for ...of` loop. More on those when we talk about data structures next week!

---

# For Loops with Arrays
A for loop is often seen paired with an indexed data structure known as an *Array*

```js
let poemLines = [
  'Roses are red', 
  'Violets are blue', 
  'Honey is sweet',
  'And so are you'
];

for (let line = 0; line < poemLines.length; line++) {
  console.log(poemLines[line]);
}
```
---
# For Loop Breakdown (pt.1)
We are using the for loop to get each item in the Array collection poemLines

```js
let poemLines = [
  'Roses are red', 
  'Violets are blue', 
  'Honey is sweet',
  'And so are you'
];

```
---
# For Loop Breakdown (pt.2)
The `for (...)` part of a `for` loop is where the loop:

* Initializes a variable to track
* Determines whether to run again
* Changes the variable after the loop runs.
```js
for (let line = 0; line < poemLines.length; line++)
```
---

# For Loop Breakdown (pt.3)
Think about the three parts as three separate lines of code.

* Initialize a variable to track
```js 
let line = 0;
```
* Determine whether to run again
```js 
line < poemLines.length;
```
* Change the variable after the loop runs
```js
line++;
```
---
# For Loop Breakdown (pt.4)
The body of the loop is the code that runs on each time through the loop
```js
for (let line = 0; line < poemLines.length; line++) 
/* everything inside the curly braces is the body */
{
  // this code will run each time we loop
  // since `index` changes each time,
  // a different poem line is printed each cycle
  console.log(poemLines[line]);
}
```