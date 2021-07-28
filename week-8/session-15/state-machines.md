# State Machines

A state machine is a system with a number of defined 'states'. The system can only be in one state at a time, and with defined rules to 'transition' between states.

At their simplest a state machine is an object, with the top level keys referencing the current state, and the values of those keys being an array of allowable transitions.

They also use a function to determine if they can change to a certain state, and prevent invalid state changes.

---

# State Machine Example: Traffic Light

![traffic light](https://res.cloudinary.com/btvca/image/upload/v1574445209/curriculum/traffic-light_saqe87.jpg)

1. How many states? What are their names?
2. Can it be in more than one state at a time?
3. What are the rules for transitioning between states?

<small>image by [katerha](https://www.flickr.com/photos/katerha/6919352910)
</small>

---

# State Transition Diagram: Traffic Light

```
[G] -> [Y] -> [R] <--> [FR]
 ^             |
  \___________/
```

- green can transition to yellow
- yellow can transition to red
- red can transition to _either_ flashing red, or green
- What if there was a "left turn ok" green light as well?

---

# State Machine Example: GUI Button

States:

1. Enabled
2. Disabled
3. Pressed
4. Active

Transitions:

- [enabled] -> mouseDown -> [pressed]

  - "when the mouse is pressed, render the button as being pressed"

- [pressed] -> mouseUp -> [active]
  - "when the button is 'down', and the user releases the mouse button, enter the 'active' state"
- [pressed] -> mouseExit -> [enabled]
  - "when the button is 'down', and the pointer leaves the button, re-render the button as up (not pressed)"
- [enabled] -> mouseUp -> []
  - "when the button is 'up', and the user releases the mouse button, do nothing"
- ... and so on

We may also need a state transition action: "when the button enters the 'active' state, send a 'click' event and then enter the 'Enabled' state"

---

# Why use a state machine?

1. Clarity
2. Predictability
3. Fail-fast debugging

- Many bugs are due to the system receiving unexpected input, or input that is inappropriate _at the moment_
- an "illegal state transition" error means something unexpected _just_ happened
  - so you may need to add a new transition (or validation routine, or error handler) to handle it when it happens again
- Without a state machine, the system may remain in an invalid state for some time
  - this makes it harder to debug once something eventually _does_ break

---

# State of the State

> The term "state" has several overlapping meanings.

- in general, "state" means any data
  - especially in OO, e.g. "state and behavior" means "instance variables and instance methods"
- in particular, "state" means "there is a clear state transition diagram at work here"

> The term "state machine" has several technical variants as well.

- "Infinite State Machine" e.g. Turing Machine
- "Finite State Machine" or "Finite State Automaton" e.g. Conway's Game of Life

<https://en.wikipedia.org/wiki/Finite-state_machine>

---

# How to implement a state machine?

> There's more than one way to do it.

Easiest way is with something like this:

### Setting up the Allowable Transitions

The first step when creating a state machine is to set up an object that will hold your allowable transitions. You will need a key to represent each possible state, and a value that's an array of possible transitions.

```js
let states = {
  green: { canChangeTo: ["yellow"] },
  yellow: { canChangeTo: ["red"] },
  red: { canChangeTo: ["green"] },
};
```

We need to keep track of the current state so we store it in a variable.

```js
let currentState = "green";
```

### Moving Between States

To enforce our state machine we will create a function that knows what the current state is, and accepts the next state as an argument.

If the change from the current state to the next state is valid we change our current state, otherwise we throw an error and the state doesn't change.

```js
function enterState(newState) {
  let validTransitions = states[currentState].canChangeTo;
  if (validTransitions.includes(newState)) {
    currentState = newState;
  } else {
    throw (
      "Invalid state transition attempted - from " +
      currentState +
      " to " +
      newState
    );
  }
}
```

---

# State Machine

All together, our state machine looks like this:

```js
let states = {
  green: { canChangeTo: ["yellow"] },
  yellow: { canChangeTo: ["red"] },
  red: { canChangeTo: ["green"] },
};

let currentState = "green";

function enterState(newState) {
  let validTransitions = states[currentState].canChangeTo;
  if (validTransitions.includes(newState)) {
    currentState = newState;
  } else {
    throw (
      "Invalid state transition attempted - from " +
      currentState +
      " to " +
      newState
    );
  }
}

console.log("State is: ", currentState);

enterState("yellow");
console.log("State is: ", currentState);

enterState("red");
console.log("State is: ", currentState);

enterState("green");
console.log("State is: ", currentState);

enterState("blue");
```

Output:

```js
State is: green
State is: yellow
State is: red
State is: green
Invalid state transition attempted - from green to blue
```

---

# Object State Machine

We can refactor our code into an object that has the same functionality:

```js
class StopLight {
  constructor(color) {
    let validColors = ["red", "yellow", "green"];
    if (validColors.includes(color)) {
      this.color = color;
    } else {
      this.color = green;
    }
  }

  enterState(newColor) {
    if (this.canChangeTo(newColor)) {
      this.color = newColor;
    } else {
      throw (
        "Invalid state transition attempted - from " +
        this.color +
        " to " +
        newColor
      );
    }
  }

  canChangeTo(newColor) {
    let validTransitions = {
      green: ["yellow"],
      yellow: ["red"],
      red: ["green"],
    };

    let allowed = validTransitions[this.color];

    if (allowed.includes(newColor)) {
      return true;
    } else {
      return false;
    }
  }
}

let myLight = new StopLight("green");

console.log("State is: ", myLight.color);

myLight.enterState("yellow");
console.log("State is: ", myLight.color);

myLight.enterState("red");
console.log("State is: ", myLight.color);

myLight.enterState("green");
console.log("State is: ", myLight.color);

myLight.enterState("blue");
```

---

# Transitioning Between Objects

Often times you will want to do more than just change from one string to another. You'll need to transition between more complex data structures like objects.

We can combine state machines, and _lookup tables_ to allow for more complex interactions.

You can still keep track of the current state as a string, and use our state machine just as we previously set it up. The difference comes in how we use that current state. If you need to map it to an object you can create a lookup table which you access _at the current state_.

---

# Lookup Tables

A lookup table is an object that is used to map strings to other values.

In the object the string you are expecting is used as the key (because all keys on an object are strings), and the value you want to match.

Lookup tables are useful in many situations, such as:

- mapping abbreviations to full words
- mapping strings to variables
- extending allowable user input

---

# Mapping strings to variables

One of the most common uses for a lookup table is to match a string (usually some form of user input) to a variable.

If we had a program that accepts a poet's name, and prints the title of a poem by that poet it might look something like this:

```js
let poetLookup = {
  "Robert Frost": "Stopping by Woods on a Snowy Evening",
  "Shel Silverstein": "Falling Up",
  "Sylvia Plath": "The Bell Jar",
};

function printTitle(userInput) {
  console.log(poetLookup[userInput]);
}
```
