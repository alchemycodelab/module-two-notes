## The Pattern of Patterns

All patterns revolve around these 4 fundamental activities:

|  | Get | Set |
|-----------|----|-------|
| **State** | 1) get State | 2) set State |
| **DOM**| 3) get DOM  |  4) set DOM |

# The 10 Patterns

1) [Wiggle](#1-wiggle)
1) [Event Handler](#2-event-handler)
1) [Render function](#3-render-function)
1) [Display Function](#4-display-function)
1) [Display a list](#5-display-a-list)
1) [Update a list](#6-update-a-list)
1) [Async fetch on 'load'](#7-async-fetch-on-load)
1) [Async update a list on click](#8-async-update-a-list-on-click)
1) [List / Detail](#9-list--detail)
1) [List of clickables](#10-list-of-clickables)

## 1) Wiggle 

The main .js file for each of your pages should follow this basic format:

- W: We always just
- I: `import`
- G: Grab DOM elements
- G: with `getElementById()`
- L: `let` state
- E: and describe our events

## 2) Event handler 
    1) add click listener to a dom element
    2) optional: get form info
    3) change state
    4) update dom

```js
button.addEventListener('click', () => {
    const name = nameInput.value;

    timesClicked++;

    charactereName.textContent = name
    countDiv.textContent = timesClicked;
});
```


## 3) Render function 
    - A pure function that takes in an object and returns an HTML element _without appending it to any external DOM_
    - Should always live in a separate file, to be imported then called.

```js
export function renderCat(cat) {
    const catEl = document.createElement('div');
    const nameEl = document.createElement('nameEl');
    const img = document.createElement('img');
    nameEl.textContent = cat.name;
    img.src = cat.image_url;

    catEl.classList.add('cat-box');
    
    catEl.append(nameEl, img);

    return catEl;
}
```

## 4) Display function 
    - An impure function that appends to or mutates existing DOM
    - Often uses global state
    - Often loops or calls render functions. 
    - This function may or may not take an argument.
    - Must always live in the same file as the DOM elements it grabs and the state it references.
        - Usually not to be imported.

```js
function displayStats() {
    reportEl.textContent = `You have changed the head ${headCount} times, the 
        body ${middleCount} times, and the pants ${bottomCount} times. And 
        nobody can forget your character's classic catchphrases:`;
}

```

<!-- ### Examples include: 
- character creator displayStats -->

## 5) Display a list
    1) loop through array
    2) for each item render an html element
    3) append each element to the dom

```js
    pastGamesEl.textContent = '';
    
    for (let game of pastGames) {
        const gameEl = renderGame(game);

        gameEl.classList.add('past');
        
        pastGamesEl.append(gameEl);
    }
```

## 6) Update a list
    1) add (or remove) item to state array
    2) clear dom list
    3) loop through updated list
    4) render and append updated list items to cleared dom

```js
finishGameButton.addEventListener('click', () => {
    const fruit = fruitInput.value;

    fruitsArray.push(fruit);

    displayFruits();
});
```

## 7) Async fetch on 'load'
    1) add async 'load' listener to the window
    2)  await function to fetch data from supabase
    3) render and append fetched data to dom

```js
window.addEventListener('load', async() => {
    // fetch all dogs
    const veggies = await getVeggies();

    for (let veggie of veggies) {
        const veggieEl = renderVeggie(veggie);
      // render the dog detail
        veggieListContainer.append(veggieEl);
    }
});
```

## 8) Async update a list on click
    1) add async 'click' listener
    2) await function to manipulate data in supabase
    3) refetch updated data
    4) render and append updated data to dom

```js
button.addEventListener('click', async e => {
    const name = nameInput.value;

    await createLizard(name);

    lizards = await updatedLizards();

    // uses global lizard state to clear and update lizard DOM
    displayLizards();
});
```

## 9) List / Detail 
    - list pages display a list where each item contains a link to a detail page about that particular item
    - detail pages shows that item's id in the url. Detail page shows info about just that item


```js
// get the id from URL: www.cool-cats.com/detail/?id=4
const params = new URLSearchParams(window.location.search);
const id = params.get('id');

// use the id to fetch the dog
const cat = await getCat(id);

// render the cat detail
const catDetailEl = renderCatDetail(cat);
catDetailContainer.append(catDetailEl);
```

## 10) List of clickables 
    - display a list, plus add an event listener to each rendered element inside the loop. 
    - Arguably, list/detail is a subset of this pattern with a link instead of an event listener

```js
for (let todo of todos) {
    const todoEl = renderTodo(todo);

    todoEl.addEventListener('click', async () => {
        await completeTodo(todo.id);

        displayTodos();
    });

    todosEl.append(todoEl);
}
```
