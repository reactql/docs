# JSON

---
JSON stored in a `.json` file will be processed through [json-loader](https://github.com/webpack-contrib/json-loader), and return a parsed Javascript object of the JSON data.

Example:

**data.json**
```json
{
  "name": "ReactQL"
}
```

**app.js**
```js
// `data` will be { name: "ReactQL" }
import data from './data.json';

console.log(data.name); // <-- "ReactQL"
```

> JSON data is always bundled with the main code, and not stored in separate files - both in development and in production.
