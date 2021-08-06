# CSS

* *Cascading Style Sheets (CSS)*
* CSS, by itself, does nothing.
* Responsible for determining how your HTML looks

---

# Why Does CSS Exist?

* CSS formats your webpage. Without it, there is only content, and no structure or styles.
* Can be written within HTML, or using an external style sheet (the correct way)
Creating external style sheets prevents you from having to write code multiple times, and makes it easy to modify.

---
# Styling Text With CSS

* Using CSS **properties**, you can modify the appearance of your HTML.
* This can done by targeting HTML **elements**.

---

# Inline Style

* Adding the style onto the HTML element directly
* Uses the style attribute of an element
* Declarations go within the style attribute value
```js
<h1 style="color: red; font-size: 32px;">
```

# Example:

Let's say we have the following HTML:

```
<!DOCTYPE html>
<html>
  <head>
    <title>My Cat</title>
  </head>
  <body>
    <h1>My Cat Bob</h1>
    <p>My cat is named Bob. He is a lazy cat.</p>
  </body>
</html>
```
Here is an example of CSS:

```
h1 {
  color:red;
  font-size:24px;
}

p {
  color:blue;
  font-size: 12px;
}
```
What is the CSS doing here?

---
# Including CSS in HTML

There are several ways to add style to an HTML page


### Inline:
```js
<!DOCTYPE html>
<html>
  <head>
    <title>My Cat</title>
    <style type="text/css" media="screen">
      h1 {
        color:red;
        font-size:24px;
      }

      p {
        color:blue;
        font-size: 12px;
      }
    </style>
  </head>
  <body>
    <h1 style="color: red; font-size: 24px;">My Cat Bob</h1>
    <p style="color: blue; font-size: 12px;">My cat is named Bob. He is a lazy cat.</p>
  </body>
</html>
```

### Style Tags:
```js
<!DOCTYPE html>
<html>
  <head>
    <title>My Cat</title>
    <style type="text/css" media="screen">
      h1 {
        color:red;
        font-size:24px;
      }

      p {
        color:blue;
        font-size: 12px;
      }
    </style>
  </head>
  <body>
    <h1>My Cat Bob</h1>
    <p>My cat is named Bob. He is a lazy cat.</p>
  </body>
</html>
```

### Style Tags with @ import of a CSS file:
  * You can put all your CSS in one file
  * You can load one CSS file into another using @import

```js
<style type="text/css" media="screen">
  @import 'my_special_css_file.css';
</style>
```
[MDN Import Guide](https://developer.mozilla.org/en-US/docs/Web/CSS/%40import)

### Link to a CSS file:
```js
<!DOCTYPE html>
<html>
  <head>
    <title>My Cat</title>
    <link href="styles/style.css" rel="stylesheet" type="text/css">
  </head>
  <body>
    <h1>My Cat Bob</h1>
    <p>My cat is named Bob. He is a lazy cat.</p>
  </body>
</html>
```


