# Arrays

- An array is a _container_
  - an object that contains any type of value
- It's a list of items
- An array is a _data structure_
  - An array is actually an _object_ - more on those soon!

---

# What Makes an Array an Array

- You can put any values inside it
- In any order
- They stay in order (unless you move them later)
- Duplicates are fine

---

# Creating an Array

```js
let fruits = ["apple", "banana", "cherry"];
```

- square brackets on their own mean "please go _create_ an array now"
- and put these 3 other values inside it

---

# Array Indexes

- Every slot in the array has an _index_
- You can retrieve any item in an array by its INDEX
- Square brackets after an array mean "the whatever-th item in this array"
  - This method of accessing items is referred to as "square bracket notation"
- The following code retrieves one fruit

```javascript
let fruits = ["apple", "banana", "cherry"];
fruits[1];
```

...but which fruit?

> `fruits[1]` is `banana`

- You an also access a value at a particular index using a string

```js
fruits["1"]; // => banana
```

---

# Start At Zero

- When counting,
- humans start at one,
- but **computers start at zero**.
- So the first item in an array is the number `0`,
  - not the number `1`.

---

# Length

Every array has a _property_ named `length`

```js
let fruits = ["apple", "banana", "cherry"];
fruits.length; //=> 3
```

- You can also _send a message_ to the array asking for `"length"`

```js
fruits["length"]; // => 3
```

Q: How can you get the last item in an array... even if you don't know its index beforehand?

---

# The End

You usually won't know how long an array is when you're writing functions, or programs that deal with user input. In these cases we'll have to figure out the length of the array programmatically and count backwards from there

```js
let fruits = ["apple", "banana", "cherry"];
fruits[fruits.length - 1];
```

- `fruits.length` evaluates to the number `3`
- then we subtract 1 to get the last index of the array (`2`) because arrays are 0 indexed
- Using an expression as value is not particular to arrays
  - Because JavaScript evaluates expressions _first_ it's a common pattern

---

# After The End

Try this:

```js
fruits[99];
```

Did you get the result you expected?

Why or why not?

---

# Undefined Means 🤷

By returning _undefined_, the computer is answering the question

> "What is the 99th item?"

with the answer

> "I don't know what the 99th item is."

---

# Array Methods

There are many useful methods on arrays. We'll cover many of them in more depth later today.

For now let's look at some of the most common array methods:

- `push`/`shift`
- `pop`/`unshift`
- `reverse`
- `slice`
- `join`
- `split`

[MDN: Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#Methods_2) lists the array API interface -- containing all the methods and properties that are common to all array values.

There are many methods here and you **should not try to memorize them all**. But skim them and remember how to get back to this documentation page later.

---

# Adding Items

- `.push` adds a value to the end of an array

```javascript
let fruits = ["apple", "banana", "cherry"];
fruits.push("pineapple");
fruits; //=> ["apple", "banana", "cherry", "pineapple"]
```

- `.push` can also add several values at once

```javascript
fruits.push("nectarine", "strawberry");
fruits; //=> ["apple", "banana", "cherry", "pineapple", "nectarine", "strawberry"]
```

> `.push` _returns_ the new length of the array

---

# Removing Values from an Array

To remove a value from the end of an array you can use the `.pop` method

- `.pop` always removes the last item in the array
- `.pop` takes no arguments
- `.pop` can only ever remove one item at a time, and it's **always** the last item in the array
- `.pop` returns the item that was removed. THis means you can use it for variable assignments!

```js
let fruits = ["apple", "banana", "cherry"];
let lastFruit = fruits.pop();
fruits; // => ["apple", "banana"]
lastFruit; // => "cherry"
```

---

# Yarra Lasrever

```js
let fruits = ["apple", "banana", "cherry"];
fruits.reverse();
```

Try this now in a console. Do you see what you expect?

> notice that the `.reverse()` method altered the original array

Some methods return a new object as the result of calling the method while others, like `.reverse()`, permanently change or _mutate_ the object that the method is called on.

---

# Slicing and Dicing

you can `slice` an array to cut it into smaller arrays, a lot like how you can slice a string to get a smaller string.

```js
let fruits = ["apple", "banana", "cherry", "date", "elderberry"];

// this means "slice from item 1 to item 3"
fruits.slice(1, 3); //=> [ 'banana', 'cherry' ]

// this means "slice from item 2 to the end"
fruits.slice(2); //=> [ 'cherry', 'date', 'elderberry' ]
```

These start and end numbers are called _indexes_ (or _indices_ if you're feeling fancy).

If you need an item from a middle index you can use `.slice` to access it.

[MDN: slice](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)

---

# Array Indexing Explained

Array indexing works in the same way as string indexing.

Think of the indexes as pointing at the _spaces between_ items, as in this diagram:

```js
0   1   2   3   4
| B | L | U | E |
['B','L','U','E']
```

So with this picture in your mind, imagine that `.slice`...

- includes the item to the _right_ of the start index
- includes the item to the _left_ of the end index...
- ...but _excludes_ the item to the _right_ of the end index

---

# Array to String

There are a few easy ways to turn an array into a string.

So we could take the following array:

```js
let fruits = ["apple", "banana", "cherry"];
```

and

```js
fruits.join(); // 'apple,banana,cherry'
fruits.join(" and "); // 'apple and banana and cherry'
fruits.toString(); // 'apple,banana,cherry'
```

---

# String to Array

You can also easily turn a string into an array with the `.split` method.

This method will give you an array of strings split on whatever character you passed to `.split`.

So if we use the string we got from `.join` on the previous slide we could turn it _back_ into an array

```javascript
"dog".split(""); //=> ['d', 'o', 'g']
"my dog has fleas".split(" "); //=> [ 'my', 'dog', 'has', 'fleas' ]
```

This will work with any string.

> Note also that the character you're splitting on gets removed.

---

# Loops and Iterators

There are many ways to "iterate" through an array.

This means to go through the entire array, one item at a time, usually in order, and then _do something_ with each individual item.

In the next slides we will illustrate 3 different ways to iterate... one way is explicit, one way is concise, and one way is fancy.

---

# Looping Through an Array with _for_

JavaScript inherited `for(;;)` from C; it's cumbersome but you should learn to recognize it.

```js
for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]);
}
```

| phrase                   | meaning                                                  |
| ------------------------ | -------------------------------------------------------- |
| `for`                    | in a loop,                                               |
| `let i`                  | make an index variable named `i`                         |
| `i=0`                    | and initially set it to 0                                |
| `i < fruits.length`      | then, as long as `i` is less than the number of `fruits` |
| `{ ... }`                | execute this block of code                               |
| `console.log(fruits[i])` | print the `i`th element of the `fruits` array            |
| `i++`                    | and then _increment_ `i` before the next time through    |

---

# Looping Through an Array with _for-of_

Recently, JavaScript added `for..of`, which hides the messy details of incrementing an index counter and accessing each array item.

```js
for (let fruit of fruits) {
  console.log("I like " + fruit + "!");
}
```

| phrase      | meaning                           |
| ----------- | --------------------------------- |
| `for`       | in a loop,                        |
| `of fruits` | take each thing inside `fruits`   |
| `let fruit` | name it `fruit`                   |
| `{` ... `}` | and send it to this block of code |

---

# Looping Through an Array with _forEach_

`forEach` is an [iteration method](https://bootcamp.burlingtoncodeacademy.com/lessons/javascript/iteration-methods)  that behaves a lot like `for..of` but in a [*functional style*](https://bootcamp.burlingtoncodeacademy.com/lessons/javascript/hybrid-styles) :

```js
fruits.forEach((fruit) => {
  console.log("I like " + fruit + "!");
});
```

| phrase                | meaning                                |
| --------------------- | -------------------------------------- |
| `fruits.forEach(...)` | hey `fruits`, for each thing inside you, |
| `(fruit)`             | please name it `fruit`                  |
| `=>`                  | and send it to                         |
| `{ ... }`             | this block of code                     |
| `console.log(fruit)`  | so I can print it to the terminal      |

[MDN: Array.forEach](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)

---

# Setting Items in an Array

The `[]` operator works for assignment as well.

`fruits[0] = 'apricot'` will set the `0`th item of the array to the string `'apricot'`

---