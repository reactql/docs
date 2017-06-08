# Writing CSS files

---
CSS can be written and placed anywhere. A common pattern is to write the `.css` alongside regular `.js` files, so they 'live' in the same place.

You can import and use styles in your code like regular Javascript:

Inside your CSS:

**someCssFile.css**
```css
.someClass {
  font-weight: bold;
  text-align: center;
  color: red;
}
```

**someJsFile.js**
```jsx
import css from './someCssFile.css';

// .someClass will get transformed into a hashed, 'local' name, to avoid
// collisions with the global namespace
export default props => (
  <div>
    <p className={css.someClass}>Hello world</p>
  </div>
)
```

> You can import `.css` (plain CSS), `.scss` &amp; `.sass` ([SASS](http://sass-lang.com/)) and `.less` ([LESS](http://lesscss.org/)) files. All three flavours export [localised classnames](modules.md).
