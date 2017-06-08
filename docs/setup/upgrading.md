# Upgrading

---
Every time you run `reactql`, the tool will check the NPM repository to see if a new version is available. If it is, a message will be displayed on your console.

To upgrade the ReactQL cli tool, simply re-run the original installation command:

```bash
npm i -g reactql
```

This will grab the latest version of the `reactql` tool, and overwrite the old one.

Note: The [starter kit source code](https://github.com/reactql/kit) (and [Typescript version](https://github.com/reactql/kit)) is managed in a separate repo. The version of the kit that's installed with `react new` is hard-coded and versioned along with the CLI. To get the latest kit, bump your CLI version using `npm i -g reactql`.

> Note: There's no way to upgrade an _active_ project to the latest version, since doing so might require changes to code you've written that modifies the original starter kit. The best way to upgrade is to create a new project, copy over your custom files, and add any of your code changes manually (particularly code you may have extended inside the `kit` folder)
