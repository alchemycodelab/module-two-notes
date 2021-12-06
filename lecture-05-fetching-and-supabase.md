
# Lecture 5 - Fetching and Supabase

## Supabase dashboard

## fetch-utils.js

```js
const SUPABASE_URL = 'https://gxwgjhfyrlwiqakdeamc.supabase.co';
const SUPABASE_KEY = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJyb2xlIjoiYW5vbiIsImlhdCI6MTYzNjQxMTMxMiwiZXhwIjoxOTUxOTg3MzEyfQ.PHekiwfLxT73qQsLklp0QFEfNx9NlmkssJFDnlvNIcA';

const client = supabase.createClient(SUPABASE_URL, SUPABASE_KEY);
```

## Async/Await and Fetching in supabase

[Supabase Select Docs](https://supabase.com/docs/reference/javascript/select)

```js
// to get all dogs
const allDogs = await client
    .from('dogs')
    .select();

// to get a single dog
const dogNumberSeven = await client
    .from('dogs')
    .select()
    .match({ id: 7 })
    .single();
```

## The 'load' event

```js
window.addEventListener('load', async () => {
    const response = await fetchData();
});
```

## Query Params

Let's say you have a URL like this: `www.my-website.com/?id=5&name=dani`

Notice the weird question mark syntax at the end. This format is called a query string.

Think of a query string as kind of an object (key/value pairs) that lives in the URL.

In this case, the id is 5 and the name is 'dani'.

In your JavaScript, you can get the id and name from the query string like so:

```js
const params = new URLSearchParams(window.location.search);

const id =params.get('id');
const name = params.get('name');
```