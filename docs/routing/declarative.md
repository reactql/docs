# Declarative routes, with React Router 4

---
ReactQL includes [React Router v4](https://reacttraining.com/react-router/).

Routes are declared _declaratively_ inside the component chain. There's no separate configuration to maintain - you simply tell React what to display when a route matches.

The syntax looks like this:

```jsx
// From React Router
import { Link, Route } from 'react-router-dom';

const Component = (
  <div>
    <ul>
      <li><Link to="/">Home</Link></li>
      <li><Link to="/page/about">About</Link></li>
      <li><Link to="/page/contact">Contact</Link></li>
    </ul>
    <hr />
    <Route exact path="/" component={Home} />
    <Route path="/page/:name" component={Page} />
  </div>
);
```

In the first `<Route>` in the above example, the `<Home>` component will load when the path matches `/` exactly.

In the second, `<Page>` will show when the path matches _at least_ `/path/...`, with a `match.params.name` prop being dynamically passed to `<Page>`.

> See the [React Router](https://reacttraining.com/react-router) docs for full usage details.
