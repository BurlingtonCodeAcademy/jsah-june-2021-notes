# Tuesday 7/20/2021

We started class by going over a few solutions to the [**Looping through an object with for...in**](https://bootcamp.burlingtoncodeacademy.com/lessons/javascript/objects.slides#lab_looping_through_an_object_with_forin) lab.

<details>
<summary>Solution</summary>
<div>

```js
let states = {
  VT: "Vermont",
  CA: "California",
  MA: "Massachusetts",
  NY: "New York",
  WY: "Wyoming",
};

// creates a collection of the keys from the states object
let abbreviations = Object.keys(states);

for (shortName of abbreviations) {
  // 'VT', 'CA', 'MA', 'NY', 'WY'
  let longName = states[shortName];
  let message = `${shortName} is short for ${longName}`;
  console.log(message);
}
```

</div>
</details>

<details>
<summary>Solution</summary>
<div>

```js
let states = {
  VT: "Vermont",
  CA: "California",
  MA: "Massachusetts",
  NY: "New York",
  WY: "Wyoming",
};

for (let shortName in states) {
  if (states.hasOwnProperty(shortName)) {
    let longName = states[shortName];
    console.log(`${shortName} is short for ${longName}`);
  }
}
```

</div>
</details>
</br>
We worked through a few object labs as a group to practice iterating through objects. We wrapped up class by starting to discuss object methods.

## Reading & Homework

* [Menu Lab](https://online.burlingtoncodeacademy.com/lessons/written/menu-order)

If you'd like, take a look at [Chapter 6 of Eloquent Javascript](https://eloquentjavascript.net/06_object.html).

## Practice

Check out additional resources and practice with [objects](https://github.com/BurlingtonCodeAcademy/jsah-june-2021-notes/blob/main/resources-0/objects.md).
