# Tuesday 7/13/2021
Tonight we reviewed a special group of functions called *iteration methods* that allow us to apply some function to every single element of the array.

## Reading & Homework
Tab a stab at reading [Chapter 5 of Eloquent Javascript](https://eloquentjavascript.net/05_higher_order.html) on higher order functions.

## Labs

* **Write Your Own *.forEach()***

    Try writing your own function that accepts an array as its argument, then iterates over the array and does something to each element in the array that it's been passed.

* **Find Another Berry**

    Refactor the *Find A Berry* lab to return the second

    <details>
    <summary>Solution to Find a Berry Lab</summary>
    <div>

    ```js
    let fruits = ['Apple', 'Blueberry', 'Cherry', 'Date', 'Elderberry'];

    function endBerry(word) {
     return word.endsWith("berry")
    }
 
    fruits.find(endBerry)
    ```

    </div>
    </details>
* [**Titilize with Map**](https://github.com/BurlingtonCodeAcademy/jsah-june-2021-notes/blob/main/week-6/session-11/labs/titileize.md)


## Practice

Check out additional [array](https://github.com/BurlingtonCodeAcademy/jsah-june-2021-notes/blob/main/resources-0/arrays.md) resources and practice.