# Lecture 10 - Complex Relational Data

## Filters in supabase

Look at all the cool things you can do in addition to just querying with `match()`:

I'm not going to go through all these, but looks through the docs and you may find some of them useful during project week. For example `select().from('dogs').gt({ age: 10})` will return all dogs over the age of 10. 

[Supabase Filter Docs](https://supabase.com/docs/reference/javascript/using-filters)

```js
select().from('dogs').or()
select().from('dogs').not()
select().from('dogs').match()
select().from('dogs').eq()
select().from('dogs').neq()
select().from('dogs').gt()
select().from('dogs').gte()
select().from('dogs').lt()
select().from('dogs').lte()
select().from('dogs').like()
select().from('dogs').ilike()
select().from('dogs').is()
select().from('dogs').in()
select().from('dogs').contains()
select().from('dogs').containedBy()
select().from('dogs').rangeLt()
select().from('dogs').rangeGt()
select().from('dogs').rangeGte()
select().from('dogs').rangeLte()
select().from('dogs').rangeAdjacent()
select().from('dogs').overlaps()
select().from('dogs').textSearch()
select().from('dogs').filter()
```
