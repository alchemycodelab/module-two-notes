# Lecture 04 - State and Arrays in React

## From Scratch Demo: Goblin Builder

## Half-Baked Project: Movie List Maker

Note that to filter movies correctly, we'll need to keep track of two arrays: the filtered movies, and all movies
- If we don't keep track of two arrays, we will lose all of our movies once they filter away.
- So our state will look something like this:

```js
  const [currentFilter, setFilter] = useState(''); 
  const [movies, setMovies] = useState([]); 
  const [filteredMovies, setFilteredMovies] = useState([]); 
```

## Array methods
We'll need to filter items on changes, and delete items on click. 
- Let's talk about filtering and deleting items from arrays.

```js
function filterMovies() {
    const filteredMovies = movies.
      filter(movie => 
        movie.title.includes(currentFilter));
        // || movie.director.includes(query) 
        // || movie.year < query 
        // || movie.color === query);
  // then inject that into state
  // filter is immutable so we don't need to spread
    setFilteredMovies(filteredMovies);
}
```

```js
  function deleteMovie(title) {
    // use this id to find the index of the movie in state
    const index = movies.findIndex(movie => movie.title === title);

    // use this index to splice out that movie in state
    movies.splice(index, 1); // delete this many at that index

    // update state with this updated array (use spread for immutability)
    setMovies([...movies]);
  }
```

## useEffect Gotcha
Try though I might, I cannot avoid showing you the weirdest bit of react: the `useEffect` dependenct array. Without it, we have a breaking bug:

### The bug
- The problem: when I delete a movie from a filtered list, it does not delete from the view. That's because we render filtered movies, but we delete from all movies
- The solution: set it up so that whenever a movie is deleted, we filter again.
- That means we need to filter our movies whenever the state of movies changes. After all, if you delete a movie, that only deletes it from the movies, not the filtered array, which can cause problems when you try to delete something while the filter is active. We can achieve this using a useEffect
- So without useEffect, there is no good way to solve this bug. but you can still get full credit without solving the bug

### useEffect: listen for changes

In addition to being a good place to put 'on load' fetches, you can think of `useEffect` as a kind of event listener. However, instead of listening for user events, it listens for changes in state.


```js
useEffect(() => {
    console.log('one of three things has happened: the component has loaded, the animals have changed, or the userId has changed`)
}, [animals, userId])
```

The weirdest thing: in `useEffect`, we often end up changing state in response to other state changes.

Our app can start to feel like a rube goldberg device

<img width="467" alt="image" src="https://user-images.githubusercontent.com/16160135/171966981-f8ad1d4f-d87e-4c3d-b914-ac4dbcf02fd3.png">
