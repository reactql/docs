#Frequently Asked Questions

### **TL;DR:** I'm short on time. How do I run this now?</h2>

---
- Step 1: Install ReactQL with `npm i -g reactql`
- Step 2: Create a new project with `reactql new`, and run through the wizard
- Step 3: `cd` into your new project, and run `npm start`

This will spawn a 'hot reloading' client dev server on [http://localhost:8080](http://localhost:8080), and a full development web server with [server-side rendering](/ssr/README.md) [http://localhost:8081](http://localhost:8081),

You can play with the sample GraphQL server (provided by default, out-the-box) and run queries at [http://localhost:8081/graphql](http://localhost:8081/graphql)

To build and run in production, replace `npm start` with `npm run build-run`

### Why should I use ReactQL?

---
This starter kit is the product of over 2 years working with React, and GraphQL since its initial public release.

IMO, this represents the best available full-stack tooling for web apps in 2017. I use this stuff every day in production, so you can be confident it'll be maintained and updated regularly.

Use ReactQL if you want to skip the set-up, and get your next project up in record time.

### Where do I start coding?

---
`src/app.js` is the starting point to your app. Read it, understand it, then overwrite it with your own code.

### Is this production ready?

---
Open source is never finished. Some of the third-party packages in my stack may be in beta or pre-beta stages, so it's up to you to evaluate if they're a good fit for your application.

I personally use this starter kit as a basis for several heavy production loads.

### What kind of projects is ReactQL a good starter for?

---

ReactQL can be considered 'full-stack' or 'front-end', depending on your needs.

By default, it bundles a GraphQL server, a web server offering full server-side rendering over HTTP, and a complete browser front-end that provides single-page applications/websites.

It's highly configurable-- you can add REST server routes, set a custom 404 handler, render React universally, and use a built-in GraphQL server or point to one off-site, all from within `src/app.js`.

If you want a client-only app, you can build a static distribution package. If you want to run a web server and serve live traffic, you can build a Docker image using the built-in `Dockerfile` and enjoy the high-performance Koa web server config that's bundled as standard.

It's an ideal stack to use for building modern web-based apps.

### Is this Windows compatible?

---
Yes. The kit has been tested on Windows 10, but will probably work on other versions, too. Environment variables and paths are written to be Windows-compatible.

> Note: Node.js is generally less performant on Windows vs. Mac or Linux distros, so expect build times to be up to 2-3x slower. This shouldn't generally affect your development environment (other than start-up times).

### What's missing?

---
There's currently no test library, so feel free to add your own.

### Will ReactQL play nicely with themes or other frameworks?

---
ReactQL provides UI, flux/app state, a web server, GraphQL, routing, code bundling and SASS/PostCSS stylesheets out the box. It should play nicely with any framework that isn't opinionated about any of those things.

If you're using a theme that's built on React, many times it will include its own competing build flow for the site -- e.g. [Gulp](http://gulpjs.com/) for build tasks, [LESS](http://lesscss.org/) for stylesheets, [Browsersync](https://www.browsersync.io/) for hot code reloading, etc. The work involved in translating that flow to ReactQL can vary. It depends how tightly coupled the components are to the flow the author provides.

Try to opt for components that are 'self-contained', that don't rely on specific build tools to compile. I'd encourage you to use components that you are in control of that don't require lots of third-party tooling, where possible. Sometimes, it makes sense to use HTML themes and manually translate to React instead.

### I'm using `[insert database/back-end X here]`. Will ReactQL work?

---
ReactQL is designed to consume [GraphQL APIs](http://graphql.org/), and includes its own built-in web server to serve HTML on the front-end. Despite coming bundled with a GraphQL server, it's completely agnostic about your back-end, and will connect to any API that can speak GraphQL.  It's up to you to define your GraphQL schema in a way that 'queries' whichever back-end you want to use.

If you're using a database such as MySQL or PostgreSQL, and you'd typically use REST to interact with a legacy system, consider building a GraphQL server that's designed to handle more dynamic requests instead.

### How do I build a GraphQL server?

---
New in v2.0, ReactQL comes bundled with GraphQL server powers out-the-box. See [this page](/writing_code/graphql.md) for details on how it works.
