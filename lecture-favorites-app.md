## Lecture 10 - Favorites App

https://github.com/alchemycodelab/favorite-movies-feb2022

### Let's put it all together
Our favorites app will hit a movie API, let a user search for movies, and let them save favorite movies in a list. That lets us bundle our main react skills:
- Auth
- Supabase
- Third party API with netlify function
- List/Detail

### Gotchas
- On the search page, we want to render items differently if they are already on the favorites list for this user. 
- That means we need to know the user's favorites every time we render a list item, even when it doesn't look like we need it.
- Where is the best place to store the user's favorites? We kind of need them all over the app, and passing it as props is annoying, while making multiple fetches seems wasteful.
- This is probably a question for another day, but the answer is `context`.
