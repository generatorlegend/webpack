---
title: Getting Started with webpack
description: Learn how to install webpack, create a basic configuration, and run your first build.
---

# Getting Started with webpack

This guide will help you get started with webpack, including installation, basic configuration, and running your first build.

## Prerequisites

Before you begin, make sure you have [Node.js](https://nodejs.org/) installed on your system.

## Installation

To install webpack and its command-line interface (CLI), run the following command in your project directory:

```bash
npm install webpack webpack-cli --save-dev
```

## Basic Configuration

Create a file named `webpack.config.js` in the root of your project directory with the following content:

```javascript
const path = require('path');

module.exports = {
  entry: './src/index.js',
  output: {
    filename: 'main.js',
    path: path.resolve(__dirname, 'dist'),
  },
};
```

This configuration specifies:
- The entry point of your application (`./src/index.js`)
- The output file name (`main.js`)
- The output directory (`dist`)

## Creating Your First Bundle

1. Create a `src` directory in your project root.
2. Inside the `src` directory, create an `index.js` file with some sample code:

```javascript
console.log('Hello, webpack!');
```

3. Add a script to your `package.json` file to run webpack:

```json
{
  "scripts": {
    "build": "webpack"
  }
}
```

4. Run the build command:

```bash
npm run build
```

webpack will create a `dist` directory with a `main.js` file containing your bundled code.

## Running Your Build

To test your bundle, create an `index.html` file in your project root:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>webpack Demo</title>
  </head>
  <body>
    <script src="dist/main.js"></script>
  </body>
</html>
```

Open this HTML file in a web browser, and you should see "Hello, webpack!" in the console.

## Next Steps

Now that you have a basic webpack setup, you can explore more advanced features such as:

- Loaders for processing different file types
- Plugins for extending webpack's functionality
- Code splitting for optimizing your bundle
- Development server for a smoother development experience

Check out the [webpack documentation](https://webpack.js.org/concepts/) for more detailed information on these topics and more.