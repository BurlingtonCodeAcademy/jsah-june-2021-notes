# Functions

Remember that a **variable** is a **name** for a piece of data

A **function** is the **name** for a piece of code

---

## Why would you want to name a chunk of code?

Perhaps...

* you have some code you want to run again and again
* you want to do the same operation on different values
* you want to keep your code organized

---

# Function example

Here's an example function:

```js
function add(x, y) {
  let sum = x + y;
  return sum;
}
```

* `function` means "define a function"
* `add` is the *name* of the function
* `x, y` are the *parameters* of the function (also called *arguments*)
* `sum` is a *local variable* of the function
* `sum` is also the function's *return value* because of the magic word *return*

---

# Call Me, Maybe

To use a function,  *call* the function by using its name, plus parentheses with the value(s) you are passing to the function:

```js
function add(x, y) {
  let sum = x + y;
  return sum;
}

add(2, 3)   // returns 5
add(12, 30) // returns 42
```

---

# Shouter

Here is a slightly more complex function that takes some String as input, and as output returns a shouted version of that String.

```js
function shouter(someString) {
  let loudString = someString.toUpperCase();
  return loudString + '!!!';
}

shouter('i like pizza'); // => 'I LIKE PIZZA!!!'
```

The variable `loudString` is called a **local variable** and can only be used **inside** the function.

---

# Passing Variables to Functions

When you pass a *variable* to a function, that variable's *value* is assigned to a *parameter*.

The variable and parameter names **do not** need to match!

```js
function shouter(someString) {
  let loudString = someString.toUpperCase();
  return loudString + '!!!';
}

let feeling = "I feel great";
let strongFeeling = shouter(feeling);
```


| Outside the function | Inside the function | Value               |
|----------------------|---------------------|---------------------|
| `feeling`            | `someString`           | `"I feel great"`    |
|                      | `loudString`     | `"I FEEL GREAT"`    |
| `strongFeeling`      |                     | `"I FEEL GREAT!!!"` |

---

# Four Function Syntaxes

> **WARNING**: JavaScript has many ways to define a function.

[Function declaration syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function)

```js
function add(x,y) { return x + y; }
```

The following are all roughly equivalent to the above:

[Function Expression](https://developer.mozilla.org/en-US/docs/web/JavaScript/Reference/Operators/function)

```js
let add = function(x,y) { return x + y; };
```

[Arrow Function Expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)

```js
let add = (x,y) => { return x + y; };
```

[Arrow Function Expression with implicit return value](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions#Function_body)

```js
let add = (x,y) => x + y;
```

* Note that these new forms are *anonymous*, meaning there is **no name** between `function` and `(x,y)`
    * the name of the function **is** the name of the variable that points to it

---

# Variables and Scope

In JavaScript variables are always in a specific *scope*.

* "Scope" determines where we can use certain variables
* Any variable defined at the *root level* of your file is in the *global scope*
  * Global scope is useful, but dangerous!
* In general, sets of curly braces `{}` create a *new scope*
  * New scopes can always look outside of themselves
  * But **nothing** can look into a different interior scope
* Function parameters are local variables scoped to the function definition
  * Arguments become the values of the parameters.