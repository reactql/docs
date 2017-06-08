# Linking in the browser

---
To create hyperlinks between local routes, use the `<Link>` component provided by React Router:

```jsx
// From React Router
import { Link } from 'react-router-dom';

const Component = (
  <div>
    <Link to="/page/contact">Contact</Link>
  </div>
);
```

In the browser, clicking a link will load it *instantly*. There's no round-trip to the server, meaning your site will function like a [single page app](https://en.wikipedia.org/wiki/Single-page_application) without any browser refreshes, or DOM tear-down per request.

Existing GraphQL, Redux store data and Javascript variables will remain in memory between route transitions.
