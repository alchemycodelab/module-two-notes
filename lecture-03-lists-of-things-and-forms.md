
# Lecture 3 - Lists of Things and Forms

## Pure Functions that return DOM elements

- Consider this HTML.
    - What's annoying about it? 
    - Would you enjoy writing HTML that looked like this?

```html
<div class="dog">
    <p>Fido</p>
    <img src="www.puppy.com/32.png" />
</div>
<div class="dog">
    <p>Codi</p>
    <img src="www.puppy.com/11.png" />
</div>
<div class="dog">
    <p>Spunky</p>
    <img src="www.puppy.com/25.png" />
</div>
```

- Notice that we're writing the same div several times with small differences.

- For a number of reasons, you should avoid writing the same HTML over and over again. 
- When you're in a situation like this, it's nice to write a function that can write our HTML for us!

```js
export function renderDog(dog) {
    const div = document.createElement('div');
    const img = document.createElement('img');
    const p = document.createElement('p');

    div.classList.add('dog');

    p.textContent = dog.name;
    img.src = dog.url;
    
    div.append(p, img);

    return div;
}
```

- `renderDog()` returns some an HTML element that looks like this:

```html
<div class="dog">
    <p>Fido</p>
    <img src="www.puppy.com/32.png" />
</div>
```

- We can call and use this function like so:

```js
// grab a hard coded DOM element from the HTML
const container = document.querySelector('#container);

// make a dog object
const dog = {
    name: 'Fido',
    url: 'www.puppy.com/32.png',
};

// feed the dog object to the renderDog function.
// This function returns a DOM node
const dogEl = renderDog(dog);

// append this DOM node to the hard-coded DOM we grabbed upstairs.
container.append(dogEl);
```

## Forms

- Sometimes we want more than just one `input` worth of information at a time. 
- That's when an HTML form is useful. 
- It also gives us that snappy 'hit enter to submit' behavior.
- The downside is that forms require us to remember 2 things:
    1) `e.preventDefault()`
    1) `const formData = new FormData(form);`

```html
<form id="dog-form">
    <input name="dog-name" />
    <input name="age" type="number" >
    <button>Submit</button>
</form>
```

```js
const dogFormEl = document.querySelector('#dog-form);

dogFormEl.addEventListener('submit', (e) => {
    // this is a line that we need in order to prevent 1996 behavior from forms
    // notice the e is defined next to the word submit a few lines up. Don't worry about it for now :)
    e.preventDefault();

    // we need to do this weird "memorize-it" thing to get user input.
    const formData = new FormData(dogFormEl);

    // here's how we conveniently get information from the form, now that we've done that weirdness
    // it's annoying if you have one or two fields, but you can imagine how this might be nice if you had dozens of fields
    const name = formData.get('dog-name');
    const age = formData.get('age);
    // notice that the .get() function takes in whatever the `name` property is in the HTML
})

```