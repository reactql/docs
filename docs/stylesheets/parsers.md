# Extended CSS parsers

---
Alongside 'plain' `.css` files, you can use write your stylesheets with the following syntax:

## SASS support

---
ReactQL has [SASS](http://sass-lang.com/) support. Any imported file with a `.scss` or `.sass` extension will be parsed through [node-sass](https://github.com/sass/node-sass) first.

`@import` statements are also parsed through SASS first, so you can use parent settings, SASS functions and variables in the calling `.sass / .scss`, too.

## LESS support

---
ReactQL offers [LESS](http://sass-lang.com/) support, too. `.less` files will be parsed through the Webpack [less-loader](https://github.com/webpack-contrib/less-loader).

You can use any feature offered by the [LESS parser](http://lesscss.org/).
