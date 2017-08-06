# Project folders

Code is organised neatly into folders, to make it clear what goes where.

**TL;DR - Put your own code in `src`, and generally you won't need to edit anything else!**

Here's the folder layout:

## [`config`](https://github.com/reactql/kit/blob/master/config)

---
Project configuration files, such as the folder structure that ReactQL will use to determine where your code lives.

You shouldn't need to edit any files in here, unless you're making changes to the fundamental layout of the kit.

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
Webpack config files. [See here](webpack.md) for a complete break-down.

## [`src`](https://github.com/reactql/kit/blob/master/src)

---
This is where all of your own code will live. Start editing [`app.js`](https://github.com/reactql/kit/blob/master/src/app.js) -- this is where you define your app config, and export your root React component.

However else you organise your code `src` is entirely up to you.

## [`static`](https://github.com/reactql/kit/blob/master/static)

---
Put static files here that you want to wind up serving in production.

Webpack will automatically crunch any of your GIF/JPEG/PNG/SVG images it finds in here, as well as generate pre-compressed `.gz` versions of every file so that your Koa web server on [http://localhost:4000](http://localhost:4000) (after running `npm run build-run`) can serve up the compressed versions instead of the full-sized originals.
