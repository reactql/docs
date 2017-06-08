# Fonts

---
Font files (`.woff`, `.woff2`, `.ttf`, `.eot`) can be included in any CSS in the usual way:

```css
@font-face {
  font-family: 'SomeCustomFont';
  font-style: normal;
  font-weight: 400; url(static/fonts/customFont.woff2) format('woff2');
}
```

```js
// `fontFile` = 'assets/fonts/whatever.ttf'
import fontFile from 'static/whatever.ttf';
```

> Files imported in a `.js` file return the string to the filename, relative to `[root]/dist/public/`:

No transformation is performed on font files; original files will simply be copied to `dist/public/assets/fonts` in production.
