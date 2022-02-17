# Lecture 10 - Testing

## Testing a click handler:

```js
import { addToWatchList } from './services/fetch-utils';

export default function Movie({ 
  movie,
  isOnWatchList, 
  refreshWatchlist,
}) {
  // const [count, setCount] = useState(0);
  const haveWatched = isOnWatchList(movie.id);
  async function handleClick() {
    if (!haveWatched) {
      const watchlistItem = {
        title: movie.title,
        api_id: movie.id,
        description: movie.overview,
        poster: movie.poster_path,
      };
      
      await addToWatchList(watchlistItem);
      await refreshWatchlist();
    }
  }


  return (
    <div 
      title="movie-item" 
      onClick={handleClick}
      <h3>{movie.title}</h3>
      <img src={`https://image.tmdb.org/t/p/original${movie.poster_path}`} />
    </div>
  );
}
```

```js
// import the function so we can examine it in a test
import { addToWatchList } from './services/fetch-utils';

// also PSYCHE--let's replace everything in that file with a mock that we can spy on
jest.mock('./services/fetch-utils.js');

test('calls the right functions', async () => {
  // make a mock we can spy on.
  const mockRefresh = jest.fn();

  render(<Movie
    movie={{
      id: 8,
      title: 'Jaws',
      poster_path: '1234.jpg',
      overview: 'A friendly fish finds a friend',
    }}
    isOnWatchList={() => false}
    refreshWatchlist={mockRefresh}
  />);

  const movieItemEl = await screen.findByTitle('movie-item');
  expect(movieItemEl).toBeInTheDocument();

  fireEvent.click(movieItemEl);

  // on click, nothing in the DOM is going to change
  // what IS going to happen is that functions are going to get called
  // what functions will get called on click?
  // refreshWatchlist, addToWatchList will get called
  // we need to check whether they have been called
  // i dont care about WHAT the refresh function does
  // all i care about is WHETHER IT WAS CALLED
  // in testing terms, this is called a 'spy'
  // we need to spy on a function and see how many times it was called
  // we can only spy on something called a mock
  await waitFor(() => {
    expect(mockRefresh).toHaveBeenCalled();
    expect(addToWatchList).toHaveBeenCalledWith({   
      api_id: 8,
      description: 'A friendly fish finds a friend',
      poster: '1234.jpg',
      title: 'Jaws' 
    });
  });
  ```
What if all that happened is that a function was called? With no changes to DOM?
You must mock the function and check that it was called.
```js
    fireEvent.click(thingToClick);`
    expect(myMockFunction).toHaveBeenCalled();
```

Ask? Was that function async?
- if so, you must `await waitFor(() => expect(thatFunction).toHaveBeenCalled())`
  
### Okay, well how do I mock a function?

Ask: was that function a prop?
	- if so, you must make a mock and pass it as a prop
  - `const mockFunction = jest.fn();`
  - `render(<MyComponent myCallback={mockFunction} />)`;

Ask: was that function imported from another file?
	- if so, you must mock that file
  - `import { addToWatchList } from './services/fetch-utils';`
  - then
  - `jest.mock('./services/fetch-utils.js');`

