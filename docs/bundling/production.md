# Production mode

---
To build assets fit for deployment, run:

```bash
npm run build
```

Webpack will follow these steps:

1. It will first build your *browser* bundle by loading the Webpack config file at [kit/webpack/browser_prod.js](https://github.com/reactql/kit/blob/master/kit/webpack/browser_prod.js), which will use [kit/src/browser.js](https://github.com/reactql/kit/blob/master/kit/entry/browser.js) as its entrypoint.

2. Webpack will then build your *server* bundle by loading the Webpack config file at [kit/webpack/server.js](https://github.com/reactql/kit/blob/master/kit/webpack/server.js), which will use [kit/src/server.js](https://github.com/reactql/kit/blob/master/kit/entry/server.js) as its entrypoint.

3. Assets will appear in a new `[root]/dist` folder. A sub-folder, `./dist/public` is created which becomes the public entry point for the built-in [Koa web server](http://koajs.com/).

3. All `./css` files are extracted out, optimised and concatenated into a separate `dist/public/assets/css/style.css` file.  Styles are processed through the [PostCSS](http://postcss.org/) loader. On the server, hashed versions of any class names used are calculated and included in the server bundle, so invoking those classes later alongside React components will match up with the compiled `style.css` file.

4. Imported images are optimised/crunched through [imagemin](https://github.com/imagemin/imagemin), and wind up in `dist/public/assets/img/`.

5. Imported fonts are copied to `dist/public/assets/fonts`.

> Once assets have been built, you can run `npm run server` to start a live web server
