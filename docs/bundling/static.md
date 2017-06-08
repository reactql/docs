# Static bundling

---
If you don't want to build a Node web server, you can run one of two commands:

`npm run build-browser`

or:

`npm run build-static`

Both commands create the full browser bundles: Javascript, CSS and the asset minification pipeline, and both commands dump the same files to `dist/public`. Both commands also skip generating a `server.js` file for running a web server.

The difference is the latter command _also_ creates a static `index.html` file that is injected with the correct `<link>` and `<script>` tags to load the latest (hashed) CSS and JS assets.

You can then upload `dist/public/*` to any static web host, and you'll have your complete ReactQL application running in the browser -- no web server required.

> Since `index.html` will contain just skeletal load code for your CSS and JS, you might want to check out a service like [Prerender.cloud](https://www.prerender.cloud/) to avoid the initial blank screen that will show before your app's JS is fully downloaded/rendered. You could also use the open source [prerender](https://github.com/prerender/prerender) lib if you want to spin up a pre-render service in-house.
