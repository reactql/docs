# Wiring up to React

---
### Adding React components that 'listen' to or 'trigger' state changes

Finally, we just need to set-up our React components that either 'listen' to store state, or trigger actions necessary to change it.

Editing [src/app.js](https://github.com/reactql/kit/blob/master/src/app.js), we'll write some components that do just that.

**src/app.js**
```jsx
// ----------------------
// IMPORTS
// ...

// @connect decorator to inject store state and dispatching
import { connect } from 'react-redux';

// Actions to add/remove to-do
import { addToDo, removeToDo } from 'store/actions';

// To-do components.  This will demonstrate Redux at work.

// Add a new to-do
@connect() class AddToDo extends React.PureComponent {
  setRef = ref => { this.ref = ref; }
  addToDo = () => {
    this.props.dispatch(addToDo(this.ref.value));
    this.ref.value = '';
  };
  render() {
    return (
      <div>
        <input ref={this.setRef} type="text" />
        <button onClick={this.addToDo}>Add to-do</button>
      </div>
    );
  }
}

// List the to-dos
@connect(state => ({ todos: state.todos }))
class ListToDos extends React.PureComponent {
  static propTypes = {
    todos: PropTypes.arrayOf(
      PropTypes.string,
    ),
  }

  // Return a thunk that dispatches the `removeToDo`
  removeToDo = todo => () => {
    this.props.dispatch(
      removeToDo(todo),
    );
  }

  render() {
    const { todos } = this.props;
    let inner;
    if (!todos.length) {
      inner = (
        <h4>No to-dos yet. Add one.</h4>
      );
    } else {
      inner = (
        <ul>
          {todos.map(todo => (
            <li key={todo}>
              {todo}
              <button onClick={this.removeToDo(todo)}>Remove</button>
            </li>
          ))}
        </ul>
      );
    }
    return (
      <div className={css.todos}>
        {inner}
      </div>
    );
  }
}

// Wire up the above components into a single `<ToDoHandler>`
const ToDoHandler = () => (
  <div>
    <AddToDo />
    <ListToDos />
  </div>
);
```

There's a lot happening here, so let's break it down.

First, we import a function called `connect()` from the [react-redux](https://github.com/reactjs/react-redux) library. This provides our functions with a 'higher-order component' that injects in state/action dispatching via props.

We then import our custom add/remove to-do actions.

In our `<AddToDo>` component, we use the `connect` function as a decorator. This function automatically passes a `dispatch()` function to our props. It's this function that allows us to tell Redux that an action has been triggered.

We wire up a simple form. The input registers itself on `this.ref`, which allows us to easily grab the value in the text box. The button fires off the dispatch event, with the text box value. The call to `addToDo()` returns a full object that then looks like this:

```js
{
  type: 'ADD_TODO',
  todo: 'Whatever you entered in the input box'
}
```

This gets fed down to our reducer, which returns back the 'new' state which now looks like this:

```js
[
  'Whatever you entered in the input box'
]
```

If you enter something new into the input box and hit the button again, the state would now be:

```js
[
  'Whatever you entered in the input box',
  'Something new that you entered'
]
```

So, now we have our means to *add* to our state.

We then create the component that *listens* to the state -- our `<ListToDos>`.

Here, we use the same `@connect` decorator, but this time we pass in a function that tells `connect` which parts of our application state we want to listen to.

Since we have access to the FULL state object (including the `apollo` root key!), and we only care about the `todos` key, we'll return an object with just that part.

Inside our component, we now have access to the `todos` via `this.props.todos`. Our component is then just basic Javascript - we check that `this.props.todos` isn't an empty array (if it is, we encourage the user to add a to-do) and display them as a `<li>` list.

Finally, we wire up another action - this time the `removeToDo` - to change the state of the application once again.

> Note: Updating React components is done declaratively. We don't 'tell' React to update - the `connect` HOC automatically updates the `props` that are fed in to the component and thus React implicitly re-renders when the state data changes.
