# Build pipeline for stylesheets

---
You can write stylesheets in plain CSS (.css), [SASS](http://sass-lang.com/)) (.scss / .sass) or [LESS](http://lesscss.org/) (.less).

You can also mix and match all three, import styles into your components, and reference classes within those stylesheets as if you're referencing a regular Javascript object.

Classnames will automatically be 'localised' so they're scoped to the component that imported them -- preventing 'bleed out' into the global namespace (examples are given below), unless your file ends `.global.(css|sass|scss|less)`, in which case the original classnames are preserved.

**Every stylesheet goes through the following Webpack compilation pipeline:**

1. If you're using SASS or LESS, the CSS is first run through the relevant Webpack loader (details in the relevant section below) to transform it into plain CSS.

2. Your original CSS code (or the resulting CSS dumped by the SASS/LESS loader) is then passed through PostCSS to add vendor prefixes, enable [CSSNext](http://cssnext.io/) features, SASS-style [nesting](nesting.md), and minify your code.

3. The Webpack [CSS loader](https://github.com/webpack-contrib/css-loader) inspects your classnames, and produces a hashed, or 'localised' version of them, to prevent namespace clashes with other styles that may use the same classnames in other components.  You can then import the stylesheet just as you'd import any other Javascript file, and the original classname will be a key that points to the hashed version, making it easy to reference the new classname in your React components.

4. In production, your styles are concatenated, minified and placed in `dist/public/assets/css/style.[hash].css` via the [Extract Text plug-in](https://github.com/webpack-contrib/extract-text-webpack-plugin). Even if you use multiple imports, multiple style formats (SASS, LESS), or code that is only imported on code-split components, all resulting CSS code will wind up in this one file.

5. Your stylesheet is automatically loaded on the initial view by your web server. This ensures all styles are available to your components, preventing 'flicker' upon first load.

> In development, your styles are bundled into the resulting Javascript code, so there may be a brief moment when your content appears unstyled before the bundle is loaded. This won't happen in production, since the CSS is loaded in the `<head>` section before any HTML content is parsed by the browser.
