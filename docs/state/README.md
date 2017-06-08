# Managing state

Out-the-box, [Apollo](http://dev.apollodata.com/react/) - the GraphQL client that ReactQL includes - uses [Redux](http://redux.js.org/) to manage its own internal query state.

You don't need to do anything for this. Apollo takes care of itself.

But what about other parts of your application? What if you want to store some kind of variables 'globally' across your app, and allow one or more React components to 'listen' to - or effect - the state?

That's where [Redux](http://redux.js.org/) comes back into play.

## Links

* **[How Redux works](redux.md)**.  Brief overview of how the Redux library works, and how you can use it to manage state in your app.

* **[An example: To-Do list](example.md)**.  For the rest of this section, we'll build a sample to-do list app that uses Redux to manage data that React components will use to update the to-dos.

* **[Adding custom reducers](reducers.md)**. '[Reducers](http://redux.js.org/docs/basics/Reducers.html)' are functions that determine how app state will be managed when an action is fired.  We'll write a reducer to add and remove to-dos.

* **[Adding actions](actions.md)**. [Actions](http://redux.js.org/docs/faq/Actions.html) trigger a state change that your reducers will handle.

* **[Wiring up to React](react.md)**. Once we have our reducers and actions, it's time to wire them up to our React components to trigger and 'listen' to state.

* **[Running the demo](demo.md)**. Let's run the demo, and see Redux in action.

* **[Server-side state](server.md)**. Redux works on both the server and in the browser. Server state is 'dehydrated' and sent down the wire for the browser to 'rehydrate' and use as its initial state.

* **[Redux DevTools](devtools.md)**. Redux DevTools is a free Chrome extension that lets you debug Redux state, and see changes to your application in real-time. ReactQL is compatible with DevTools out-the-box.
