# Lecture 09 - Context

the idea behind context is to avoid prop drilling. If we put data in context, it's a pain to set up, but it will be available anywhere in the app without having to annoyingly pass it around as props.

Here, no matter where we call `useGameContext`, we'll always be accessing and changing the same globally-available state:

```js
export default function Game() {
  const {
      player1Score, setPlayer1Score,
      player2Score, setPlayer2Score,
   } = useGameContext()
   
   return <div>
        <p>Score: {player1Score} to {player2Score}</p>
        <button onClick={() => setPlayer1Score(player1Score + 1)}>Increment Player 1 score</button>
        <button onClick={() => setPlayer1Score(player1Score + 1)}>Increment Player 2 score</button>
   </div>
 }
```

Here's the downside: you gotta set it up with lots of boilerplate:

```js
// A provider is a component that "Provides" data to all of its children.
// That data will be avaialbe through the magic of context (useContext).
import {
  createContext,
  useContext,
  useState,
} from 'react';

// this thing has a property called 'Provider'. We will use it later.
// in fact, we will wrap our WHOLE APP in this GameContext.Provider.
// our whole app will be props.children to this Provider component
// that's why we needed to talk about children
const GameContext = createContext();

  
// here i am defining state that is useful to our whooole app.
// no matter whaere we are in our app, Context will let us grab this
// without the problems that come with prop drilling

// this is sort of our 'fetch-utils' for react state
// instead of import/export, we call the useGameContext function to get access
// to these helpers
export default function GameProvider({ children }) {
  const [player1Score, setPlayer1Score] = useState(0);
  const [player2Score, setPlayer2Score] = useState(0);

  resetGame() {
    setPlayer1Score(0);
    setPlayer2Score(0);
  }

  const gameStateAndSetters = {
    player1Score, setPlayer1Score,
    player2Score, setPlayer2Score,
  };

  return <GameContext.Provider value={gameStateAndSetters}>
    {children}
  </GameContext.Provider>; 
}

// this is the function we call in a component--no matter where in the hierarchy it is
// and we get free access to that state
// this is the getter
export function useGameContext() {
  return useContext(GameContext);
}
```
