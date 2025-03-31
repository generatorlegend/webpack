# Development Guide

This guide will help you set up a development environment with webpack, including features like source maps, watch mode, and dev server integration.

## Setting Up Your Development Environment

### 1. Install webpack and webpack-cli

First, ensure you have Node.js installed on your system. Then, install webpack and webpack-cli as dev dependencies in your project:

```bash
npm install --save-dev webpack webpack-cli
```

### 2. Configure webpack

Create a `webpack.config.js` file in your project root:

```javascript
const path = require('path');

module.exports = {
  mode: 'development',
  entry: './src/index.js',
  output: {
    filename: 'bundle.js',
    path: path.resolve(__dirname, 'dist'),
  },
};
```

### 3. Enable Source Maps

Source maps help you debug your original source code in the browser. Add the following to your webpack config:

```javascript
module.exports = {
  // ... other config options
  devtool: 'inline-source-map',
};
```

## Watch Mode

Watch mode allows webpack to watch for changes in your files and recompile automatically.

### Using CLI

Run webpack with the `--watch` flag:

```bash
npx webpack --watch
```

### Using Configuration

Add the following to your webpack config:

```javascript
module.exports = {
  // ... other config options
  watch: true,
};
```

## Dev Server Integration

webpack-dev-server provides you with a simple web server and live reloading capability.

### 1. Install webpack-dev-server

```bash
npm install --save-dev webpack-dev-server
```

### 2. Configure webpack-dev-server

Add the following to your webpack config:

```javascript
module.exports = {
  // ... other config options
  devServer: {
    contentBase: './dist',
    hot: true,
  },
};
```

### 3. Run the dev server

Add a script to your `package.json`:

```json
"scripts": {
  "start": "webpack serve --open"
}
```

Then run:

```bash
npm start
```

This will start the dev server and open your default browser.

## Additional Development Tools

### 1. webpack-dev-middleware

If you're using an Express server, you can integrate webpack-dev-middleware:

```bash
npm install --save-dev webpack-dev-middleware
```

Usage example:

```javascript
const express = require('express');
const webpack = require('webpack');
const webpackDevMiddleware = require('webpack-dev-middleware');

const app = express();
const config = require('./webpack.config.js');
const compiler = webpack(config);

app.use(webpackDevMiddleware(compiler, {
  publicPath: config.output.publicPath,
}));

// Serve the files on port 3000.
app.listen(3000, function () {
  console.log('Example app listening on port 3000!\n');
});
```

### 2. Hot Module Replacement (HMR)

HMR allows modules to be updated at runtime without a full refresh. To enable HMR:

1. Add the HMR plugin to your webpack config:

```javascript
const webpack = require('webpack');

module.exports = {
  // ... other config options
  plugins: [
    new webpack.HotModuleReplacementPlugin(),
  ],
};
```

2. Update your application code to accept hot updates:

```javascript
if (module.hot) {
  module.hot.accept('./print.js', function() {
    console.log('Accepting the updated printMe module!');
    printMe();
  })
}
```

By following this guide, you should now have a solid development environment set up with webpack, including source maps, watch mode, and dev server integration. This setup will help you develop your applications more efficiently and with better debugging capabilities.