# Redirects (301/302) routes

---
Like the `<NotFound>` component, there's a `<Redirect>` available too to handle client and server side route redirection:

```jsx
// `<Switch>` component that will execute the first matching route
import Switch from 'react-router-dom';

// `<Redirect>` either 'permanently' or temporarily
import { Redirect } from 'kit/lib/routing';

// Create a redirect component by extending `<Redirect>`
const RedirectElsewhere = () => <Redirect to="/somewhere/else" />;

// Redirect if the route isn't found
export default () => (
  <Switch>
    <Route exact path="/" component={Home} />
    <Route path="/page/:name" component={Page} />
    <Route component={RedirectElsewhere} />
  </Switch>
);
```

The ReactQL `<Redirect>` component extends the 'native' component of the same name in [React Router v4](https://reacttraining.com/react-router/web/api/Redirect) and offers the same `from`, `to`, and `push` attributes.

It adds the `permanent` boolean option, too. If `permanent=true`, then `routeContext.status === 301` inside the [`createReactHandler`](https://github.com/reactql/kit/blob/master/kit/entry/server.js#L100) that renders the React chain. If `permanent=false`, then `routeContext.status === 302`.
