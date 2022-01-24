# Lecture 01 - React Components and Props

## Gotchas!
- `className`
- importing images vs public directory
    - background images in CSS are weird and must always live in `src`
- inline styles
- `<>` fragments and "Adjacent JSX"

## Components

Take a look at the code below. Make a quick drawing predict what will be rendered when we make a react app out of this code.

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

function Header(props) {
    return <h1>Welcome {props.username}</h1>
}

function Footer(props) {
    return <p>Contact me at {props.phone}</p>
}

function Main() {
    return <section>This is my first react app</section>
}
```
