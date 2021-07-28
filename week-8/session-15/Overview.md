# Tuesday 7/27/2021

We kicked off class baking some yummy cakes by reviewing the [**Cake Factory**](https://online.burlingtoncodeacademy.com/lessons/written/cake-constructor) lab. Some of the solutions we looked at are below:

<details>
<summary>Solution #1</summary>
<div>

```js

class Cake {
  static defaultCake(decoration) {
    let flavor = "vanilla";
    let icing = "chocolate";

    let validDecoration = ["sprinkles", "cocoa", "fruit"];
    if (validDecoration.includes(decoration)) {
      decoration = decoration
    } else {
      "sprinkles";
    }

    let theCake = new Cake(flavor, icing, decoration);
    return theCake;
  }

  constructor(flavor, icing, decoration) {
    this.flavor = flavor;
    this.icing = icing;
    this.decoration = decoration;
  }

  describe() {
    return (
      "It is a " +
      this.flavor +
      " cake, with " +
      this.icing +
      " frosting, and " +
      this.decoration
    );
  }
}

let cakeOne = new Cake("chocolate", "caramel", "sprinkles");
console.log(cakeOne.describe());

let defaultCake = Cake.defaultCake("cocoa");
console.log(defaultCake.describe());

```
</div>
</details>

<details>
<summary>Solution #2</summary>
<div>

```js
class Cake {
  static defaultCake() {
    return new Cake("vanilla", "chocolate", "no decorations");
  }

  constructor(flavor, icing, decoration) {
    let invalid = [" ", "", undefined, null];

    if (invalid.includes(flavor)) {
      this.flavor = "vanilla";
    } else {
      this.flavor = flavor;
    }

    if (invalid.includes(icing)) {
      this.icing = "chocolate";
    } else {
      this.icing = icing;
    }

    if (invalid.includes(decoration)) {
      this.decoration = "no decorations";
    } else {
      this.decoration = decoration;
    }
  }

  describe() {
    return `It is a ${this.flavor} cake, with ${this.icing}, and ${this.decoration}.`;
  }
}

let myCake = new Cake("chocolate", "caramel", "sprinkles");
let vCake = new Cake(" ", "strawberry", "strawberries");
let userCake = process.argv.slice(2);
userCake = new Cake(userCake[0], userCake[1], userCake[2]);
let dCake = Cake.defaultCake(); //why no new? because it is being passed directly to defaultCake()?

console.log(myCake.describe());
console.log(vCake.describe());
console.log(userCake.describe());
console.log(dCake.describe());
```

</div>
</details>

<details>
<summary>Solution #3</summary>
<div>

```js
class Cake {
  static makeRedVelvet() {
    return new Cake("red velvet", "vanilla", "sprinkles");
  }

  constructor(flavor, icing, decoration) {
    this.flavor = flavor;
    this.icing = icing;
    this.decoration = decoration;
  }
  describe() {
    return `This cake's flavor is ${this.flavor}, with a yummy ${this.icing} icing, and ${this.decoration} as decorations! Enjoy!`;
  }
}

let cake = new Cake("red velvet", "butter cream", "sprinkles");
let cakeTwo = new Cake("chocolate", "vanilla", "nothing");
let cakeThree = new Cake(
  "strawberry shortcake",
  "whipped strawberry cream",
  " diced strawberries"
);

console.log(cake.describe());
console.log(cakeTwo.describe());
console.log(cakeThree.describe());
console.log(Cake.makeRedVelvet().describe());
```

</div>
</details>

<br>

After that we explored *state machines* as a system that allows us to define rules to transition and move between states. We defined a state machine for a standard traffic light and refactored our code to create a state machine with objects.

## Reading & Homework

- [Walkway Lab](https://online.burlingtoncodeacademy.com/lessons/written/walkway)

## Practice (optional)

If you have extra time and want more practice.

- [Tag Search Lab](https://online.burlingtoncodeacademy.com/lessons/written/tag-search)
