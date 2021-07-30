# Thursday 7/29/2021

We started class reviewing solutions to the [**Walkway Lab**](https://online.burlingtoncodeacademy.com/lessons/written/walkway) and talking a bit more about state machines.

<details>
<summary>Solution #1</summary>
<div>

```js
let walkPath = {
  home: {
    canChangeTo: ["walkway"],
    description: "my apartment on 123 Python Ave",
  },
  walkway: {
    canChangeTo: ["store", "home"],
    description: "the lonely streets of Kansas",
  },
  store: {
    canChangeTo: ["walkway"],
    description: "the walmart 15 miles away from my house",
  },
};

let currentLocation = "home";

function moveLocation(location) {
  let validTransitions = walkPath[currentLocation].canChangeTo;
  if (validTransitions.includes(location)) {
    console.log(`\nMoving from ${currentLocation} to ${location}`);
    currentLocation = location;
    console.log(`${walkPath[currentLocation].description}`);
  } else {
    throw "Invalid pathway enter:" + currentLocation + "to" + location;
  }
}

moveLocation("walkway");
moveLocation("store");
moveLocation("walkway");
moveLocation("home");
```

</div>
</details>

<details>
<summary>Solution #2 (WalkPath as an Object)</summary>
<div>

```js

class WalkPath {
  constructor() {
    this.home = {
      canChangeTo: ["walkway"],
      description: "my apartment on 123 Python Ave",
    }
    this.walkway = {
      canChangeTo: ["store", "home"],
      description: "the lonely streets of Kansas",
    }
    this.store = {
      canChangeTo: ["walkway"],
      description: "the walmart 15 miles away from my house",
    }
  }

  moveLocation(location) {
    let validTransitions = this[currentLocation].canChangeTo;
    if (validTransitions.includes(location)) {
      console.log(`\nMoving from ${currentLocation} to ${location}`);
      currentLocation = location;
      console.log(`${this[currentLocation].description}`);
    } else {
      throw "Invalid pathway enter:" + currentLocation + "to" + location;
    }
  }
};

let walkPath = new WalkPath();

let currentLocation = "home";

walkPath.moveLocation("walkway");
walkPath.moveLocation("store");
walkPath.moveLocation("walkway");
walkPath.moveLocation("home");

```

</div>
</details>

<details>
<summary>Solution #3</summary>
<div>

```js
class Place {
  constructor(location, description, canChangeTo) {
    this.location = location;
    this.description = description;
    this.canChangeTo = canChangeTo;
  }
}

//object
let home = new Place("home", "You are home where your dogs are hungry.", [
  "walkway",
]);
let walkway = new Place("walkway", "Walking down a sidewalk.", [
  "home",
  "store",
]);
let store = new Place(
  "store",
  "You are at the store and already know you forgot something.",
  ["walkway"]
);
let bar = new Place("bar", "Where everyone knows your name.", ["walkway"]);
//create state object
let currentLocation = {
  home: { canChangeTo: ["walkway"] },
  walkway: { canChangeTo: ["home", "store"] },
  store: { canChangeTo: ["walkway"] },
};

let currentState = home;

function moveLocation(newLocation) {
  let validTransitions = currentState.canChangeTo;
  if (validTransitions.includes(newLocation.location)) {
    console.log(
      `Moving from ${currentState.location} to ${newLocation.location}`
    );
    currentState = newLocation;
  } else {
    throw (
      "Invalid state transition attempted - from " +
      currentState.location +
      " to " +
      newLocation.location
    );
  }
  console.log(currentState.description);
}

moveLocation(walkway);
moveLocation(store);
moveLocation(walkway);
moveLocation(home);
moveLocation(bar);
```
</div>
</details>

In the second part of class we introduced the new project for the week, [**Zorkington**](https://online.burlingtoncodeacademy.com/lessons/project/zorkington).

## Homework
Work on your **Zorkington** project! The project will be due next **Thursday, August 5th.**

* [Project Description](https://online.burlingtoncodeacademy.com/lessons/project/zorkington)
* [GitHub Repository](https://classroom.github.com/assignment-invitations/de229a479a7c7f39c08ba90d22f0fa52) 
* Play Zork [here](https://www.pcjs.org/software/pcx86/game/infocom/zork1/)


## Reading

A few additional readings on state machines if you are interested:

- https://kentcdodds.com/blog/implementing-a-simple-state-machine-library-in-javascript
- https://xstate.js.org/docs/
