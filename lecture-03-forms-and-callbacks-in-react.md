# Lecture 03 - Forms and Callbacks in React

## Form State

- on every keystroke, the state of the form changes
- we must store this state ourselves in react, otherwise we lose the react magic

## Callbacks

- When parents talk to children, we use props.
- When children talk to parents, we use callbacks.
- Think of a callback like a debit card. If we want to change the state of a bank account, only the parent can do that.
- However, if a parent gives a child a debit card, that debit card can be used to change the state of the parent's bank account.

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

## From Scratch Demo: Fast Food order tool

## Half-Baked Project: Tourism Postcard Builder
