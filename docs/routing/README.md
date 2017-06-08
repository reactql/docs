# Routing

Universal routing is provided by [React Router v4](https://reacttraining.com/react-router/).

## Links

* **[Declarative routes](declarative.md)**. Defining HTTP routes in your components will work universally, in both the browser and the server. You define routes _declaratively_ inside your components, instead of requiring a separate config.

* **[Server-side routing](server.md)**. Routes on the server will fire off real HTTP status code headers, and render the HTML specific to that route.

* **[Browser linking](browser.md)**. In the browser, views already loaded into memory are instantly navigable, providing a '[Single Page App](https://en.wikipedia.org/wiki/Single-page_application)' effect.

* **[Match parameters](match.md)**. Get access to route data inside a component, using 'match parameters'.

* **[Not Found (404) handling](notfound.md)**. You can define 404 handling however makes sense to your application - by displaying a page, redirecting to a 'global' 404 route, or handling things differently in the server.

* **[Redirects](redirects.md)**. Redirects work on both the server and the browser. The former will redirect with 301/302 HTTP status codes; the latter handle redirection by altering the URL in the location bar.
