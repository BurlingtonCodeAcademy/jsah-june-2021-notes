# What makes an Object?

We have set up some objects previously, but what actually makes an object?

- Is it the presence of properties?
- Methods?
- Both? Neither?
- Do any other JavaScript data types behave like objects?

---

# Arrays are Objects

Surprise!

> Every JavaScript array is also a JavaScript object

That means that arrays have properties and methods like any other object.

Examples:

- `array.length` is a _read-only property_ that always contains the number of elements in the array
- `array.reverse()` is a _method_ that reverses the ordering of all elements in the array

See [MDN: Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#Methods_2) to see a lot more array methods

---

# Iteration Methods

Every JavaScript array has a few [very handy methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#Iteration_methods)
that let you _apply a function_ to its contents.

| method                                                                                                      | description                                      | returns                                        |
| ----------------------------------------------------------------------------------------------------------- | ------------------------------------------------ | ---------------------------------------------- |
| [`forEach`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach) | do something to each item                        | `undefined`                                    |
| [`find`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find)       | find the first item that matches                 | one matching item (or `undefined` if no match) |
| [`filter`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)   | accept or reject each item                       | a new collection, possibly smaller             |
| [`map`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)         | change each item into a new item                 | a new collection of the same size              |
| [`reduce`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce)   | scan the entire collection and "reduce" it to... | ...a single result, e.g. a total               |

- We call this group of methods "[iteration methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#Iteration_methods)"
- They all take a _callback function_ that is applied to some set of elements within the array
- There are about a dozen built-in iteration methods, plus lots more added by libraries like [lodash](https://lodash.com/).

---

# forEach

`forEach` works a lot like `for..of`, but using a callback function

Given this array of names...

```javascript
let names = ["Alice", "Bob", "Carol", "Charlie"];
```

This code...

```js
for (let name of names) {
  console.log(name.toUpperCase(name));
}
```

and this code....

```js
function printUpper(name) {
  console.log(name.toUpperCase());
}

names.forEach(printUpper);
```

both print:

```text
ALICE
BOB
CAROL
CHARLIE
DAVID
```

---

# Find

To find the first item that matches the condition...

```javascript
let names = ["Alice", "Bob", "Carol", "Charlie"];

let beginsWithC = function (word) {
  return word.charAt(0).toUpperCase() === "C";
};

let cName = names.find(beginsWithC); //=> 'Carol'
```

Note that:

- the `beginsWithC` function returns `true` or `false`
- the `.find` method returns the _first_ item (from the array)
  - that causes `beginsWithC` to return `true`

---

# Find Inline

For conciseness, people often define the filter function _inline_, like this:

```javascript
let cName = names.find(function (word) {
  return word.charAt(0).toUpperCase() === "C";
});
```

Is this more or less clear than the previous slide?

---

# Filter

the `.filter` iteration method returns _all_ matching values, in a _new array_

```javascript
let names = ["Alice", "Bob", "Charlie", "Carol"];

let beginsWithC = function (word) {
  return word.charAt(0).toUpperCase() === "C";
};

let cNames = names.filter(beginsWithC); //=> [ 'Charlie', 'Carol' ]
```

---

# Map

The `.map` iteration method returns a _new array_ whose elements correspond to the elements of the original array.

```javascript
let names = ["Alice", "Bob", "Charlie", "Carol"];
let upper = function (word) {
  return word.toUpperCase();
};
let bigNames = names.map(upper); //=> [ 'ALICE', 'BOB', 'CHARLIE', 'CAROL']
```

It's called "map" because in a mathematical sense, it defines a _mapping_ from one collection to another.

| from      | to        |
| --------- | --------- |
| 'Alice'   | 'ALICE'   |
| 'Bob'     | 'BOB'     |
| 'Charlie' | 'CHARLIE' |
| 'Carol'   | 'CAROL'   |

---

# Method Chaining

- **method chaining** is the practice of taking the **result** of one method, and immediately calling a method on that result **without assigning it to a variable**, again and again until you get a final result.
- Method chaining can be very elegant, but it can also be very dense, making the code harder to understand, test, and debug.
- "Unspooling" a method chain into intermediate variables can make the code easier to follow, but it can also make it much more verbose and obscure the algorithm.
- For example; we could take the results of a `filter` method, and _chain_ a `map` method off it to return a modified subset of an array.

---

# Reduce

The `reduce` method keeps track of a _running total_ (aka _accumulator_ or _memo_); whatever value the function returns is used as the accumulator for the next pass.

Here's some code that counts the total number of letters across all words in an array:

```javascript
let names = ["Alice", "Bob", "Charlie", "Carol", "David"];

const reducer = function (accumulator, word) {
  return accumulator + word.length;
};

let totalCount = names.reduce(reducer, 0); //=> 25
```

---

# Reduce Explained

The `reduce` algorithm can be difficult to follow at first; here's a walkthrough:

| Iteration | Accumulator In | Word      | Length | Accumulator Out |
| --------- | -------------- | --------- | ------ | --------------- |
| 1         | 0              | 'Alice'   | 5      | 0 + 5 = 5       |
| 2         | 5              | 'Bob'     | 3      | 5 + 3 = 8       |
| 3         | 8              | 'Charlie' | 7      | 8 + 7 = 15      |
| 4         | 15             | 'Carol'   | 5      | 15 + 5 = 20     |
| 5         | 20             | 'David'   | 5      | 20 + 5 = 25     |

The accumulator is used to pass information from one iteration to the next.
