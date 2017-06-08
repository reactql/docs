# Development mode

---
In development, ReactQL will:

- Run a 'hot reloading' Webpack dev server at [http://localhost:8080](http://localhost:8080)
- Run a development web server for [server-side rendering](/ssr/README.md) at [http://localhost:8081](http://localhost:8081)
- Build both browser and server-side [development bundles](/bundling/development.md)
- Enable sourcemaps for your CSS and Javascript code
- Activate hot code reloading. Any changes to your code will update automatically in your Webpack dev server; to get a new server-side first page render from your web server, just hit refresh in the browser.

To activate development mode, `cd` to your starter kit folder, and run:

```bash
npm start
```
