# Running a ReactQL project

ReactQL can be run in several 'modes':

- **[Development](development.md)**. When coding locally, a Webpack dev server will spawn on [localhost:8080](http://localhost:8080), offer you 'hot code reload' upon save, instantly reflecting changes in the browser. A development web server will also rebuild and restart upon save (on [localhost:8081](http://localhost:8081)), allowing you to test [server-side rendering](/ssr/README.md) on-the-fly.

- **[Production](production.md)**.  Assets are minified, optimised and compressed, ready for production.  The web server can be deployed to a host or a [Docker instance](/bundling/docker.md), and serve your production traffic.

- **[Static](static.md)**. If you don't want/need server-side rendering, you can choose to build a static bundle that can be uploaded to Github Pages, S3 or any other static host -- no web server required.
