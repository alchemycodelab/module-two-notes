

# Lecture 4 - Games as State

- This is kind of a 'put it all together' Lecture. 
- You don't have much new to learn today. 
- However, the assignment itself is complex because you have a lot of state you need to manage.

Some advice for complex assignments:
1) Remember to make a plan. You might have squeaked by with no plan so far, but it's more likely to catch up with you here if you try to 'just figure it out at you go'.
1) Think carefully about you HTML elements and their relationship to events.
    - Make a list: for each event in your app, ask what HTML element will the event be attached to?
1) Think carefully about your events and their relationship to state.
    - Make a list: for each event in your app, what state will change and how will it change?
1) Think carefully about the relationship between HTML elements and the state.
    - Make a list: for each item in state, what HTML elements will I need to generate to represent this state?
    - Make a list: when does state change? Every item on this list counts as a time when you need to update the DOM (otherwise the user won't know that state changed)