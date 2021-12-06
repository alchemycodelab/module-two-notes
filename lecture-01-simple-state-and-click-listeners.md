# Lecture 1 - Simple State and Event Listeners

## Wiggle

- W: We always just
- I: `import`
- G: Grab DOM elements
- G: with `getElementById()`
- L: `let` state
- E: and describe our events

## 'Grabbing' elements with document.querySelector() 

```js
// these two statements are exactly the same
const myDiv = document.getElementById('my-div');
const myDiv = document.querySelector('#my-div');
```

- `document.querySelector()` can eat anything that css can eat.
- If you want to grab an item by class, use `.my-class`, for example. 
- But be careful: if you have more than one element with the class `.dog-box`, it will only return the first match it finds. 
- It's usually good to stick with `#ids` for this kind of thing until you feel very comfortable with DOM manipulation.

## Functions for Reused Code

- There are two kinds of functions: pure and impure.

### Pure Functions

```js
// pure functions are super predictable
// if you pass the same input twice, you will get the same output twice
// all pure functions have return statements
function add(num1, num2) {
    return num1 + num2
}

// because this function has a return statement, we can store (in a variable) whatever result it 'spits out'.
const sum = add(5, 6);
```

### Impure Functions

```js
// notice that this variable is defined _outside the function declaration_
const coolDivFromHTML = document.querySelector('#my-divs')

function mutateCoolDiv(words) {
    // 💥 impure function alert 💥
    // this function mutates something defined _outside the function declaration_
    coolDivFromHTML.textContent = words;

    // 💥 impure function alert 💥
    // no return statement!
}
```


```js
function getRandomNumberBetween0And10(/*💥 impure function alert 💥 no arguments! */) {
    // 💥 impure function alert 💥
    // randomness! no way to predict this
    return Math.random() * 10
}
```

- **Consider**
    - What do you think is easier to test: pure or impure functions? Why?

## Random numbers

```js
// get a random number between 1 and 10
const randomNumber = Math.floor(Math.random() * 10);

// you could use this random number as an array index. Why would we want to do that?
myArray[randomNumber] 
```


## State and View

- State is the whole point of apps.

- State is anything that changes over time.

- Every time state changes, update the DOM to show the user what the new state is.

- In plain JS, state is usually stored in `let` variables. 
    - Why do you think that is?

```js
let counter = 0;

counter++
```

## Click handlers

```js
const button = document.querySelector('#my-button');

button.addEventListener('click', () => {
    // 😎 Cool Zone 😎
    // when you click the #my-button button, whatever code you write in the cool zone will execute 

    // (the cool zone is actually called an 'anonymous callback' or maybe a 'click handler')

    // don't worry--it's not a free for all!
    // usually, we do exactly 3 things here:

        // 1) get some information, somehow :)
        const value = someInput.value;

        // then
        // 2) use that information to update state
        greetingState = `Hello ${value}!`;

        // finally
        // 3) update the DOM to reflect these state changes
        greetingEl.textContent = greetingState;
})
```

## Making a plan

- If you haven't gotten yourself into a mess yet, you won't believe me, but: planning is more important than coding.

- Without a plan, it is all too easy to "try to do everything at once"
    - Unlike writing in human languages, in coding language, it's always a bad idea to "make a sloppy copy" or "rough draft".

- The Golden Rule:  🦸 🦸‍♂️ `Stop starting and start finishing.` 🏁

- If you work on more than one feature at a time, you are guaranteed to multiply your bugs and your anxiety.

- When you've made a big enough mess, don't be surprised if me or a TA advises you to trash the repo and start over. 
    - We're not trying to be mean: we've all thrown out dozens of apps we've sunk hours into! 
    - It's sometimes just literally easier to start a project over than miserably debug a project where 'nothing works'.

---

### Here's a follow-the-steps process for how to avoid big messes:

1) Make a drawing of your app. Simple "wireframes"
1) Once you have a drawing, name the HTML elements you'll need to realize your vision
1) For each HTML element ask: Why do I need this? 
1) Once we know _why_ we need each element, think about how to implement the "Why" as a "How"
    - for example, if we know we need to inject words into a div, note `div.textContent = 'my new words'`
1) Find all the 'events' (user clicks, form submit, on load etc) in your app. Ask one by one, "What happens when" for each of these events. 
    - Does any state change? 
    - Does any DOM change? (if state changes, the answer is yes 🙂)
1) Think about how to validate each of your steps according to a Definition of Done
    - 90% of the time, it's just "`console.log` something" to make sure it's right.
1) Consider what features _depend_ on what other features. Use this dependency logic to figure out what order to complete tasks.
