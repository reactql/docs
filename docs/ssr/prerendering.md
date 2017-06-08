# SSR vs. pre-rendering

---
Pre-rendering is a technique for interpreting client-only apps ahead of time, and serving the 'cached' data to a user. Libraries and services such as [prerender.io](https://prerender.io/) make it possible to simulate many of the benefits of server-side rendering, without writing code that targets a server platform.

Whilst pre-rendering is generally a step up from serving 'headless' client bundles, 'real' SSR provides the ultimate experience for your users.

Here are the key differences:

1. **Data is often 'stale'**. With pre-rendering, you're serving a cached version of the page, which could be minutes or hours out-of-date.  By contrast, ReactQL's SSR allows you to serve the 'real' request on demand, and offer content specific to that request.

2. **Initial HTML is often generic**. Pre-rendering works by spawning a headless Javascript browser, loading the route, running Javascript on the page, and capturing the resulting DOM.  Since this happens en masse and not per visitor, you often forego the opportunity to personalise the HTML with data specific to the user.

3. **[Flash of unstyled content](https://en.wikipedia.org/wiki/Flash_of_unstyled_content) or 'flicker' effects are commonplace**. Since you're serving generic data and there's no server to pre-process data loading requests, DOM changes will often be made after the initial HTML is served.  This can lead to 'flicker' effects or content that suddenly gets style information applied, changing its position or look on the page.  By contrast, ReactQL sends down full, optimised CSS style information with the initial HTML, so content looks good immediately - and stays that way.

4. **No heavy lifting by the server**. A web server can strengthen the user experience by making asynchronous data requests to your GraphQL server or database, caching relevant information, or generally providing functionality that's not available on the client-side-- which can all add to the initial HTML sent down.  By contrast, pre-rendering doesn't have a 'web server'-- it blindly dumps back static HTML and leaves the rest to the client.
