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
Check out [MDN String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String) docs for more.

--- 
# String Escapes

* If you do want to include a special character like a single or double quote in your string you will need to use a *string escape*
* In JavaScript backslash is the *escape character* and means "the next character means something special"
* You can use the escape character to add quotes within your string

```js
'Jane\'s dog has fleas' // => "Jane's dog has fleas"
"I told you yesterday, \"Vermont is my favorite state\"" // => 'I told you yesterday, "Vermont is my favorite state"'
```
* Another use for the escape character is backslash-n (`\n`) which means "newline" or backslash-t (`\t`) which means "tab".
```js
console.log("Roses are red,\n\tViolets are blue;\n\t\tCandy is sweet,\n\t\t\tAnd so are you.") // =>
Roses are red,
    Violets are blue
        Candy is sweet,
            And so are you
```

--- 
# String Messages
You can use may different operators and *methods* on strings.
* **Concatenation**: the combination of two or more strings into a single string
```js
"drive" + "way"
'Java'+"Script"
"Bert's pal Ernie"+ ' sings "Rubber Duckie"'
```
* **toUpperCase and toLowerCase Methods**: **methods** invoke a predefined function on a value; in the case of `toUpperCase()` and `toLowerCase()` they act on a string.

```js
"titanic".toUpperCase() // => TITANIC
"TITANIC".toUpperCase() // => TITANIC
"QUIETLY".toLowerCase() // => quietly
```
* **repeat**: takes a single argument that tells the method how many times to repeat the string
```js
"Java".repeat(4) // => JavaJavaJavaJava
```
* **length**: returns the length property of the string, defined as the number of characters. Length is an inherited property of all strings.
```js
"banana".length // => 6
```
* **Indexes**: to isolate the character of a string you can call the method `charAt()` or `[]` passing the index as a single argument.
```js
"berry".charAt(1) // => e
"berry".charAt(0) // => b
"apple"[3] // => l
```

* **includes & endsWith**: ask the string if it *includes* a substring (in the case of `includes`) or if it *ends with* (in the case of `endsWith`). Both of these evaluate to a boolean value.
```js
"banana".includes("nan") // => true
"banana".endsWith("ana") // => true
"banana".endsWith("ba") // => false
```

* **Replace**: returns a new string that is the old stringby replacing the first set of characters with the second passed in the method
```js
"blueberry".replace("blue", "black") // => blackberry
```

There are tons of built-in string methods, check them out on [MDN's Useful String Methods](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/Useful_string_methods) docs.

---

# Slicing and Dicing

Every string is made of lots of other strings.

You can pull out parts of a string with the `slice` method.

This does not *change* or *mutate* the string you are calling it not.

```js
// this means "slice from character 0 to character 4"
"blueberry".slice(0, 4) 

// this means "slice from character 4 to the end
"blueberry".slice(4)
```

These start and end numbers are called *indexes* (or *indices* if you're feeling fancy).

[MDN: Slice](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/slice)

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
# String Comparison
JavaScript strings respond to the `<` and `>` operators.

```js
> "apple" > "cherry"
false
> "banana" < "cherry"
true
```
>Strings are compared one character at a time using the *Unicode* values of each character.

* **BEWARE**: In ASCII and Unicode, because of the way that all the uppercase letters are together, followed by all lowercase letters (codes 97 to 122).

> That means that all uppercase strings are less than all lowercase strings.

```js
> "apple" < "banana"
true
> "apple" < "BANANA"
false
```

For example, if you say `"apple" < "apricot"`, JavaScript does something like this behind the scenes:
```js
> "apple".charCodeAt(0)
97
> "apricot".charCodeAt(0)
97

> "apple".charCodeAt(1)
112
> "apricot".charCodeAt(1)
112

> "apple".charCodeAt(2)
112
> "apricot".charCodeAt(2)
114
```
In the above, 112 is less than 114, so the comparison stops there and returns true.

## ASCII