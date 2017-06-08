# Development mode

---
To start a development server, run:

```bash
npm start
```

This will create two 'servers':

1. A 'hot reloading' Webpack dev server. This will build the [kit/entry/browser.js](https://github.com/reactql/kit/blob/master/kit/entry/browser.js) entry point into a browser-only bundle. Any code changes will be 'pushed' to the browser in real-time.

2. A full development web server. This builds [kit/entry/server_dev.js](https://github.com/reactql/kit/blob/master/kit/entry/server_dev.js) into a working web server, and runs it, enabling you to test [server-side rendering](/ssr/README.md) on-the-fly. Code changes will automatically re-build and restart the server; just hit refresh in your browser to see the new HTML.

This is what Webpack will do when spawning in development:

Two configurations are loaded simultaneously:  [kit/webpack/browser_dev.js](https://github.com/reactql/kit/blob/master/kit/webpack/browser_dev.js) for browser bundling, and [kit/webpack/server_dev.js](https://github.com/reactql/kit/blob/master/kit/webpack/server_dev.js) for building a development web server.

## For the Webpack dev server (browser bundle)

Webpack will start processing code in the [kit/entry/browser.js](https://github.com/reactql/kit/blob/master/kit/entry/browser.js) entry file, start a development server at [http://localhost:8080](http://localhost:8080) and compile your source code into 'in memory' code bundles, at [http://localhost:8080/vendor.js](http://localhost:8080/vendor.js) (for third-party NPM code) and [http://localhost:8080/bundle.js](http://localhost:8080/bundle.js) (your own code). No physical files are stored on the filesystem.

All routes will be served by [kit/views/webpack.html](https://github.com/reactql/kit/blob/master/kit/views/webpack.html). In development mode, there is no server-side rendering. Everything is loaded in the browser. That means GraphQL data fetching or anything 'async' will cause React to re-render with the correct props once it's retrieved them.

Stylesheets will be included as inline code inside `bundle.js`. You might notice a [flash of unstyled content](https://en.wikipedia.org/wiki/Flash_of_unstyled_content) as `/bundle.js` is first loaded before snapping your styles into place.

The `./static` folder becomes your public route. Anything you might place in here - images, third-party scripts, etc - will be served 'unprocessed', in their original form.

A small snippet of code will be added to your in-memory `/vendor.js` entrypoint for handling hot code reload via websockets. Whenever you make changes to your code, the browser is 'injected' with the code difference and reflected in real-time.

Development mode is not intended for production environments. Code bundles will be larger than production versions due to unminified sourcemaps and original files, and there is no server-side rendering in this mode.

## For the web server bundle (SSR):

Webpack starts at  [kit/entry/server_dev.js](https://github.com/reactql/kit/blob/master/kit/entry/server_dev.js), bundles server code at `dist/server_dev.js`, and spawns a web server at [http://localhost:8081](http://localhost:8081). Static files are stored in `dist/dev`.

A client-side bundle is generated for `dist/dev/vendor.js` and `dist/dev/browser.js`. A CSS file is generated in `dist/dev/assets/css/style.css`. The development web server will provide HTML code to load all of these files in the web server.

Any images, fonts, or other static assets included in your code, will wind up in `dist/dev` too. This folder will be the public mount point for all requests to [http://localhost:8081](http://localhost:8081). If the file doesn't exist, it will be the ReactQL [React handler](https://github.com/reactql/kit/blob/master/kit/entry/server.js#L100) that serves the request (which is how routing on the server works.)

The client bundles essentially uses the production browser bundling config, with two exceptions:

1. Source maps are included, and `process.env.NODE_ENV === 'development'`.

2. When you make changes to code (anywhere outside of Webpack config files), the server and browser bundles will be re-generated, and the server re-started. This allows you to refresh the page in the browser, and see the very latest version of your app via [server-side rendering](/ssr/README.md).
