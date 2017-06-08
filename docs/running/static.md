# Building a static app (i.e. no web server)

---
If you only wish to target a browser and you don't care about server-side rendering or running a web server, you can build assets with:

`npm run build-static`

In addition to the regular Javascript, CSS and asset pipeline, the above command will also generate a static `index.html` file that will automatically load stylesheets and Javascript in the browser.

You can then upload the contents of `dist/public` to any static file host (S3, Netlify, Github pages, etc) or FTP to your root web directory on any host, and you'll have a complete application, minus the web server.

> Note: Your `index.html` file will contain only the minimum needed to bootstrap your application -- your JS code will do the rest. You can customise the HTML that is sent back by editing `kit/views/browser.html`. Note that CSS and JS will be injected automatically by Webpack into the `<head>` and footer sections of the page.

To run a local static web server (for testing your bundle), run:

`npm run static`

Or, you can combine the above two commands with:

`npm run build-static-run`
