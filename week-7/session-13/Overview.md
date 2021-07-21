# Tuesday 7/20/2021
We started class by going over a few solutions to the [**Looping through an object with for...in**](https://bootcamp.burlingtoncodeacademy.com/lessons/javascript/objects.slides#lab_looping_through_an_object_with_forin) lab.

<details>
<summary>Solution</summary>
<div>

```js
let states = {
  'VT': 'Vermont',
  'CA': 'California',
  'MA': 'Massachusetts',
  'NY': 'New York',
  'WY': 'Wyoming'
}

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
  'VT': 'Vermont',
  'CA': 'California',
  'MA': 'Massachusetts',
  'NY': 'New York',
  'WY': 'Wyoming'
}

for (let shortName in states) {
  if (states.hasOwnProperty(shortName)) {
    let longName = states[shortName];
    console.log(`${shortName} is short for ${longName}`);
  }
}

```

</div>
</details>
We went through the GPA lab.
</br>

## Reading & Homework
* []()

## Labs

## Practice
Check out additional resources and practice with [objects](https://github.com/BurlingtonCodeAcademy/jsah-june-2021-notes/blob/main/resources-0/objects.md).