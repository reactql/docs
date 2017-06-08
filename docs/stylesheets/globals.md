# Global styles

---
If you want to override the 'local by default' classnames, you have two options:

### 1. Use `*.global.(css|sass|scss|less)` files

---
**This is the preferred / most fail-safe option**.

By suffixing your style files with `.global.css` (plain CSS), `.global.scss` / `.global.sass` (SASS) or `.global.less` (LESS), classnames within those files are preserved and won't be localised.

This is useful for integrating third-party style frameworks where components expect the original classnames to be used:

**app.js**
```js
// Import your style globally. No need to assign it to a variable --
// it'll wind up in our style.[hash].css file just the same
import './styles.global.scss';
```

**styles.global.scss**
```scss
/* example: importing the Foundation Sites SASS library */
@import '~foundation-sites/scss/foundation';
@include foundation-everything;
```

### 2. The `:global` prefix

---
Note: **this method is generally not recommended**. See below for an edge case that can creep up.

You can prefix `:global` before any rule and it'll be made available across your entire app:

```css
:global .thisClassWontRename {
  font-color: blue;
}
```

In this case, `.thisClassWontRename` will be the exact name used in the output to your final .css file, so you can use this class name wherever you want the style to apply - anywhere in your code.

`:global` will work across all parsers -- plain CSS, SASS and LESS -- because all CSS is ultimately parsed through the [CSS loader](https://github.com/webpack-contrib/css-loader).

However, you can run into problems with `:global` due to the way PostCSS combines rules to save space.

Consider this code:

```css
html, body {
  height: 100%;
}

:global someSelector {
  height: 100%;
}
```

In production, PostCSS sees that the second `height: 100%` is redundant, and will combine the tags like this:

```css
:global someSelector, html, body {
  height: 100%;
}
```

... which will throw an error, since `:global` is being prefixed incorrectly.

For this reason, it's better to put all of your styles in a separate `.global.(css|scss|sass|less)` file described in the first method above.

> Note: Avoid using `@import` statements inside of a `:global` block. Imports are intended to be top-level statements, which means they will 'break out' of a surrounding global block and wind up as local modules. Instead, use the method below.
