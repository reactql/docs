# Zopfli Gzip and Brotli compression

---
Gzip is a standard compression technology supported by all major browsers, that can significantly reduce file sizes and data downloads, and provide users with a faster first load.

ReactQL uses the superior [Zopfli](https://en.wikipedia.org/wiki/Zopfli) algorithm, which typically results in files that are 3-8% smaller than zlib's maximum compression. All modern browsers automatically support this.

Additionally, ReactQL also compresses with  [Brotli](https://opensource.googleblog.com/2015/09/introducing-brotli-new-compression.html), an algorithm developed by Google that can achieve files sizes between 20-26% smaller than Zopfli compression. Browser support is growing, and Brotli versions are automatically served by the built-in web server (in production mode) where the browser support Brotli encoding.

Static assets that wind up in the `dist/` folder -- including CSS, images and fonts -- get gzip'd `.gz` versions automatically (and `.br`, for Brotli) courtesy of the [Compression Webpack Plugin](https://webpack.js.org/plugins/compression-webpack-plugin/) and [Brotli Webpack Plugin](https://github.com/mynameiswhm/brotli-webpack-plugin). Alongside the original, a new `[file].[gz|br]` will appear in the same folder -- e.g. `styles.css` gets a `styles.css.gz` and `styles.css.bz`, too.

The ReactQL web server that comes built-in will look for `.gz` and `.br` files before serving the original.  It'll automatically send the version that is best supported by the user's browser.

Since your assets are minified one-time in advance, this prevents CPU cycles crunching the data in 'real-time' for every visit.

You don't need to do anything to activate this&mdash; compression is enabled automatically.
