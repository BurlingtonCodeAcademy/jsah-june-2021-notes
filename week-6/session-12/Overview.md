# Thursday 7/15/2021
We started class by going over a solution to the [**Titilize with Map**](https://github.com/BurlingtonCodeAcademy/jsah-june-2021-notes/blob/main/week-6/session-11/labs/titileize.md) lab.

<details>
<summary>Solution</summary>
<div>

```js
let words = "the rain in spain falls MAINLY on the PLAIN";

function capitalize(word) {
  let firstLetter = word[0];
  let restOfWord = word.slice(1);
  return firstLetter.toUpperCase() + restOfWord.toLowerCase();
}

console.log(words.split(" ").map(capitalize).join(" "));
```

</div>
</details>

<details>
<summary>Solution using Method Chaining</summary>
<div>

```js
let words = "the rain in spain falls MAINLY on the PLAIN";

function capitalize(word) {
  let firstLetter = word[0];
  let restOfWord = word.slice(1);
  return firstLetter.toUpperCase() + restOfWord.toLowerCase();
}

console.log(words.split(" ").map(capitalize).join(" "));
```

</div>
</details>
</br>

We wrapped up our discussion on array iteration methods from Tuesday and learned about the `.reduce()` method. We spent the majority of class learning about objects!


## Reading & Homework
* [Looping through an object with for...in](https://bootcamp.burlingtoncodeacademy.com/lessons/javascript/objects.slides#lab_looping_through_an_object_with_forin)
    * Hint: you will need to convert the object into keys using `Object.keys()` first, before you use a loop

## Practice
Check out additional resoures and practice with [objects](https://github.com/BurlingtonCodeAcademy/jsah-june-2021-notes/blob/main/resources-0/objects.md).