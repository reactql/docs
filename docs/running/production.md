# Production mode

---
In production, ReactQL will:

- Build a [server bundle](/bundling/server.md), which includes a built-in Koa web server
- Activate [server-side rendering (SSR)](/ssr/README.md) for your React components / GraphQL data fetching
- Create a [minified browser bundle](/bundling/production.md)
- Crunch your [CSS](/bundling/css.md), [images](/bundling/images.md) and [other web assets](/bundling/fonts.md)

To run it, you first need to build the server and client bundles with:

```bash
npm run build
```

Then, simply run:

```bash
npm run server
```

... which (by default) spawns a server at [http://localhost:4000](http://localhost:4000)

> Tip: `npm run build-run` has same effect as running the above two commands separately.
