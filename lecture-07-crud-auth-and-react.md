# Lecture 07 - Auth and Protected Routes in React

## Double token weirdness
- We need to hold onto the token in state, even though it's right there in localstorage
- Otherwise we lost the token occasionally while developing

## Protecting routes in React
     ```js   <Switch>
          {/* once the switch finds a correct answer, it's done */}
          <Route exact path="/">
            {/* pass down the debit card so that the child can change parent state */}
            {
              // this protecting of routes and holding on to the user data in state --- that's new!!
              currentUser 
                ? <Redirect to="list"/>
                : <HomePage setCurrentUser={setCurrentUser} />
            }
          </Route>
          <Route exact path="/list">
            {
              !currentUser 
                ? <Redirect to="/"/>
                : <ListPage />
            }
          </Route>
          <Route exact path="/create">
            {
              !currentUser 
                ? <Redirect to="/"/>
                : <CreatePage />
            }
          </Route>
          <Route exact path="/edit/:id">
            {
              !currentUser 
                ? <Redirect to="/"/>
                : <UpdatePage />
            }
          </Route>
        </Switch>
```js
