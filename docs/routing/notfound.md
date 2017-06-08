# Not found (404) routes

---
There's probably times you'll want to display content when a route _doesn't_ match. Say, if someone navigates to a link that doesn't exist, and you want to tell the user they've hit a wrong turn.

For those times, we've included a `<NotFound>` component that you can use like this:

```js
// `<Switch>` component that will execute the first matching route
import Switch from 'react-router-dom';

// NotFound 404 handler for unknown routes in `kit/lib/routing`
import { NotFound } from 'kit/lib/routing';

// Assuming we have a `<Home>` that will show up when the path is '/',
// <Page> that will show when the route is /page/whatever, and <NotFound>
// at all other times
export default () => (
  <Switch>
    <Route exact path="/" component={Home} />
    <Route path="/page/:name" component={Page} />
    <Route component={NotFound} />
  </Switch>
);
```

You can extend the component by adding your own content like this:

```jsx
// Create a component that extends `<NotFound>`
const YourOwn404 = () => (
  <NotFound>
    <h1>Hey - no route here by that name, buster!</h1>
  </NotFound>
);

// This will execute the first route that matches (`<YourOwn404>` if not)
export default () => (
  <Switch>
    <Route path="/route/that/exists" component={TryThisFirst} />
    <Route component={YourOwn404} />
  </Switch>
);
```

> On the server, if a component renders `<NotFound>` (or any component that extends it), then `routeContext.status === 404` inside the [`createReactHandler`](https://github.com/reactql/kit/blob/master/kit/entry/server.js#L100) function that renders the React chain. This allows you to add your own 404 strategy (say, redirecting to a common 'not found' page). If you want to do anything special on the server-side, the implementation is left up to you.
