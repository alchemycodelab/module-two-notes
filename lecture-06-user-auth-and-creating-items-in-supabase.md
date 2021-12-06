# Lecture 6 - User Auth and Creating Items in Supabase

## Supabase template with auth

In addition to a functioning Sign In/Sign Up form, we include some basic, boilerplate auth functions in the template.

Lets talk about what each one does.


```js
// when a user tries to visit a page that calls this function, we automatically redirect the user back to the login page if they are not logged in
export async function checkAuth() {
    const user = await getUser();

    if (!user) location.replace('../'); 
}

// when a user tries to visit a page that calls this function, we automatically redirect the user away from the login page if they are already logged in
export async function redirectIfLoggedIn() {
    if (await getUser()) {
        location.replace('./some-other-page');
    }
}

// signs an new user in and puts an auth token in local storage in the browser
export async function signupUser(email, password){
    const response = await client.auth.signUp({ email, password });
    
    return checkError(response);
}

// signs an existing user in and puts an auth token in local storage in the browser
export async function signInUser(email, password){
    const response = await client.auth.signIn({ email, password });

    return checkError(response);
}

// removes the token from local storage and redirects the user home
export async function logout() {
    await client.auth.signOut();

    return window.location.href = '/';
}

// alerts the user if there is an error with their supabase call
function checkError({ data, error }) {
    return error ? console.error(error) : data;
}

```

## Getting the user_id for the logged in user

```js
const userId = client.auth.user().id, 
```

## Async/Await Creating items in supabase

[Supabase Select Docs](https://supabase.com/docs/reference/javascript/insert)

```js

const newDog = await client
    .from('dogs')
    .insert({ 
        name: 'spot', 
        user_id: client.auth.user().id, 
    })
    .single();

```