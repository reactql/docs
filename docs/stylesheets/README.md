# Stylesheets

ReactQL supports plain CSS, SASS and LESS stylesheets.

Like regular Javascript, you can import the above file types into your code directly, and classnames will be available on the imported object for use inside your React components.

This section describes how CSS works in ReactQL, and how code is optimised.

## Links

* **[Writing CSS files](css.md)**. Where to put your stylesheet code, and how to import styles into your React components.

* **[SASS/LESS support](parsers.md)**. Write files in `.sass/.scss` (SASS) or `.less` (LESS), alongside regular 'plain' `.css`

* **[Next-gen CSS via PostCSS](postcss.md)**. All CSS code - whether plain or SASS/LESS - is ultimately optimised by PostCSS.

* **[Nesting](nesting.md)**. Thanks to PostCSS, even plain CSS code can be 'nested'. This page shows how to write nested classes and styles.

* **[Local modules](modules.md)**. By default, your CSS classes will be hashed to avoid namespace conflicts &mdash; making it trivial to 'scope' your classes to components.

* **[Global styles](globals.md)**. If you need styles to be output using their original classnames - say, for connecting to a library like Bootstrap or Semantic-UI, that's easy too &mdash; just follow the format shown on this page.

* **[Bundling styles](bundling.md)**. Styles are automatically extracted out into a `.css` file in production and included along with the initial page HTML in the browser.  This link explains how it works.

* **[Build pipeline for stylesheets](pipeline.md)**. Deep-dive into the Webpack build pipeline for stylesheets, and how it works under the hood.

* **[Server-side support](server.md)**. Styles work just as well on the server &mdash; no special syntax required!
