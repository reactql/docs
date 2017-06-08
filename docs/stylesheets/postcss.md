# Next-generation CSS parsing (via PostCSS)

---
All stylesheets - plain CSS, LESS or SASS - are all ultimately parsed through [CSSNext](http://cssnext.io/) (a collection of [PostCSS](http://postcss.org/) plugins) as a final step.

That means you can use things like nested statements out-the-box in plain `.css`:

```css
.anotherClassName {
  h1 {
    text-size: 2em;
  }
  p {
    color: green;
  }
}
```

As well as variable names, and other goodies:

```css
:root {
  --mainColor: red;
}
a {
  color: var(--mainColor);
}
```

> Since SASS and LESS use different syntax, you'll need to write styles that are compatible with the respective parsers before reaching the PostCSS step.

Vendor prefixes will automatically be added, so you can write the bare CSS and let PostCSS worry about polyfilling browsers.

See [CSSNext](http://cssnext.io/) for more details and syntax.
