# Adding actions

---
Now, we need to create a couple of simple '[actions](http://redux.js.org/docs/basics/Actions.html)' that will 'notify' our reducer when something needs changing.

Create a file called `src/store/actions.js` with this:

**src/store/actions.js**
```js
export function addToDo(todo) {
  return {
    type: 'ADD_TODO',
    todo,
  };
}
export function removeToDo(todo) {
  return {
    type: 'REMOVE_TODO',
    todo,
  };
}
```

Actions are super simple. They basically just return an object with a `type` key (that tells Redux what type of action this is) and then whatever other data we need to carry along with the request.

Remember the `switch()` statement in our [reducer](reducers.md) that looks at `action.type` to respond to `ADD_TODO` and `REMOVE_TODO`? The return statement of our action gets fed into the second parameter of our reducer, which is how we know what kind of action was sent.

We'll use these actions in the next step, inside our components.
