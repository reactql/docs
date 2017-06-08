# System requirements

---
The [ReactQL CLI](installation.md) works with most flavours of OS X, Linux and Windows.

## Development machine / in production

You'll need a version of [Node.js](https://nodejs.org) with native `async/await` (7.6+) to develop locally, and on any host that you deploy to in production (e.g. Docker.)

## In the browser

The browser bundle targets IE 11+, and all modern versions of Edge, Chrome, Safari and Firefox.

Promises, `async/await`, `fetch` and other non-native features are automatically polyfilled, so your ReactQL app should work in all browsers released over the past 3 years.
