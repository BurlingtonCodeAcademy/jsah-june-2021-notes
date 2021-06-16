# Let's Write Some Code!

Open up your terminal and follow along. Let's play with some data!

![data from Star Trek](https://res.cloudinary.com/btvca/image/upload/v1622815089/curriculum/data_msnapo.jpg)

---

# Values

- A *value* is a location in computer memory that stores *data*.
- There are many kinds of values, including String, Number, Array, Date, ...
- Different flavors of data are referred to as different *Types*

---

# Primitive Data Types

- Numbers
- Strings
- Booleans
- Null
- BigInt
- Symbol

> [Data Types ~MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures)

---

# A Programmer's Best Friend

- You will often run into problems you're not sure how to solve
- Don't be afraid to Google things, we all do it!
- Try to explain the problem with regular words
  - put the question you ask directly into google
  - pay attention to the dates articles were published
  - look for notoriously good sites:
    - MDN
    - Stack Overflow
    - Medium
    - Dev.to
    - ...and many more

> You can't always get what you want, but if you try sometimes you just might find you get what you need ~The Rolling Stones

---

# Numbers

A **number** is what it sounds like -- any integer or decimal.

```js
10
-12
3.14
```

- Many programming languages make a distinction between integers, and decimals.
    - A number that is not an integer is also called a *floating point number* or *float*
- JavaScript doesn't
- This can lead to some ...odd behaviors

---

# NaN

- In JavaScript, `NaN` stands for *Not a Number*
- `NaN` is one of JavaScript's null values

---

# The Math Class

- In JavaScript there is a class called `Math` (More on classes and Objects later)
- It helps with mathematical operations
- Often used to round numbers, or set them to a certain number of decimal places
- Can be used to generate random numbers

---

# Off by One Errors

- As people we want to start counting from 1
- But computers want to start counting at 0
- One of the most prevalent types of errors in programming is the "off by one" error
- The fix is easy, just add or subtract 1!

---

# Strings

A **string** is an object that's a collection of characters, like a word or a sentence.
* a *string literal* is a string whose characters are spelled out explicitly in your code
* JavaScript string literals are surrounded with either single quotes (`'`) or double quotes (`"`), but not both!

```js
"apple"
"banana"
"Cherry Pie"
"My dog has fleas."
'Vermonters have a hundred words for "snow".'
```
---

# Slicing and Dicing

Every string is made of lots of other strings.

You can pull out parts of a string with the `slice` method.

```js
// this means "slice from character 0 to character 4"
"blueberry".slice(0, 4) 

// this means "slice from character 4 to the end
"blueberry".slice(4)
```

These start and end numbers are called *indexes* (or *indices* if you're feeling fancy).

[MDN: slice](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/slice)

---

# String Indexing

Humans like to start counting at 1, but computers like to start counting at 0.

Think of the indexes as pointing at the *spaces between* characters, as in this diagram:

    | B | L | U | E | B | E | R | R | Y |
    0   1   2   3   4   5   6   7   8   9
     
So with this picture in your mind, `slice`...
  
   * includes the character to the *right* of the start index
   * includes the character to the *left* of the end index...
   * ...but *excludes* the character to the *right* of the end index

Try various start and end values in the console and see what happens!

---

# Booleans

A **boolean** is a value that is either true or false, and is represented in JavaScript with the keywords `true`, and `false`.

- Many operations return booleans and are used to run code conditionally (more on that later)

- Pretty much any data in JavaScript can be evaluated as a boolean

- often we use implicit truthy, or falsy values instead of the actual keywords `true` and `false`

(It's named after *[George Boole](https://en.wikipedia.org/wiki/George_Boole)*, 
a 19th-century mathematician who invented [Boolean algebra](https://en.wikipedia.org/wiki/Boolean_algebra).)

---

# Booleans and Conditionals

Let's look ahead a little bit and use a simple conditional to evaluate various values. A conditional starts with the keyword `if` then takes a check in parentheses `if('some condition')` and finally a block of code defined by curly braces which only runs if the check evaluates to `true`

Don't worry too much about how conditionals work right now, we'll go into a lot more depth in them later on. For now just use the conditional given on the next slide to complete the lab, swapping out the check for different values to answer the questions

---

# Code Along: Is it True?

Given this conditional answer the following questions. If the check (currently the boolean `true`) is true it will print `It is truthy` to the console, otherwise nothing will print.

Give me your best guesses to the questions on the next slide!

```js
if(true) {
    console.log('It is truthy')
}
```

---

# Is it True?

* Is the boolean `true` truthy?
    * how about `false`?
* What if we replace the boolean `true` with a string?
    * Is it truthy?
* What if we replace the boolean `true` with a number?
    * Is it true?
    * What about the number `0`?
* What if we replace the boolean `true` with the expression `1 < 2`?
    * What happens if you switch the operator like so `1 > 2`?