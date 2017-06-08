# Building a Docker image

Deploying your project as a [Docker](https://www.docker.com/) container offers you a self-contained web server that can quickly scale out with container management platforms such as [Kubernetes](https://kubernetes.io/), [Rancher](http://rancher.com/), or via any Docker host.

Every ReactQL project ships with a default [Dockerfile](https://github.com/reactql/kit/blob/master/Dockerfile), that can be used to quickly build an image with the usual Docker build command:

`docker build . -t your_project`

To run your project, issue this command:

`docker run -p 4000:4000 your_project`

... which will spawn your production web server on `http://[docker_host_ip]:4000`

# Custom host/port

By default, your project will bind to the container's **0.0.0.0** interface on port **4000**. This means it will be accessible to every device on your network that can connect to the Docker-assigned container IP.

To specify an override host/port, you can use the regular environment variables:

`docker run -e SERVER_PROD_HOST=127.0.0.1 -e SERVER_PROD_PORT=8000 reactql`

# Caching / speeding up build times

The [Dockerfile](https://github.com/reactql/kit/blob/master/Dockerfile) first checks whether `package.json` has changed since the last build, before installing the necessary C compilers and other binary support packages, building `node_modules`, and cleaning up after itself.

After binary packages have been used and uninstalled, it then proceeds to copy over your project source code, and internally run the `npm run build` command to generate the distribution assets for production.

Since you'll likely make edits to your source code at a greater frequency than NPM changes, this speeds up subsequent Docker builds by caching previous build steps, essentially only copying over new source code and re-running the NPM build script.

The first time you build the Docker image and/or change `package.json`, expect the process to take at least 10-15 minutes. Source code changes thereafter should generally re-build in 30 seconds or less.

# Technical details

The Dockerfile extends [debian:jessie-slim](https://hub.docker.com/_/debian/).  This significantly cuts down on the filesize versus more comprehensive distro builds, without giving up the GNU C compilers needed to build binary packages in `node_modules`.

The Node version bundled is currently **8.0.0**.

The built image weighs in at **~349 MB**, including your project files, built NPM packages, and distribution code &mdash; compared with over 600MB from 'just' Node from the [official v8.0.0 tag](https://hub.docker.com/_/node/).
