# Project folders

Code is organised neatly into folders, to make it clear what goes where.

Here's the folder layout:

## [`config`](https://github.com/reactql/kit/blob/master/config)

---
Project configuration files, such as the folder structure that ReactQL will use to determine where your code lives.

You can put your own settings in [`config/project.js`](https://github.com/reactql/kit/blob/master/config/project.js) or create new files in this folder to host them.

By default, [`config/project.js`](https://github.com/reactql/kit/blob/master/config/project.js) contains just the URI that Apollo will use to connect to your back-end GraphQL server. You can extend this with your own configuration options, for example SMTP details or other API endpoints.

This is written in ES6 style with no defaults, so you can import select configuration options from the client side without exposing credentials thanks to automatic tree-shaking/dead code elimination.

## [`kit`](https://github.com/reactql/kit/blob/master/kit)

---
The bulk of ReactQL is found in [`./kit`](https://github.com/reactql/kit/blob/master/kit).  If you need to dive into the Webpack config or add some custom functionality to your web server or browser instantiation, you'd do it here.

For the most part though, you probably won't need to touch this stuff.

### [`kit/entry`](https://github.com/reactql/kit/blob/master/kit/entry)

---
This is where Webpack looks for entry points for building the browser and the server.

> Note: There's no separate entry for 'vendors', since the bundle is built automatically by testing whether packages reside in `node_modules`

### [`kit/lib`](https://github.com/reactql/kit/blob/master/kit/lib)

---
Custom libraries built for ReactQL.  You'll find custom helpers for Redux and Apollo for creating new stores, building connections to your GraphQL endpoint via Apollo and more.

### [`kit/views`](https://github.com/reactql/kit/blob/master/kit/views)

---
Server-side React component views for rendering the full HTML.

Contains the following:

- [`browser.html`](https://github.com/reactql/kit/blob/master/kit/views/browser.html): Used when [building a static bundle](/bundling/static.md), this file is used to generate the resulting `dist/public/index.html` file that bootstraps your CSS and Javascript code. `<script>` and `<link>` is automatically injected by Webpack to point to the latest assets.

- [`ssr.js`](https://github.com/reactql/kit/blob/master/kit/views/ssr.js): The `<Html>` server-side root component. Generates the HTML, inserts title and meta tags, and dehydrates Redux store which the client uses to seed the initial application state.

- [`webpack.html`](https://github.com/reactql/kit/blob/master/kit/views/webpack.html): used by the Webpack to load a minimal bootstrap when running a local development server.

### [`kit/webpack`](https://github.com/reactql/kit/blob/master/kit/webpack)

---
Webpack v2 config files. [See here](webpack.md) for a complete break-down.

## [`src`](https://github.com/reactql/kit/blob/master/src)

---
This is where all of your own code will live. By default, it contains the `<App>` component in [`app.js`](https://github.com/reactql/kit/blob/master/src/app.js) which demonstrates a few of the concepts that this starter kit offers you, along with CSS defined in various style files.

You can overwrite these files directly with your own code and use this as a starter point.

## [`static`](https://github.com/reactql/kit/blob/master/static)

---
Put static files here that you want to wind up serving in production.

Webpack will automatically crunch any of your GIF/JPEG/PNG/SVG images it finds in here, as well as generate pre-compressed `.gz` versions of every file so that your Koa web server on [http://localhost:4000](http://localhost:4000) (after running `npm run build-run`) can serve up the compressed versions instead of the full-sized originals.
