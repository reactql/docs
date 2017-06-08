# Adding custom reducers

---
A '[reducer](http://redux.js.org/docs/basics/Reducers.html)' is a function that modifies the state of your application, and returns a copy.

This is what enables Redux to know that something has changed, and ultimately feed those changes back to any listening React components.

The first thing we need to do is create a reducer.

Since we're building a simple to-do list, let's create a reducer that has two simple functions: Adding a to-do, and removing one. We'll create this at `store/reducer.js`, since we'll only have one reducer throughout our application (the name's not important; if we have more than one reducer, we might call it 'reducers/todo.js' or something similar.)

**store/reducers.js**
```js
// Custom reducers.  We'll create a simple to-do list handler.
export default function reducer(state = [], action) {
  // eslint-disable-next-line default-case
  switch (action.type) {
    case 'ADD_TODO':
      if (action.todo && !state.includes(action.todo)) {
        return [...state, action.todo];
      }
      break;
    case 'REMOVE_TODO':
      return state.filter(todo => action.todo !== todo);
  }
  return state;
}
```

What's happening here?

Redux will pass in our current 'state' object. If we're calling this for the first time, we won't have an object, so by default we create an empty `state` array.

`action` will contain whatever our action (which we've not yet built) passes to the reducer. We'll get to that in a moment, but for now let's assume it'll have an `action.type` string, which tells our reducer what to do with the `state`.

If `action.type === 'ADD_TODO'`, then we check to ensure that same to-do item doesn't already exist on our state. If not, we'll create a *new* array, passing in all of the old values, along with our new to-do.

> Note: Creating a new array and not simply mutating the old one is a [key concept](http://redux.js.org/docs/recipes/UsingObjectSpreadOperator.html) of Redux. This allows us to keep our state 'clean' and free of side-effects, by each new action always resulting in a new/fresh copy of the state. We can then guarantee our React components are never relying on stale data, and it also makes it trivial to implement 'undo' features that travel back to previous states.

If `action.type === 'REMOVE_TODO'`, we'll pass back a new array with the todo filtered out. Again, note that we're not just removing it from the current array -- we pass back a fresh copy, just with that value omitted.

Once we've built our reducer, we need to add it to our Redux instantiation code that both the server and browser will use to wire up Redux.

Edit [kit/lib/redux.js](https://github.com/reactql/kit/blob/master/kit/lib/redux.js) by importing your reducer and adding it to the `combineReducers()` object that you're passing:

**kit/lib/redux.js**
```js
// ...

// Import the new reducer we've just created
import todoReducer from 'store/reducer';

// ...

// Add it to the existing `combineReducers()` call, alongside Apollo
export default function createNewStore(apolloClient) {
  const store = createStore(
    combineReducers({
      apollo: apolloClient.reducer(),
      todos: todoReducer, // <--- this is where we've added our custom reducer!
    }),
    !SERVER ? window.__STATE__ : {}, // initial state
    compose(
        applyMiddleware(apolloClient.middleware()),
        (!SERVER && typeof window.__REDUX_DEVTOOLS_EXTENSION__ !== 'undefined') ? window.__REDUX_DEVTOOLS_EXTENSION__() : f => f,
    ),
  );

  return store;
}
```

Note that we've given the reducer object a `todos` root keyword. This means changes to the state will affect _only_ that 'part' of the state. Apollo has its own `apollo` root, to avoid clashing with other 'parts' of our application state.

That's it - we now have a custom reducer that's concerned with responding to our to-do actions.
