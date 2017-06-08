# Server-side rendering

ReactQL apps run on both a Node.js server, and in the browser.

This makes it trivial to write apps that render full HTML on the initial page load, with a browser bundle that can continue where the server finishes.

That means faster apps, better search engine indexing, and a better overall experience for your users.

## Links

* **[Why use server-side rendering?](benefits.md)**. The benefits of SSR are numerous; find out why it makes sense to use it, and how it can benefit your UI/UX.

* **[SSR vs. pre-rendering](prerendering.md)**. SSR goes further than 'pre-rendering'. Learn the differences, and why SSR is often the superior choice.

* **[How ReactQL implements SSR](features.md)**. ReactQL's SSR implementation covers HTML rendering, declarative `<head>` configs, Redux stores and CSS rendering. This link explains how it all fits together.

* **[Environment awareness](environment.md)**. You can detect whether your code is running on the server or in the browser, making it simple to import DOM-only packages or run private server code that won't find its way into the browser bundle.  Here's why.
