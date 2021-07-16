# Software Models the World

* Data Structures allow for programmers to make models of the world in code.
* People naturally think of the world as made up of things.
* Programming languages have ways to represent things.
* JavaScript's primary way of representing a thing is an "Object".
* JavaScript objects let you describe things in any way you can imagine.
  * As long as your description is valid JavaScript :)

> All models are wrong, but some are useful. -- [George Box](https://en.wikipedia.org/wiki/All_models_are_wrong)

---

# An Object Contains Properties

```javascript
let abby = {
  'species': 'dog',
  'color': 'brown',
  spayed: true,
  breed: 'mutt',
  weight: 40,
  'favorite activity': 'chasing squirrels'
};
```

* This is called **object literal** syntax since it defines the object exactly as it's **written**.
* The word on the left is called the *key*; the string on the right is called a *value*; the two together are called an *entry* or a *property*.
  * Property keys **must** be valid *variables*
* JavaScript object keys are always strings, but if the key can be represented as a variable, you can omit the quotations
* `let abby = {...}` is an assignment, setting the variable `abby` to point to the object we just defined

---

# An Object is a Lookup Table

An object is useful for putting many similar things together.

Let's make an object that maps a state's *abbreviation* to its *full name*

```javascript
let states = {
  VT: 'Vermont',
  CA: 'California',
  MA: 'Massachusetts',
  NY: 'New York'
};
```

---

# Getting Object Properties

You can get the properties of an object with either *dots* or *brackets*:

| With Dots   | With Brackets  | The Value         |
|-------------|----------------|-------------------|
| `states.VT` | `states['VT']` | `'Vermont'`       |
| `states.CA` | `states['CA']` | `'California'`    |
| `states.MA` | `states['MA']` | `'Massachusetts'` |
| `states.NY` | `states['NY']` | `'New York'`      |

Both syntaxes are useful in different situations. When you know what variable you want to use 

```javascript
states['VT']  // 'Vermont'
states.VT    // also 'Vermont'
```

---

# Setting Object Properties

* You can set the properties of an object with either *dots* or *brackets* followed by a `=` (single equal sign)
* Adding properties works even after the object has been created.

```javascript
states.WY = 'Wyoming';

states['FL'] = 'Florida';
```

* Setting a property with a key that already exists *removes* the original value first
```javascript
states.VT = 'The Green Mountain State'
```

---

# Dots vs. Brackets

Dots are much more common than square brackets, but less versatile, since some keys simply cannot be represented using dot notation, and trying to use them causes syntax errors.

The bracket `[]` syntax is less common but covers more uses, and is generally only used when you are trying to access the object using a *variable*.

```javascript
> let capitals = {}
{}

> capitals.New York = 'Albany'
capitals.New York = 'Albany'
             ^^^^
SyntaxError: Unexpected identifier

> capitals.'New York' = 'Albany'
capitals.'New York' = 'Albany'
         ^^^^^^^^^^
SyntaxError: Unexpected string
```

If you get those errors, revert to brackets, which is more reliable:

```js
> capitals['New York'] = 'Albany'
'Albany'
> capitals
{ 'New York': 'Albany' }
```
---

# Dots, Brackets, and Variables

The primary use of square bracket syntax is to use variables instead of literals to get and set properties.

Given this code ...
```js
let items = {
    brick: 'red'
}
let item = 'brick'
```
... two of the following expressions look for a key named item, but only one looks for a key named the value of the variable named item:

|code|	value|	explanation|
|-|-|-|
|`items.item`|	`undefined`|	"get me the property named 'item'"|
|`items['item']`|	`undefined`|	"get me the property named 'item'"|
|`items[item]`|	`'red'`|	"get me the property named 'brick'"|

> This can be confusing!

---

# An Object is a Data Structure

Objects are good for a lot more than mere one-to-one maps. They allow you to design *data structures* that are as complicated and as deeply nested as you can imagine...

```javascript
let alice = {
  name: 'Alice Abrams',
  age: 36,
  married: false,
  homeAddress: {
    street: '12 Maple St.',
    city: 'Burlington',
    state: 'VT',
    zipCode: '05401',
    location: {
      latitude: 44.4759,
      longitude: -73.2121
    }
  },
  pets: ['Mittens', 'Fido']
}
```
---

# Accessing the Inner Objects

Given the object from the previous slide, the value of `alice.homeAddress.street` is `'12 Maple St.'`

> Note: The above shows the essence of [JSON](/lessons/slides/json):
> a syntax for representing data structures containing primitive values,
> including nested objects and arrays.

---

# `Object.keys`

`Object.keys` is a special function that:

  * takes any object as an argument
  * returns an array
  * containing that object's keys

Example:

```javascript
Object.keys(states)  //=> [ 'VT', 'CA', 'MA', 'NY' ]
```

---

# Accessing All the Properties

You aren't always going to be working with objects that you created. In web development you will often be fetching objects from elsewhere on the internet, and using them in your programs.

* `Object.keys` gives you an array of all keys
* You can use the array to access the values of all keys on an object
* useful for debugging
* useful as another method of iterating over an object
* useful for checking a property exists on the object

---

# All keys are strings, even nulls

* In a JavaScript object, keys are strings that should also be valid variables

* **Beware** of using these as keys, since they get converted to strings in unexpected ways:
  * `null`
  * `undefined`
  * `''` (empty string)
  * `false` or `true`
  * `0` (or any number)

---

# `delete`

To remove a key-value pair from an object, use the keyword `delete`:

```js
states = {
  CA: 'California',
  MA: 'Massachusetts',
  NY: 'New York'
}

// { ca: 'California', ma: 'Massachusetts', ny: 'New York' }

delete states.ma

// Returns true

states

// { ca: 'California', ny: 'New York' }
```

---

# Fake delete

The preferred way of removing an object's values in JavaScript is to nullify it. We can do this by setting the value to `null` or `undefined`.

```js
states.ca = null

states.ny = undefined

states
// { ca: null, ny: undefined }

let stateAbbrevs = Object.keys(states)

for (let abbrev of stateAbbrevs) {
  console.log(states[abbrev])
}
```

> This only removes the *value*, but not the *key*, from the property list.
