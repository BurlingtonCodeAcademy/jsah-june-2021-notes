# Tuesday 6/29/2021
Tonight we started by reviewing a number of I/O labs from last week's homework. Solutions exist within the lab definitions, with some additional solutions below.

We reviewed conditionals and learned about using `&&` and <code>&#124;&#124;</code> conjunctions. We took a look at scope and practiced identifying values of variables based on their scope.

## Reading & Homework

Take a shot at reading [Chapter 4 of Eloquent Javascript](https://eloquentjavascript.net/04_data.html) and [Chapter 5 of Eloquent Javascript](https://eloquentjavascript.net/05_higher_order.html). These are *tricky*!


## Practice

### Labs

* [Guess the Variable with Functions](https://bootcamp.burlingtoncodeacademy.com/lessons/javascript/scope#anchor/exercise_guess_the_variable_with_functions)

## Additional Solutions to Homework Practice

#### Good Friend, Bad Friend

<details>
<summary>Solution</summary>
<div>

```js
console.log("What is your name?");

function handleInput(chunk) {
  let name = chunk.toString().trim();
  if (name === 'Darth') {
    console.log('Noooo! That is impossible!');
    process.exit();
  } else if (name === 'bye!') {
    console.log('See you soon!');
    process.exit();
  } else {
    console.log("Hello, " + name + "!");
  }
  console.log('What is your name?')
}

process.stdin.on("data", handleInput);
```

</div>
</details>


#### Enemies List

<details>
<summary>Solution using Arrays</summary>
<div>

```js
console.log("What is your name?");

function handleInput(chunk) {
  let name = chunk.toString().trim();
  name = name.toLowerCase();
  let enemiesList = ['darth','voldemort','sauron','palpatine'];

  if (enemiesList.includes(name)) {
    console.log('Go away you villain!');
    process.exit();
  } else if (name === 'bye!') {
    console.log('See you soon!');
    process.exit();
  } else {
    console.log("Hello, " + name + "!");
  }
  console.log('What is your name?')
}

process.stdin.on("data", handleInput);
```
</div>
</details>