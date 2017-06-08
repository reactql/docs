# CSS / stylesheets

---
You can import `.css` or `.scss`/`.sass` ([SASS](http://sass-lang.com/)) stylesheets by simply `import/require`ing from any Javascript file:

```js
// `styles` will be an object that contains a list of exported 'hashed' classnames
import styles from 'src/css/whatever.css';
```

Classnames will be [hashed](https://github.com/webpack-contrib/css-loader#css-scope) to prevent bleeding out to the global scope. This can be overridden by putting your styles inside a [global style file][/stylesheets/globals.md].

> See [Stylesheets docs](css.html) for examples.

`@import` statements within CSS will be concatenated in the final bundle:

```css
@import url(other/css/file.css);
```

If you're using SASS, imports will be processed via SASS first; settings, SASS variables and functions will be available to any CSS file that uses `@import` to pull from a parent SASS file.
