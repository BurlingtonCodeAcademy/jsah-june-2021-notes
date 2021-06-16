
# Operators

A character or group of characters that represent an action to be taken on one or more values.

* Unary Operators
  * `+`
  * `delete`
  * `typeof`
  * `void`
  * Incrementers/Decrementers

* Binary Operators
  * Arithmetic Operators
  * Logical Operators
  * Comparison Operators
  * Assignment Operators
  * Bitwise Operators

* Trinary Operators
  * The Ternary Operator

---

# The Unary +

The `+` operator can be used on an operand to convert that operand into a number
```js
+"33" // => 33
+"0" // => 0
+"" // => 0
+" "// => 0
+"cheese" // => NaN
```

# delete

The keyword `delete` is an operator that deletes whatever property, or element that's passed to it as an operand. However delete can't be used to delete full objects.

```js
delete objectName // returns false, objectName still exists
delete objectName.prop // deletes the property `prop` off of the object `objectName`
delete arrayName[3] // deletes the element at index three of the array `arrayName`
```

# typeof

The keyword `typeof` is a unary operator that returns the type of the operand it's called on as a string.

```js
typeof function() {...} // => 'function'
typeof "Hello, world!" // => 'string'
typeof [1, 2, 3, "red"] // => 'object'
typeof unassignedVariable // => 'undefined'
typeof false // => 'boolean'
typeof null // => 'object
```

# void

The `void` keyword takes an expression as its operand and causes it to return undefined rather than the normal return value of the expression.

We won't use this operator very often in this course.

```js
void (1+1) // => undefined

function sayHello() { return "Hello, world!" }

void sayHello() // => undefined
```

# Incrementers/Decrementers

Incrementers and decrementers only work on the number type.
 * `++` increments the value to its left by 1
 * `--` decrements teh value to its left by 1

 ```js
 3++ // => 4
7-- // => 6
"cheese"++ // => NaN
 ```
---
# Arithmetic Operators

Takes two numbers and performs an operation on them

Returns a new number

* `+` addition

* `-` subtraction

* `*` multiplication

* `/` division

* `%` modulus
  * modulus evaluates to the *remainder* of the division

* `**` exponent

```js
2 + 1 // => 3
2 - 1 // => 1
2 * 2 // => 4
6 / 2 // => 3
6 % 3 // => 0
6 % 5 // => 1
5 ** 2 // => 25
```

# Logical Operators

Evaluates two values or expressions and returns a boolean

`&&` **and**; evaluates true if BOTH sides are truthy

`||` **or**; evaluates true if EITHER side is truthy

`!` **not**; inverts the truthyness/falsyness of the preceding value or expression

```js
'dog' && 'cat' // => 'cat'
null && 'cat' // => false
'dog' || 'cat' // => 'dog'
undefined || 'cat' // => 'cat'
!true // => false
!(7 < 5) // => true
```

# Comparison Operators
Compares two values and returns a boolean

`>` greater than

`<` less than

`>=` greater than or equal to

`<=` less than or equal to

`==` equal to
* Asks: are these values equal?
* The double equals will try to coerce the operands so that they match if possible
```js
"12" == 12 // => true
```


`===` identity
* Asks: are these two values *exactly* the same? This takes into account `typeof` each value.
* When **comparing** two values you should always use the triple equals
```js
"12" === 12 // => false
```

`!=` not equal

`!==` REALLY not equal

```js
5 > 3 // => true
5 < 3 // => false
5 >= 3 // => true
5 <= 5 // => true
5 == '5' // => true
5 === '5' // => false
'cat' != 'dog' // => true
'cat' !== 'cat' // => false
```

# Assignment Operators
Modifies an existing value MUTATES the value.

* `=` sets the variable on the left equal to the value on the right

* `+=` adds the value to the right to the variable on the left

* `-=` subtracts the value to the right from the variable on the left

```js
let x = 7
let y = 3

1 += 2 // => 3
x = y // x => 3
x += y // x => 10
x -= y // x => 4
```
---
# Ternary Operator

The *ternary operator*, also called the conditional operator, is the only trinary operator in JavaScript, and is a way of handling control flow.

```js
expression ? valueOne : valueTwo // If the expresion evaluates to true returns valueOne, otherwise returns valueTwo
```