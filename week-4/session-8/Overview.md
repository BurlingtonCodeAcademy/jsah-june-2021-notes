# Thursday 7/1/2021

Today we reviewed the scope lab/exercise from Tuesday's homework. Solutions exist within the lab definitions, with some additional solutions below.

Please see the week's project at the bottom of these notes

### Exercise Challenge

```js
let poet = 'Robert Frost';

function famousPoem(poet) {
  let poemAuthors = {
    'Robert Frost': 'Stopping by Woods on a Snowy Evening',
    'Walt Whitman': 'Leaves of Grass',
    undefined: 'The Lanyard';, // Billy Collins
  };

  function findAuthor(poet) {
    // looks up the poem by author
    return poemAuthors[poet];
  }

  return findAuthor(poet);
}

console.log(famousPoem('Walt Whitman')); // Which Poem?
console.log(famousPoem(poet)); // Which Poem?

poet = 'Maya Angelou';
console.log(famousPoem()); // Which Poem?
```

### Solution

```js
console.log(famousPoem('Walt Whitman')); // Leaves of Grass
console.log(famousPoem(poet)); // Stopping by Woods on a Snowy Evening
console.log(famousPoem()); // The Lanyard

```

## Reading & Homework

Finish reading [Chapter 4 of Eloquent Javascript](https://eloquentjavascript.net/04_data.html) and [Chapter 5 of Eloquent Javascript](https://eloquentjavascript.net/05_higher_order.html). These are *tricky*!

## Practice

- https://javascript.info/closure#tasks
- https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/local-scope-and-functions
- https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/global-scope-and-functions
- https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-javascript/global-vs--local-scope-in-functions

## Guess the Number Project

Please sign up for the project using the link provided in class, which is also in the announcement within Discord. We will review the progress that has been made, and answer questions about the project on Tuesday, July 6th.

https://online.burlingtoncodeacademy.com/lessons/project/guess-the-number

The project will be due Thursday, July 8th.
