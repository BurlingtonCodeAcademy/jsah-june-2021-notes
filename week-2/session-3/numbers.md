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