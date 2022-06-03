# Lecture 04 - State and Arrays in React

## From Scratch Demo: Goblin Builder

## Half-Baked Project: Movie List Maker

## Gotcha

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
