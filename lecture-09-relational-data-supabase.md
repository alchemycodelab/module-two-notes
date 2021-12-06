# Lecture 9 - Relational Data in Supabase

## One-to-many relationships

## Foreign-keys in the supabase dashboard

Look for the little ⛓️ chain icon to add relationships between tables in supabase.
## Joins in supabase

- A join is a SQL term for using a foreign key to fetch data from two related tables. 
- Note that what I'm calling a 'join' here isn't exactly right, but just keep the word in mind for the future.

- Imagine we have a data model with two tables, `neighborhoods` that have many `shops`, and shops refer to their neighborhood by id, like so:

```js
const sellwood = {
    id: 42,
    name: 'Sellwood',
    location: 'SE Portland',
};

const cully = {
    id: 21,
    name: 'Cully',
    location: 'NE Portland',
};

// which neighborhood does this shop belong to?
const cloudCapGames = {
    id: 9,
    name: 'Cloud Cap Games',
    rating: 5,
    neighborhood_id: 42,
};

```

```js
const response = await client
    // go to the neighborhoods table
    .from('neighborhoods')
    // and show me all the neighborhoods' properties
    // INCLUDING all the items in the shops table that have this neighborhood as their neighborhood_id
    .select('*, shops (*)')
```

The above supabase call will return the following data, `join`ed from the `shops` and `neighborhoods` tables

```js
[
    {
        id: 21
        name: 'Cully',
        location: 'NE Portland',
        shops: [],
    },
    {
    id: 42
    name: 'Sellwood',
    location: 'SE Portland'
    shops: [
        {
            id: 9,
            name: 'Cloud Cap Games',
            rating: 5,
            neighborhood_id: 42,
        }
    ]
    },
]
```

- As usual, remember to use `.match({ user_id: client.auth.session().user.id })` for user-created entities, especially in the 'half-baked'assignments.

## Matching within sub-queries

Lets say you want to get all neighborhoods, with all their shops, but only dogs whose age is 5:

```js
export async function getFamilies() {
    const response = await client
        .from('neighborhoods')
        .select('*, fuzzy_bunnies (*)')
        .match({ 'shops.rating': 5 });

    return checkError(response);    
}
```