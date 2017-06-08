## Basic concepts: Webpack 2

---
[Webpack](https://webpack.js.org/) is a code bundling tool that turns your raw source code into a single 'bundle' file that can run in the browser.

Out-the-box, ReactQL uses syntax that a regular browser cannot understand without being [transpiled](https://en.wikipedia.org/wiki/Source-to-source_compiler) down to plain Javascript.

This can include variants of JS that don't yet ship with common Javascript interpreters that are bundled with browsers (such as native `async/await` code, or module `import` statements), as well as features that are unique to Webpack, such as the ability to use local `.css` files and translate stylesheet classnames into [locally hashed versions](css.html#local).

This is where Webpack comes in. It will translate many files of source code into a single bundle that will be loaded along with your HTML code in the browser. That's why it's valid to write code like this:

```js
// importing a .css file and treating it like JS would be impossible in a browser...
import style from './someFile.css'

console.log(style.someClassName); // <-- woah!
```

... and actually see it working in the browser.

Furthermore, it includes several pre-processors that will crunch and optimise your code for production, as well as provides functionality for spawning a development server with source-maps, hot code reloading and more.
