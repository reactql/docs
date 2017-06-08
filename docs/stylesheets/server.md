# Server-side support

---
All stylesheet flavours are fully supported on the server, so you can write your code without fear that stylesheets will break universal/server-side rendering.

In production, your styles will automatically be extracted out to a `dist/public/assets/css/style.[hash].css` and your server bundle will know the relevant 'hashed' classname to include in your `class=` attribute on your components.

This is done for you automatically - no code changes required.
