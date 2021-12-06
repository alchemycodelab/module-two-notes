
# Sample data models for 'from scratch' deliverables

## Beanie babies List/Detail App

### Beanie Baby 
- because this deliverable has no way to create a beanie baby, you will manually enter these in the supabase dashboard
```js
{
    id: 1,
    name: '',
    birthday: '',
    picture_url: '',
    description: '',
}
```

## Poll Maker App

### Poll
```js
{
    id: 1,
    question: '',
    option1: '',
    option2: '',
    votes1: 0,
    votes2: 0,
    user_id: '',
}
```

## Building Designer App

### Building
- note: one building is only ever created for a given user, to be updated by that user later.
```js
{
    id: 1,
    left: '',
    right: '',
    middle: '',
    slogans: [''],
    user_id: '',
}
```

## Shopping Checklist App

### Shopping Item
```js
{
    id: 1,
    item: '',
    quantity: 0,
    user_id: '',
}
```

## Workshop Planner App

### Workshops
- because this deliverable has no way to create a workshop, you will manually enter these in the supabase dashboard
```js
{
    id: 1,
    workshop_name: '',
}
```

### Participant 
```js
{
    id: 1,
    name: '',
    user_id: '',
    // this is a one-to-many foreign_key and must be created using the "chain link" feature in the supabase dashboard
    // as a rule, let's say that, due to scheduling conflicts, we're assuming that a participant can only enroll in a single workshop, but that a single workshop will, of course, have many students enrolled.
    workshop_id: 2,
}
```

## Movie Review App

### Movie
```js
{
    id: 1,
    name: '',
    poster_url: '',
    year: 1999,
    genre: ''
}
```

### Review
```js
{
    id: 1,
    author: '',
    rating: 2,
    thumbs: 'up', // or 'down' if the rating is negative
    review: '',
    // this is a one-to-many foreign_key and must be created using the "chain link" feature in the supabase dashboard
    // one review will always belong to a single movie, but one movie may have multiple reviews
    movie_id: 2,
    user_id: '',
}

```
