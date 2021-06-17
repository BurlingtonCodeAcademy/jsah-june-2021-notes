# Numbers

A **number** is what it sounds like -- any integer or decimal.

```js
10 - 12;
3.14;
```

- Many programming languages make a distinction between integers, and decimals.
  - A number that is not an integer is also called a _floating point number_ or _float_
- JavaScript doesn't
- This can lead to some ...odd behaviors

[MDN Docs for Number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number)

---

# Arithmetic
We can use the following operations on numbers.

| operand | name                        | example  | =   |
| ------- | --------------------------- | -------- | --- |
| +       | addition                    | 3 + 2    | 5   |
| \*      | multiplication              | 3 \* 2   | 6   |
| /       | division                    | 3 / 2    | 1.5 |
| %       | modulus ("remainder")       | 3 % 2    | 1   |
| \*\*    | exponentiation ("power of") | 3 \*\* 2 | 9   |

Remember, **PEMDAS**? Order of operations are important, and parentheses are free to use.

> When in doubt, use parentheses!

---
# Strings plus Numbers
Even though strings and numbers are different *types*, JavaScript automatically converts one to the other. This is called *type coercion*.

```js
> 1 + 2 // No type coercion
3
> "1" + "2" // No type coercion
'12'
> "1 + 2" // No type coercion
'1+2'
> "1" + 2 // 2 is coerced into a string
'12'
> "30" + 1  // 1 is coerced into a string
'301'
> "30" - 1  // "30" is coerced into a number
29
```
The best way to make sure your code acts the way you want is to do *type conversion* to explicitly declare what type you want to win.

## Converting a Number to a String
Use the `.toString()` method on a number.
```js
(12).toString() // => '12'
```
## Converting a String to a Number
There are many ways to [convert a string to a number in JavaScript](https://coderwall.com/p/5tlhmw/converting-strings-to-number-in-javascript-pitfalls).

The easiest and cleanest is `unary +`:
```js
+"12" // => 12
+"012" // => 12
+"0.2" // => 0.2
+"cheese" // => NaN
+"0" // => 0
+"" // => 0
```
---

# The Math Class

- In JavaScript there is a class called `Math` (More on classes and Objects later)
- It helps with mathematical operations
- Often used to round numbers, or set them to a certain number of decimal places
- It can be used to generate random numbers
    * Calling `Math.random()` returns a random *decimal* number between 0 and 1.

---

# Math in JavaScript can be Wonky
All JavaScript numbers are **floating-point numbers**. However, some rational numbers cannot be represented in floating-point which means that simple arithmetic may give unexpected results.

For instance, you cannot go higher than about 9 quadrillion without glitching.

```js
> 2**53===2**53+1
true
```

Other wonky arithmetic to be aware of
```js
> 7/9 
0.7777777777777778

> 0.5 - 0.4 - 0.1
-2.7755575615628914e-17

> (0.8 - 0.7 - 0.1)/(0.5 - 0.4 - 0.1)
-3

> 2**53 == 2**53+1
true

> 2**10000
Infinity
```
See [Wikipedia on IEEE 754 double](https://en.wikipedia.org/wiki/Double-precision_floating-point_format) aka Double-precision floating-point format or binary64 if you're interested in learning more about *why* this happens.