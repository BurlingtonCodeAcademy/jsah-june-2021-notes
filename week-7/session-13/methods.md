# Object Instance Methods

A method is a *function* attached to an *object* as a *property*.

```js
let stringUtils = {
  capitalize: function(word) {
    return word.charAt(0).toUpperCase() +
      word.slice(1).toLowerCase();
  },
  rant: function(opinion) {
    return option.toUpperCase() + '!!!';
  }
}

stringUtils.rant('i love pizza') //=> 'I LOVE PIZZA!!!'
```

---

# You've Already Used Some Methods!

Most things in JavaScript are objects, and many of them have prebuilt methods which we have been utilizing throughout this course.

* `console.log("some message")` `console` is an object, `.log` is a method
* `string.toUpperCase()` strings have a prototype object, that gives them access all the string methods
* `Math.random()` `Math` is a JavaScript class that has a *static method* `.random()`

---

# Methods Can Access Object State

`this` is a magic word that means "this object I'm in *right now*".

Here are a few examples:

```js
let stringUtils = {
  phrase: "i love pizza!",

  capitalize: function () {
    return (
      this.phrase.charAt(0).toUpperCase() 
      + this.phrase.slice(1).toLowerCase()
    );
  },

  rant: function () {
    return this.phrase.toUpperCase() + "!!!";
  },
};

let loudPhrase = stringUtils.capitalize();
let shoutedPhrase = stringUtils.rant();

console.log(loudPhrase); // => 'I love pizza!'
console.log(shoutedPhrase); // => 'I LOVE PIZZA!!!!!!"
```

```js
let rectangle = {
  height: 10,
  width: 8,
  area: function() {
    return this.height * this.width;
  }
}

rectangle.height   //=> 10
rectangle.area()   //=> 80
```
---
# Extending objects on the fly

Since JavaScript is a *dynamic* language,
you can add methods to *any object*.


```js
let rectangle = {
    height: 10,
    width: 8,
}

rectangle.area()   //=> TypeError: rectangle.area is not a function

rectangle.area = function() {
     return this.height * this.width;
}

rectangle.area()   //=> 80
```

* remember, `this` means "this object I'm in *right now*" which in this case is the rectangle
* `this.height` on the *inside* of the object means the same as `rectangle.height` on the *outside*

---
# Speak
Using the following definition
```js
let dog = {
    name: 'Abby',
    paws: 4
}
```
Please *add a method* to `dog` called `speak` so the following code:
```js
console.log(dog.speak())
```
prints the following line:
```js
My name is Abby and I have 4 paws!
```
