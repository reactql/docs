# Images

---
Import `.gif`, `.jp(e?)g`, `.png` or `.svg` images using standard `import` or `require` syntax:

```js
// `backgroundImage` will be a string of the filename, relative to `[root]/dist/public`
import backgroundImage from './bg.png';
```

You can then use the filename in your code, as usual:

```jsx
const Component = (
  <div>
    { /* `image` = string containing path to file name */ }
    <SomeOtherComponent image={backgroundImage} />
  </div>
);
```

You can also include images in your CSS files, which will be processed by Webpack, too:

```css
.logo {
  /* this will be processed exactly the same way as if imported in JS */
  background-image: url('./path/to/file.png');
}
```

### Image compression

In production, images are processed through [image-webpack-loader](https://github.com/tcoopman/image-webpack-loader), which minifies JPEG, GIF, PNG and SVG files via [imagemin](https://github.com/imagemin/imagemin) and copied to `[root]/dist/public/assets/img`. In development, original images files are served from memory (and compression is skipped), and no files are copied to the physical filesystem.

> By default, the JPG compression is set at 65% the quality of the original, and PNG has a target range of 65-90%. If images appear fuzzy, you can override this by editing [kit/webpack/base.js](https://github.com/reactql/kit/blob/master/kit/webpack/base.js)
