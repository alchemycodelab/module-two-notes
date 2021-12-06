# Lecture 7 - Updating in Supabase

## Async/Await and updating in supabase 

[Supabase Select Docs](https://supabase.com/docs/reference/javascript/update)

```js
const response = await client
    .from('dogs')
    .update({ name: 'spot sr.' })
    .match({ user_id: client.auth.session().user.id });
```

Remember to always use `.match({ user_id: client.auth.session().user.id })`  for user-created entities, especially in the 'half-baked'assignments.