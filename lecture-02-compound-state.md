# Lecture 2 - Compound State


## Dropdowns

```html
<select id="my-select">
    <option value="dog-value">Dog Is What The User Sees</option>
    <option value="cat-value">Cat Is What The User Sees</option>
    <option value="pigeon-value">Pigeon Is What The User Sees</option>
</select>
```

```js
const selectEl = document.querySelector('#my-select');

selectEl.addEventListener('change', () => {
    console.log(selectEl.value) // cat-value, dog-value, or pigeon-value
})
```

## Scope

Child scope can use parent scope.

Parent scope __cannot__ use child scope.

Think of it like Halloween candy: the child went and earned it, and is unlikely to want to share it with the parent.

```js
const parentThing = 7;

addButton.addEventListener('click', () => {
    const childThing = 2;

    console.log('A child says: ', parentThing);
    console.log('B child says: ', childThing);
});

// things defined inside a function are not accessible outside the function
console.log('C parent says: ', parentThing);
console.log('D parent says: ', childThing);
```

## Arrays as state

```js
let fruits = ['apple', 'orange'];

myButton.addEventListener('click', () => {
    console.log(selectEl.value) // cat-value, dog-value, or pigeon-value

    // here we mutate the array state
    fruits.push('kiwi')

    // note that, as usual, whenever we update state, we want to update the DOM
    updateListDOM()
})
```


## Creating DOM elements

- Obviously, it would be impossible for all website HTML to be hard coded.

- Here is how you can create new HTML elements (and add them to the DOM) on the fly.

```js
// go grab a hard-coded div from the website
const container = document.querySelector('#container');

// make and mutate a new div
const div = document.createElement('div');
div.textContent = 'This is my new, dynamically generated div!';

// append the div to the container in order to get it to show up in the website
container.append(div);
```

## Rendering lists of things

```js
const container = document.querySelector('#container');

for (let fruit of fruits) {
    container.append(fruit);
}
```

- In situations where you expect to _add items to your list of things_, the easiest solution is to clear out the DOM every time you want to add a new item to the list. 

- If you don't clear out the old DOM, it's easy to accidentally duplicate the whole list.

- There's suddenly a lot going on! 
    - So it might be a good idea to put all this work into a function. 
    - This function can be called whenever we want to refresh our list with the newest state.

```js
// notice that this array is state. It is in 'global' scope.
let fruits = [];

function refreshList() {
    const container = document.querySelector('#container');

    // clear out the old DOM to make room for the new
    container.textContent = ''

    for (let fruit of fruits) {
        // the function has access to global state, even if we don't pass it as an argument
        container.append(fruit);
    }
}
```

- One of these functions is pure and the other is impure. Which is which? What's the difference?

## Where should functions live?

- Impure functions that manipulate existing DOM elements _must_ live in the main .js file. Otherwise, you will cause problems in your test suite down the road.

- Pure functions that _create and return new DOM elements_ should probably live in a separate file and imported in.

```js
import { add } from './utils.js'

add(4, 2)
```

```js
export function add(num1, num1) {
    return num1 + num2
}
```