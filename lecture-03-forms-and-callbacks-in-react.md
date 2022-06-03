# Lecture 03 - Forms and Callbacks in React

```js
import React from 'react';

export default function InstructionsForm({ handleSubmit, setInstructionInForm }) {
  return (
    <form onSubmit={handleSubmit}>
      <input onChange={e => setInstructionInForm(e.target.value)} />
      <button>Add instruction</button>
    </form>
  );
}
```

Looking at the above component, what do you think the data types of `handleSubmit` and `setInstructionInForm` are?

## Callbacks


## Immutability in react state

We must make our array changes immutable.

Immutability means: create a new array every time instead of just making changes to the same array over and over.

It feels a little like this:
https://www.youtube.com/watch?v=KUXKUcsvhQc

Here is how to immutably add an item to an array in React state:

```js
// this makes a copy of the old array, adding a new item at the end
const newArray = [...oldArray, newItem]

setArrayInState(newArray)
```

alternatively . . .

```js
// this makes a copy of the old array, adding a new item at the end
oldArray.push(newItem)

// this is enough to count as immutable. We make a new copy here and we lose the old array forever.
setArrayInState([...newArray])
```

## From Scratch Demo: Character Designer

## Half-Baked Project: City Builder
