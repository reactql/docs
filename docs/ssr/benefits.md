# Why use server-side rendering?

---
Server-side rendering (SSR, for short) gives your users a full HTML render of the first route they navigate to on your site.

The benefits are:

* A faster experience for your users- both perceived, and actual. Instead of waiting for your code bundles to download and get parsed by the browser's Javascript engine, the browser can render markup and styles instantly. Code is parsed whilst your user is already reading your content, speeding up the user's perception of your app's responsiveness.

* A faster experience for mobile or low-powered devices.

* Better SEO.  Whilst Google et al are getting smarter at interpreting Javascript, nothing beats serving 'raw' markup.

* A seamless experience between the server and browser. Once your initial HTML has been rendered, the client picks up where the server finishes - subsequent hyperlinks loads instantly, and the browser's own Javascript engine takes over to respond to data requests without further round-trips to the server.
