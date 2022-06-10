# Lecture 01 - React Components and Props

## Gotchas!
- `className`
- casing really, really matters! 
    - components get capitalized
    - component files get capitalized
    - the CSS files get capitalized
    - if you try to change this too late, git will not notice and deploys will break  
- importing images vs public directory
    - background images in CSS are weird and must always live in `src`
- inline styles
- `<>` fragments and "Adjacent JSX"
- Components and files must be uppercase
- Netlify deployment

## Components

Take a look at the code below. Make a quick drawing to predict what will be rendered when we make a react app out of this code.

```js
export default function App() {
    return (
        <div>
            <Header username='dr cool' />
            <Main />
            <Footer phone='(212) 555-4345' />
        </div>
    )
}

function Header({ username }) {
    return <h1>Welcome {username}</h1>
}

function Footer({ phone }) {
    return <p>Contact me at {phone}</p>
}

function Main() {
    return <section>This is my first react app</section>
}
```

## Render and append

```js
export default function DogList({ dogs }) {
  return (
    <div className='dog-list'>
      {
        dogs.map((dog) => <DogItem key={dog.name} {...dog} />)
      }
    </div>
  );
}
```
