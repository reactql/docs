# Code bundling

Code bundling is the process of turning your raw source code, into something that can be run in the browser and/or on the server.

ReactQL includes an [extensible](https://github.com/reactql/kit/tree/master/kit/webpack) Webpack configuration chain that optimises your code for both development and production environments.

In this section, you'll learn how it works with your Javascript, CSS and static assets.

## Links

* **[Webpack](webpack.md)**. Webpack v3 is the engine that transform your source into a minified bundle that can work in your target environment.  This link explains how it works.

* **[Server bundling](server.md)**. Bundling isn't just for the browser. To enable inline imports of non-Javascript files, Webpack can also transform your source into a server bundle for handling your production web traffic and server-side rendering.

* **[Config files](config.md)**. ReactQL contains a collection of config files for transpiling code for the browser, server, in development, production and static modes.

* **[CSS / stylesheets](css.md)**. How Webpack bundles together your styles.

* **[Images](images.md)**. You can `import` images into your Javascript code, just like CSS or other JS files. The import variable will be transformed automatically to the public path of the file, making it simple to drop into React components. But there's more to it than that &mdash; Webpack will also crunch your assets in production. This link explains how.

* **[Fonts](fonts.md)**. Inline font imports, for use with CSS styles.

* **[JSON](json.md)**. In contrast to Node.js' native `.json` importing, Webpack transforms the JSON file into a plain object that's included along with the target bundle. This makes it compatible both on the server, and in the browser.

* **[Development mode](development.md)**. How to spawn a development environment, and a deep-dive into what happens beneath the Webpack hood.

* **[Production mode](production.md)**. Turn your code into a bundle that's ready to handle your live web traffic.

* **[Static bundling](static.md)**. If you want to build a browser-only bundle that's compatible with static hosts such as Github Pages, S3, etc, this is how you do it.

* **[Compression](compression.md)**. Your images, fonts, CSS and JS code are minified in production, but they're also compressed &mdash; using both the Zopfli (gzip) and Brotli algorithms, for faster overall load times.

* **[Building a Docker image](docker.md)**.  Your kit ships with a default `Dockerfile` that can be used to build a Docker image, for deploying to Kubernetes, Rancher, or any containerisation platform.
