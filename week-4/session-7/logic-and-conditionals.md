# Truthiness

Computers have a very particular idea of when things are *true* and *false*.

To a computer **everything** is one or the other.

```js
1 < 2 // => true
2 + 2 < 4 // => false
2 + 2 <= 4 // => true
"anonymous".endsWith("us") // => true
"every journey".startsWith("a step") // => false

```

---

# Comparisons

*Comparison operators* let you compare two values. JavaScript has all the usual suspects...

|Operator|Comparison|
|---|---|
| `<` | less than |
| `>` | greater than |
| `<=` | less than or equal to |
| `>=` | greater than or equal to |
| `==` | equal to |
| `!=` | not equal |
| `===` | *really* equal to |
| `!==` | *really* not equal to |

[Comparison operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Comparison_Operators) are also called "Boolean operators" after *[George Boole](https://en.wikipedia.org/wiki/George_Boole)*,
a 19th-century mathematician who invented [Boolean algebra](https://en.wikipedia.org/wiki/Boolean_algebra).)

---

# Conditions

The keyword `if` sets up a *conditional* statement.

The phrase immediately after `if` is a *condition*.

```js
if (age < 18) {
  console.log("Sorry, you can't vote yet.");
}
```

|phrase|meaning|
|---|---|
| `if (` ... `)`      | **if** this condition's value is *truthy* |
| `{` ... `}`         | **then** run this block of code |

Wait a second. "Truthy?"

[MDN: if...else](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else)

---

# What is truthiness?

![Truthiness](https://res.cloudinary.com/btvca/image/upload/v1574445211/curriculum/truthiness_jhdubk.png)

* in the Colbert Report [truthiness](https://en.wikipedia.org/wiki/Truthiness) means things we *feel* to be true, even though we know they probably aren't

* In JavaScript, **most** values are *truthy* **unless** they are explicitly *falsy*.

* [MDN: Truthy](https://developer.mozilla.org/en-US/docs/Glossary/Truthy)

---

# What is falsiness?

`false`, `null`, `undefined`, `0`, `NaN`, and the empty string (`""`) are all falsy values.

These are also the *only* falsy values in JavaScript.

Fortunately, `true` is truthy and `false` is falsy.

Unfortunately, the string `"false"` is truthy, and the string `"0"` is truthy, even though the number `0` is falsy. This is because the string contains a character, and, even though the character is `0`, *any string with at least one character is truthy*.

[MDN: Falsy](https://developer.mozilla.org/en-US/docs/Glossary/Falsy)

---

# if... then... else...

The magic word `else` allows **BRANCHING**.

```js
if (age >= 18) {
  console.log("allowed");
} else {
  console.log("denied");
}
```

Like a fork in the road, the program chooses one path or the other.

It takes the first path if the condition is truthy, and takes the second path if the condition is falsy.

---


# The Tragedy of the Equal Sign

* a single equal sign means ASSIGNMENT
  * `name = "Alice"` -- "assign the value 'Alice' to the variable 'name'"
* two equal signs means COMPARISON
  * `name == "Alice"` -- "does the variable 'name' contain the string 'Alice'?"

> This is confusing! (More about it on the next slide.)

---

# Condition or Assignment?

> BEWARE of using a single equal sign inside an `if` condition!

* the value of a comparison is either `true` or `false`
  * so `if (x == 2)` means `if x is 2` which changes based on `x`

* the value of an assignment is the *value being assigned*
  * so `if (x = 2)` means `if 2` which is *always truthy*
  * also, the value of `x` will be 2 afterwards, no matter what it was before

---

# When Should I Use `===`?

Since the rules for type conversion are confusing, most JavaScript experts recommend:

> **always use `===`, never use `==`**

> Using `==` can have some very interesting side effects, see [Stackoverflow](https://stackoverflow.com/questions/359494/which-equals-operator-vs-should-be-used-in-javascript-comparisons)

---

# Conjunction Junction

You can make more complicated logical expressions using conjunctions:

|Conjunction|Operator|Example|Meaning|
|---|---|---|---|
| AND | `&&` | `X && Y` | "are both X and Y true?" |
| OR | <code>&#124;&#124;</code> | <code>X &#124;&#124; Y</code> | "is either X or Y (or both) true?" |
| NOT | `!`  | `!X` | "is X false?" |


```js
if (age >= 18 || hasPermissionSlip()) {
  console.log("allowed");
} else {
  console.log("denied");
}
```

[MDN: logical operators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_Operators)