# Webpack config files

[Webpack](https://webpack.js.org/) v3 takes care of building our server and browser bundles in development, production and static modes, as well as compressing assets, hot code reloading, and more.

It's at the heart of ReactQL's bundling process.

Chances are, we've already provided everything you need to spawn a new project.

But, getting to grips with Webpack and knowing how to extend it, gives you the flexibility to define your build pipeline exactly how you want it to work, should you ever need to customise.

## Files in [`kit/webpack`](https://github.com/reactql/kit/blob/master/kit/webpack)

- [`base.js`](https://github.com/reactql/kit/blob/master/kit/webpack/base.js): Base configuration that all others inherit from
- [`browser.js`](https://github.com/reactql/kit/blob/master/kit/webpack/browser.js): Base configuration for the browser.  Inherits from base, and is extended by browser_dev and browser_prod
- [`browser_dev.js`](https://github.com/reactql/kit/blob/master/kit/webpack/browser_dev.js): Config for the browser spawned at [http://localhost:8080](http://localhost:8080) when running `npm start`
- [`browser_prod.js`](https://github.com/reactql/kit/blob/master/kit/webpack/browser_prod.js): Production browser bundling.  Minifies and crunches code and images, gzips assets, removes source maps and debug flags, builds your browser bundles ready for production.  This is automatically served back to the client when you run `npm run build-run`
- [`common.js`](https://github.com/reactql/kit/blob/master/kit/webpack/common.js): Common objects shared amongst multiple Webpack config files, to save keystrokes
- [`dev.js`](https://github.com/reactql/kit/blob/master/kit/webpack/dev.js): Common settings for building a development bundle, that other config files can extend from
- [`eslint.js`](https://github.com/reactql/kit/blob/master/kit/webpack/eslint.js): Entry point for the linter, to properly follow local module folders and avoid false positives
- [`server.js`](https://github.com/reactql/kit/blob/master/kit/webpack/server.js): Node.js web server bundle.  Even though we're running this through Node, Webpack still gets involved and properly handles inline file and CSS loading, and generates a build that works with your locally installed Node.js. You can build the server with `npm run build-server` or build and run with `npm run build-run`. Both the development and production web servers extend this config
- [`server_dev.js`](https://github.com/reactql/kit/blob/master/kit/webpack/server_dev.js): Used when you run `npm start` to create a development web server for [server-side rendering](/ssr/README.md). When you run that command make a change to your project code, the web server will automatically re-build and restart
- [`server_prod.js`](https://github.com/reactql/kit/blob/master/kit/webpack/server_prod.js): When you run `npm run build`, this config file is used to generate a production web server bundle
- [`static.js`](https://github.com/reactql/kit/blob/master/kit/webpack/static.js): Extends from [`browser_prod.js`](https://github.com/reactql/kit/blob/master/kit/webpack/browser_prod.js), by also creating a static `index.html` file that allows you to host a browser-only version of your app -- no web server required
