# Lecture 07 - Netlify Functions and Third-Party API

## Gotchas
- `npm run dev` is how we serve up react with our netlify functions.
- You need CORS headers to prevent chrome from stopping the response from your netlify function.
- Examine your API response (then your netlify function response) in the console. Where does the array live at each step?
- In your netlify function, you can access query parameters from the request by using `event.queryStringParameters.myKey`
- If you name it correctly, by default your netlify function will live at `http://localhost:8888/.netlify/functions/pokemon?name=char`. Note that this string will not work on the deployment since the URL will not be `localhost` there. You can make the call like so below to default to the correct deployment domain name:

```js
  const rawResponse = await fetch(`/.netlify/functions/movies?searchFilter=${searchFilter}`);
```
