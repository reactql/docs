---
description: Modern starter kit for React, Apollo, Redux, React Router 4, Webpack 2
---

<img src="img/reactql-logo.svg" width="250" alt="ReactQL"/>

![Travis](https://api.travis-ci.org/reactql/kit.svg?branch=master) [![GitHub stars](https://img.shields.io/github/stars/reactql/cli.svg?style=flat-square)](https://github.com/reactql/cli/stargazers) ![npm](https://img.shields.io/npm/dt/reactql.svg?style=flat-square) ![license](https://img.shields.io/github/license/reactql/kit.svg?style=flat-square) ![Libraries.io for GitHub](https://img.shields.io/librariesio/github/reactql/kit.svg?style=flat-square) [![GitHub issues](https://img.shields.io/github/issues/reactql/kit.svg?style=flat-square)](https://github.com/reactql/kit/issues)

ReactQL is React + GraphQL done properly &mdash; for Mac, Windows and Linux.

It combines best-of-breed choices for UI, GraphQL data fetching, CSS and code bundling, handles server-side rendering (SSR) properly, and is fast and extensible. You can choose Javascript or Typescript flavours.

It focuses on performance characteristics that you don't often find in other starter kits &mdash; offering Zopfli/Brotli compression, automatic vendor splitting, aggressive minification of JS/CSS, instant hot code reloading and more, out-the-box.

It pairs an async web server for handling SSR, non-JS imports (like images, CSS, etc) and works universally. Your code will run both in the browser, and on the server &mdash; even inline imports!  

Development, production and even static bundling can be invoked with just one command, via the [ReactQL CLI](https://github.com/reactql/cli).

You can easily [bolt-on your own GraphQL server](https://github.com/reactql/examples/tree/master/graphql-server), or point to one off-site.

If you want to shave weeks off your next project boilerplate, try ReactQL.

## Video: Intro to ReactQL

---
In this 15 minute video, [Lee Benson](http://github.com/leebenson) (ReactQL author/maintainer) walks you through the headline features of ReactQL, and shows you how you can spawn a new project in one command:

{% youtube %}
https://www.youtube.com/watch?v=hFm4PBQghgA
{% endyoutube %}


## Features

### Stack

- [ReactQL CLI](https://github.com/reactql/cli) for quickly starting a new project
- [React v15](https://facebook.github.io/react/) for UI
- [Apollo Client (React)](http://dev.apollodata.com/react/) for GraphQL
- [React Router 4](https://github.com/ReactTraining/react-router/tree/v4) for declarative browser + server routes
- [Redux](http://redux.js.org/) for flux/store state management

### Server-side rendering

- Built-in [Koa 2](http://koajs.com/) web server, with async/await routing
- Full route-aware [server-side rendering (SSR)](https://reactql.org/docs/ssr) of initial HTML
- Universal building - both browser + Node.js web server
- HTTP header hardening with [Helmet for Koa](https://github.com/venables/koa-helmet)
- Declarative/dynamic `<head>` section, using [react-helmet](https://github.com/nfl/react-helmet)

### Real-time

- Dev + [React-compatible hot code reloading](http://gaearon.github.io/react-hot-loader/); zero refresh, real-time updates
- [Development web server](https://reactql.org/docs/setup#development) that automatically rebuilds and restarts on code changes, for on-the-fly SSR testing with full source maps


### Code optimisation

- [Webpack v3](https://webpack.js.org/), with [tree shaking](https://webpack.js.org/guides/tree-shaking/)
- Universal building - both browser + Node.js web server
- Easily extendable [webpack-config](https://fitbit.github.io/webpack-config/) files
- Separate local + vendor bundles, for better browser caching/faster builds
- Dynamic polyfills, courtesy of [babel-preset-env](https://github.com/babel/babel-preset-env)
- Aggressive code minification with [Uglify](https://webpack.github.io/docs/list-of-plugins.html#uglifyjsplugin)
- [GIF/JPEG/PNG/SVG crunching](https://github.com/tcoopman/image-webpack-loader) for images

### Styles

- [PostCSS v6](http://postcss.org/) with [next-gen CSS](http://cssnext.io/) and inline [@imports](https://github.com/postcss/postcss-import)
- [SASS](http://sass-lang.com) and [LESS](http://lesscss.org/) support (also parsed through PostCSS)

### Production-ready

- [Production bundling](https://reactql.org/docs/bundling/production), that generates optimised server and client code
- [Static bundling mode](https://reactql.org/docs/bundling/static) for hosting your full app on any static host -- Github pages, S3, Netlify, etc
- [Static compression](https://webpack.js.org/plugins/compression-webpack-plugin/) using the [Zopfli Gzip](https://en.wikipedia.org/wiki/Zopfli) and [Brotli](https://opensource.googleblog.com/2015/09/introducing-brotli-new-compression.html) algorithms for the serving of static assets as pre-compressed `.gz` and `.br` files (default `vendor.js.bz` goes from 380kb -> 89kb!)
- [Docker](https://www.docker.com/) support, out-the-box.

### Developer support

- [ESLint v3](http://eslint.org/)ing based on a tweaked [Airbnb style guide](https://github.com/airbnb/javascript)
- [Jest](https://facebook.github.io/jest/) test runner
- Tons of code commentary to fill you in on what's happening under the hood
- Extensive, up-to-date [online documentation](https://reactql.org/docs/)
- [Examples repository](https://github.com/reactql/examples), showing you how to add a GraphQL server, run without GraphQL, take advantage of Redux, etc.

## Usage

See the **[CLI tool](https://github.com/reactql/cli)** for easily deploying this starter kit on Mac, Windows or Linux.

Then run `npm start` in the project root, and away you go!

## Docker

A [Dockerfile](https://github.com/reactql/kit/blob/master/Dockerfile) is included, that will build, optimise and bundle a production-mode ReactQL web server, your static assets and client-side code -- making it trivial to deploy to production.

Build as normal with:

`docker build . -t <project>`

Then run with:

`docker run -p 4000:4000 <project>`

Navigating to http://<docker_host>:4000 will yield the ReactQL project code.

# New to GraphQL?

Watch my free [45 minute YouTube video](https://www.youtube.com/watch?v=DNPVqK_woRQ), for a live coding walk-through of putting together a GraphQL server with a database. Learn how to write queries, mutations and handle nested/related data.

If you want to build your own GraphQL server, check out the [GraphQL Server repo](https://github.com/reactql/examples/tree/master/graphql-server) in [examples](https://github.com/reactql/examples).
