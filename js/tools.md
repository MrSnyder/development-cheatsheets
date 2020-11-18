# Tools

[What are NPM, Yarn, Babel, and Webpack; and how to properly use them?](https://medium.com/front-end-weekly/what-are-npm-yarn-babel-and-webpack-and-how-to-properly-use-them-d835a758f987)

## npm

npm is a package manager for Node.js

* Config file: ``package.json``
* Module folder: ``node_modules``
* package.json: Dependencies, Skripte, Metadaten
* node_modules
* node_modules/.bin
* dependencies
* devDependencies

```bash
# create initial package.json
npm init
```

## Webpack

Webpack is a static module bundler for modern JavaScript applications.

* Creates bundles (most notably of JS files)
* Default config file: ``webpack.config.js``
* Entry: Defines the files to bundle / watch
* Output: Tells webpack where to emit the bundles it creates and how to name these file
* Loader: (Babel, compress images, etc)
* Treeshaking: Remove redundant / unused variables / functions

## Chrome

* Find resources by content: F12 -> Network -> Looking glass
