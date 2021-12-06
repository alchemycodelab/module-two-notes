# Lecture 8 - Arrays and Complex Updating in Supabase

## Async/Await and Updating

[Supabase Delete Docs](https://supabase.com/docs/reference/javascript/update)

```js
// delete a single dog with an id of 10
await client
    .from('dogs')
    .delete()
    .match({ 
        id: 10,
        user_id: client.auth.session().user.id
     })
    .single();
```


Remember to always use `.match({ user_id: client.auth.session().user.id })`  for user-created entities, especially in the 'half-baked'assignments.