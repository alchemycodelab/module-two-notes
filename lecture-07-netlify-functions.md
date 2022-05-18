# Lecture 07 - Netlify Functions and Third-Party APIs


<img width="1290" alt="image" src="https://user-images.githubusercontent.com/16160135/169093080-eac3ecbd-7de9-4a7e-8343-c4f4007557fd.png">

<img width="1290" alt="image" src="https://user-images.githubusercontent.com/16160135/169092943-0a0def87-b842-4211-97c9-d1bb310a70fc.png">

## Hitting our netlify function from the front end

```js

export async function getData(searchFilter) {
  // we now hit OUR OWN ENDPOINT
  const rawResponse = await fetch(`/.netlify/functions/my-function?searchFilter=${searchFilter}`);
  const data = await rawResponse.json();

  return data;
}
```

## Hitting an API from our netlify function
```js
const fetch = require('node-fetch');
require('dotenv').config();

exports.handler = async (event, context) => {
  try {
    // put your keys in .env to hide them from malicious users and github robots.
    // note: in your netlify function, your .env variables do not need to be prepended with REACT_APP
    console.log(process.env.MY_KEY)
    
    // here is how we get query parameters (i.e., `?searchFilter=charmander`) inside our netlify function
    console.log(event.queryStringParameters.searchFilter)
    
    const response = await fetch(`www.my-api.com/v2/characters`);
    const data = await response.json();
    const json = JSON.stringify({ data });
    
    return { 
      statusCode: 200, 
      body: json
    };
  } catch (error) {
    console.log(error);
    return {
      statusCode: 500,
      body: JSON.stringify({ error: 'Failed fetching data' }),
    };
  }
};

```

## Gotchas
- `npm run dev` is how we serve up react with our netlify functions.
- If you're not on `node` version 14, 16, or 18 (the long-term suppport versions are always even numbers) something might break.
- You might need CORS headers to prevent chrome from stopping the response from your netlify function.
- Examine your API response (then your netlify function response) in the console. Where does the array live at each step?
- In your netlify function, you can access query parameters from the request by using `event.queryStringParameters.myKey`
- If you name it correctly, by default your netlify function will live at `http://localhost:8888/.netlify/functions/pokemon?name=char`. Note that this string will not work on the deployment since the URL will not be `localhost` there. You can make the call like so below to default to the correct deployment domain name:

```js
  const rawResponse = await fetch(`/.netlify/functions/movies?searchFilter=${searchFilter}`);
```
