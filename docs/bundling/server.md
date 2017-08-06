# Server bundling

---
Webpack isn't just for the browser. ReactQL will also generate an optimised _server_ bundle that's ready to use in production.

This allows you to write your code to target a 'universal' platform, that will run in exactly the same way in the browser as well as via a Node.js server.

Just like in the browser, that makes code like this perfectly valid on the server:

```js
// importing a .css file and treating it like JS would be impossible in a browser...
import css from 'some/stylesheet.css'

console.log(css.classname); // <-- what the...?!
```

The server bundle contains a built-in [Koa web server](http://koajs.com/) that will listen to HTTP requests, render the relevant React code into HTML, and serve it back to your user.

This allows you to offer fast *time-to-first-byte* to visitors, without waiting for the full browser bundle to download and process first. Instead, users will be greeted with initial HTML and all styles intact, giving a more 'progressive' experience when the bundle eventually loads.
