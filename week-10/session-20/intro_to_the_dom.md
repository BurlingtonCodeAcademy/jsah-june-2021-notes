# The DOM

- stands for Document Object Model
  - "Document" = HTML page
  - "Object Model" = way of describing page elements
    - tags, attributes, styles, text, etc.
- Mostly standard
  - but there are some browser differences
- Core DOM objects
  - Node, Element, Text, Comment, Attr

---

# DOM Scripting

"Scripting" is a term used when you're writing programs that don't do much _on their own_; instead scripts usually use other, more advanced programs, or are embedded within them.

"DOM Scripting" means using JavaScript to manipulate the DOM (page elements and contents) inside a web page, either during page load, or in response to user events, like clicking a button or selecting text.

---

# Scripts as Attributes

This is the simplest way to execute JavaScript inside a Web page.

```html
<button name="button" onclick="alert('Abracadabra!')">Magic</button>
```

Try it out here: <button name="button" onclick="alert('Abracadabra!')">
Magic
</button>

`onclick` is an _attribute_ that contains a _script_ that pops up an alert box. Also known as an _event handler_.

(We will discuss several other ways to attach event handlers later in this lesson.)

---

# The Script Tag (no src)

Without a src attribute, it defines a script and immediately executes its code:

```html
<script>
  var message = "Shazam!";
  alert(message);
</script>
```

<script>
  var message = "Shazam!"
  alert(message)
</script>

---

# The Script Tag (src)

With a `src` attribute, it _loads code from a separate file_, and _immediately executes_ it:

```html
<script src="tictactoe.js"></script>
```

This code expects a file named `tictactoe.js` to _exist on the server_ in the same directory as the HTML file.

The `script` tag may appear in the `head` or in the `body`. Scripts are executed in top-to-bottom order.

> HINT: to be sure that your code executes after the page has been fully loaded, put your `<script>` tags at the bottom of the `<body>` section.

---

# The `document`

In a DOM script, the current page is always available via the _global variable_ named `document`.

In addition to providing many useful _functions_, it also provides some _properties_:

| Property                                   | Description                                                                                                                                                           |
| ------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `document.URL`                             | the URL of the current page, in the form of a string.                                                                                                                 |
| `document.location`                        | the URL of the current page, in the form of a Location object.                                                                                                        |
| `document.location = 'http://example.com'` | causes the browser to visit that web page.                                                                                                                            |
| `document.title`                           | the _title_ of the document, which appears inside windows and tabs.                                                                                                   |
| `document.title = 'the joy of cooking'`    | immediately changes the _title_ of the document. Some apps use this to display, e.g., a count of unread messages, which the user can then see without switching tabs. |

<https://developer.mozilla.org/en-US/docs/Web/API/Document>

---

# Finding an Element by ID

If an element has an `id` attribute, you can get a _pointer_ to that element with a single line of code:

```js
let element = document.getElementById(id);
```

Once you have a pointer to that element, you can manipulate it further. You can also log it to the console for further inspection using:

```js
console.log(element);
```

<https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById>

---

# Finding an Element by CSS Selector

```js
let element = document.querySelector("main div.preview > p");
```

This returns the first Element within the document that matches the specified selector (in this case, the first `<p>` that is a direct child of any `<div class='preview'>` that is in the `main` section).

<https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector>

---

# Using an Element

Once you find an element (using `getElementById` or any other way), you can start attaching behavior, or modifying its attributes.

```js
let header = document.getElementById("header");
let text = header.textContent;
```

There is also a property called `innerText` but it's confusing and implemented differently in different browsers.

<https://developer.mozilla.org/en-US/docs/Web/API/Node/textContent>

---

# Code Along: Update an Element

<iframe height="600" style="width: 100%;" scrolling="no" title="DOM-scripting-lab-1" src="https://codepen.io/burlingtoncodeacademy/embed/preview/gOpMvgr?height=265&theme-id=light&default-tab=html,result&editable=true" frameborder="no" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href='https://codepen.io/burlingtoncodeacademy/pen/gOpMvgr'>DOM-scripting-lab-1</a> by Joshua Burke
  (<a href='https://codepen.io/burlingtoncodeacademy'>@burlingtoncodeacademy</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

---

# Nodes vs Elements

In the DOM, the term "node" means _almost any_ item that you can find in the document tree.

When you're hunting for a function or property, sometimes it's on a Node, and sometimes it's on an Element. Make sure to check _both_ of these documentation pages:

- <https://developer.mozilla.org/en-US/docs/Web/API/Node>
- <https://developer.mozilla.org/en-US/docs/Web/API/Element>

For instance, `attributes` is a property of an Element, but `childNodes` is a property of a Node.

---

# Other Node Types

An element is a particular type of node, and it's the most common, but beware, these are also nodes...

- Document, Element, Text, Comment, CDATASection, ProcessingInstruction, DocumentFragment, DocumentType, Notation, Entity, EntityReference

...and all of them have their own properties that are _not_ part of the basic Node set.

> Also, this sense of "node" is **completely different** from the "node" in NodeJS. :-(

---

# Finding Many Elements

In addition to getting a _single_ element by its `id` or a CSS selector, you can also ask the document to give _all_ elements that match a certain criterion.

by _CSS Class_ name

```js
let elements = document.getElementsByClassName("profile-picture");
```

by _Element_ name

```js
let elements = document.getElementsByTagName("h2");
```

by _CSS Selector_ expression

```js
let elements = document.querySelectorAll("h2.preview > p");
```
---

# HTML Collections

DOM queries that can target multiple elements always return a data structure called an *HTML Collection*. This is an array like object, but it *is not an array*. It will be an ordered list with a `length` property, but has no methods attached to it.

We can turn it into a real array several different ways

* `Array.from(collection)`
* Iterate over it with a `for...of` loop, and push each value to an empty array
* use the *spread* operator `[...collection]`

Please not that I am using `collection` as a variable name to represent the HTML collection. The word "collection" has no special meaning in JavaScript.

---

---
# Events as Functions
In JavaScript, *event handlers are callback functions*.

The classic example of an event handler is "onclick", i.e. "please call this function when the user clicks this button".

To attach an event handler,

1) Find the element, e.g.

```js
let button = document.getElementById('magic');
```
2) Attach the callback, like this:
```js
button.addEventListener('click', () => { alert('Abracadabra!') });
```

> NOTE: using the "fat arrow" for event handlers is a very good idea since fat arrows will restore the this variable to point to the same object as when the listener was added.

https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener

---
# LAB: Update Element on Click
<iframe height="300" style="width: 100%;" scrolling="no" title="DOM-scripting-lab-2" src="https://codepen.io/burlingtoncodeacademy/embed/vYOKdJO?default-tab=html%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/burlingtoncodeacademy/pen/vYOKdJO">
  DOM-scripting-lab-2</a> by Burlington Code Academy (<a href="https://codepen.io/burlingtoncodeacademy">@burlingtoncodeacademy</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

---

# Events by Reference

If you have already defined an event handler function, you can attach it by reference, like this:
```js
<button type="button" id="magic">Magic</button>
<script>
function sayMagicWord() {
    alert('Shazam!');
}
let button = document.getElementById('magic');
button.addEventListener('click', sayMagicWord)
</script>
```
>NOTE: if you attach a listener by reference, pass the name of the function only! Do not immediately invoke the function, like this:

```js
// BAD CODE, DO NOT USE
button.addEventListener('click', sayMagicWord())
```

This **calls the function** `sayMagicWord` when the listener is *attached* and tries to attach the *return value* of `sayMagicWord` (which will likely be `undefined`).

---
# Event Parameters
An event handler function can optionally accept a parameter -- usually called `event` (or just `e`) -- that contains [lots of information about the thing that just happened].

An [event object](https://developer.mozilla.org/en-US/docs/Web/API/Event) has many properties but the most important one is `event.target`, which points to the element where the action took place.

For instance, for a click event, `event.target` contains a pointer to the *element* that was clicked.
```js
<button type="button" id="presto">Presto...</button>
<button type="button" id="abra">Abra...</button>
<script>
var prestoButton = document.getElementById('presto');
var abraButton = document.getElementById('abra');

function sayMagicWord(event) {
  if (event.target === prestoButton) {
    alert('Change-o!');
  } else if (event.target === abraButton) {
    alert('Cadabra!');
  } else {
    alert('Shazam!');
  }
  console.log({event}); // for debugging
}

prestoButton.addEventListener('click', sayMagicWord)
abraButton.addEventListener('click', sayMagicWord)
</script>
```
---

# Event Bubbling & Capture

* Events are created by their elements
* After creation they move up the chain by default
* This behavior can be changed by using `cancel` on the listener
```html
<div onclick="alert('outer div')">OUTER DIV
  <div onclick="alert('inner div')">INNER DIV
    <p onclick="alert('paragraph')">Paragraph</p>
  </div>
</div>
```
<iframe height="300" style="width: 100%;" scrolling="no" title="bubble-events" src="https://codepen.io/Dangeranger/embed/GbjpbP?default-tab=html%2Cresult" frameborder="no" loading="lazy" allowtransparency="true" allowfullscreen="true">
  See the Pen <a href="https://codepen.io/Dangeranger/pen/GbjpbP">
  bubble-events</a> by Joshua Burke (<a href="https://codepen.io/Dangeranger">@Dangeranger</a>)
  on <a href="https://codepen.io">CodePen</a>.
</iframe>

---

# Event Diagram

![Event Flow Diagram](https://bootcamp.burlingtoncodeacademy.com/images/eventflow.svg)