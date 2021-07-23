# Thursday 7/22/2021
We started class by going over a few solutions to the [**Menu Lab**](https://online.burlingtoncodeacademy.com/lessons/written/menu-order) lab. (Before you look at the solution, make sure you attempt it on your own! Remember, practice, practice, practice)

<details>
<summary>Solution</summary>
<div>

```js
let orderItems = process.argv.slice(2);
let restaurant = {
  menu: {
    burger: 5.0,
    fries: 3.5,
    shake: 1.11,
    salad: 4.25,
  },

  totalOrder: function(order) {
    let total = 0;
    let findItem = (item) => {
      let price = this.menu[item];

      if (price !== undefined) {
        total = total + price;
      } else {
        console.log('Cannot find price for item:', item);
      }

      return total;
    };

    order.forEach(findItem);

    return this.format(total);
  },

  format: function(answer) {
    return `$${answer.toFixed(2)}`;
  },
};

let result = restaurant.totalOrder(orderItems);
console.log(result);
```

</div>
</details>

<br>

We about `classes` and how they allow us to generate multiple objects with the same functionality in a clear and efficient way and created a `Circle` class.

```js
class Circle {
  static fromDiameter(diameter) {
    let circleRadius = diameter / 2;
    return new Circle(circleRadius, 'red', 'smooth');
  }

  constructor(radius, color, texture) {
    this.radius = radius;
    this.color = color;
    if(["fuzzy", "bumpy", "smooth"].includes(texture)) {
      this.texture = texture
    } else {
      this.texture = "fuzzy";
    }
  }

  area() {
    return Math.PI * this.radius * this.radius;
  }

  speak() {
    return `I am a ${this.texture} ${this.color} circle that has an area of ${this.area()}`
  }
}

let circleOne = new Circle(1, 'red');
let circleTwo = new Circle(2, 'blue', 'bumpy');
let circleThree = new Circle(3, 'green', 'smooth');
let circleFour = Circle.fromDiameter(4);

console.log(circleOne.speak());
console.log(circleTwo.speak());
console.log(circleThree.speak());
console.log(circleFour.speak());
```

## Labs
* [Cake Factory](https://online.burlingtoncodeacademy.com/lessons/written/cake-constructor)
