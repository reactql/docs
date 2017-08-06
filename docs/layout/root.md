# Root files

---
There are various configuration files that you'll find in the root:

- [`.babelrc`](https://github.com/reactql/kit/blob/master/.babelrc):  This exists solely to transpile the ES6 Webpack config into something Node.js can natively run. It has no bearing on the [Babel](http://babeljs.io/) config that's used to transpile your Webpack code, so you can safely this leave alone.

- [`.editorconfig`](https://github.com/reactql/kit/blob/master/.editorconfig): Whitespace and syntax options for your editor/IDE. You probably won't need to change this, unless you prefer tabs vs. spaces or need to change the encoding of saved files.

- [`.eslintignore`](https://github.com/reactql/kit/blob/master/.eslintignore): Files the linter can safely ignore.

- [`.eslintrc.js`](https://github.com/reactql/kit/blob/master/.eslintrc.js): [ESLint](http://eslint.org/) configuration. If your editor/IDE has ESLint installed, it will use this file to lint your code.  See "[Styleguide](/writing_code/styleguide.md)" to see the syntax rules that ReactQL lints your code with.

- [`.gitignore`](https://github.com/reactql/kit/blob/master/.gitignore): Files to ignore when checking in your code.  This is built around the ReactQL starter kit, but you will probably want to use it as a base for your own code since it ignores the usual Node stuff, along with `dist` and some of the caching folders used by Webpack.

- [`browerslist`](https://github.com/reactql/kit/blob/master/browerslist): Browser target versions, so Webpack knows which polyfills to add. By default, we're targeting the last 3 versions of all major browsers.

- [`Dockerfile`](https://github.com/reactql/kit/blob/master/Dockerfile): Docker build file, for creating a Docker image that can be used to spawn production containers.

- [`package.json`](https://github.com/reactql/kit/blob/master/package.json): NPM packages used in this starter kit.  When you're extending this kit with your own code, you'll probably want to change the name, description and repo links and replace with your own.

- [`package-lock.json`](https://github.com/reactql/kit/blob/master/package-lock.json): If you're using NPM v5, this lock file will be re-used to speed up installing packages.

- [`postcss.config.js`](https://github.com/reactql/kit/blob/master/postcss.config.js): PostCSS config. Currently not used (placeholder for PostCSS v6+)

- [`webpack.config.babel.js`](https://github.com/reactql/kit/blob/master/webpack.config.babel.js): The Webpack entry point.  This will invoke the config found in [`kit/webpack`](https://github.com/reactql/kit/blob/master/kit/webpack) per the build command that spawned it.
