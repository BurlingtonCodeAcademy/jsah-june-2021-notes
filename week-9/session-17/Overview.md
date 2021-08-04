# Tuesday 8/3/2021

We started class by answering questions on [**Zorkington**](https://online.burlingtoncodeacademy.com/lessons/project/zorkington). Below is the example we talked through on moving an item from one array to another:

<details>
<summary>Moving an Item from One Array to Another*</summary>
<div>

```js
let dinnerFood = ['salad', 'soup', 'casserole'];
let breakfastFood = ['omelet', 'pancakes', 'fruit'];

console.log(`From array:  ${breakfastFood}`);
console.log(`To array:  ${dinnerFood}`);

function moveItem(itemToMove , fromArray, toArray) {
  if (fromArray.includes(itemToMove) && !toArray.includes(itemToMove)) {
    // we know the item is in the starting array
    function isItem(currentItem) {
      // if the two items are the same
      // then return the item to the caller
      return itemToMove === currentItem;
    }

    let theItem = fromArray.find(isItem);

    // ['salad', 'soup', 'casserole']
    // ['salad', 'casserole']
    // let start = dinnerFood.slice(0, 1) => ['salad']
    // let end   = dinnerFood.slice(2) => ['casserole']
    let index = fromArray.indexOf(itemToMove);
    let start = fromArray.slice(0, index);
    let end   = fromArray.slice(index + 1);

    fromArray = start.concat(end);
    toArray.push(theItem);
    return true
  }
  
  return false;
}

moveItem('pancakes', breakfastFood, dinnerFood);

console.log(`From array:  ${breakfastFood}`);
console.log(`To array:  ${dinnerFood}`);
```
</div>
</details>
* to be updated
<br/>

In the second part of class, we started learning **HTML** and created our first webpage!

## Homework
Work on your **Zorkington** project! The project will be due next **Thursday, August 5th.**

* [Project Description](https://online.burlingtoncodeacademy.com/lessons/project/zorkington)
* [GitHub Repository](https://classroom.github.com/assignment-invitations/de229a479a7c7f39c08ba90d22f0fa52) 
* Play Zork [here](https://www.pcjs.org/software/pcx86/game/infocom/zork1/)


## Labs
Focus on your **Zorkington** project first, but if you have time and would like to practice some HTML, take a look at this [**Hello HTML Lab**](https://online.burlingtoncodeacademy.com/lessons/written/hello-html).