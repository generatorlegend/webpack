# Configuration Options

Webpack provides a wide range of configuration options to customize your build process. This document outlines the available options, their purpose, and usage examples.

## Table of Contents

1. [Entry](#entry)
2. [Output](#output)
3. [Module](#module)
4. [Resolve](#resolve)
5. [Optimization](#optimization)
6. [Performance](#performance)
7. [DevTool](#devtool)
8. [Target](#target)
9. [Experiments](#experiments)
10. [Cache](#cache)
11. [Node](#node)
12. [Externals](#externals)

## Entry

The `entry` option defines the entry point(s) of your application. It can be a string, an array, or an object.

Example:

```javascript
module.exports = {
  entry: './src/index.js'
};
```

## Output

The `output` option specifies how and where webpack should output your bundles, assets, and anything else.

Example:

```javascript
const path = require('path');

module.exports = {
  output: {
    filename: 'bundle.js',
    path: path.resolve(__dirname, 'dist')
  }
};
```

### Important Output Options

- `filename`: Specifies the name of each output bundle.
- `path`: The output directory as an absolute path.
- `publicPath`: The public URL of the output directory when referenced in a browser.

## Module

The `module` option determines how different types of modules within a project will be treated.

Example:

```javascript
module.exports = {
  module: {
    rules: [
      {
        test: /\.css$/,
        use: ['style-loader', 'css-loader']
      }
    ]
  }
};
```

## Resolve

The `resolve` option configures how webpack resolves modules.

Example:

```javascript
module.exports = {
  resolve: {
    extensions: ['.js', '.json', '.jsx'],
    alias: {
      '@': path.resolve(__dirname, 'src')
    }
  }
};
```

## Optimization

The `optimization` option allows you to customize the webpack build optimization.

Example:

```javascript
module.exports = {
  optimization: {
    minimize: true,
    splitChunks: {
      chunks: 'all'
    }
  }
};
```

## Performance

The `performance` option sets hints for file sizes and entrypoint sizes.

Example:

```javascript
module.exports = {
  performance: {
    hints: 'warning',
    maxAssetSize: 200000,
    maxEntrypointSize: 400000
  }
};
```

## DevTool

The `devtool` option controls if and how source maps are generated.

Example:

```javascript
module.exports = {
  devtool: 'source-map'
};
```

## Target

The `target` option tells webpack the environment in which the bundle will run.

Example:

```javascript
module.exports = {
  target: 'web'
};
```

## Experiments

The `experiments` option enables experimental features in webpack.

Example:

```javascript
module.exports = {
  experiments: {
    asyncWebAssembly: true,
    topLevelAwait: true
  }
};
```

## Cache

The `cache` option enables in-memory caching for faster rebuilds.

Example:

```javascript
module.exports = {
  cache: {
    type: 'filesystem'
  }
};
```

## Node

The `node` option configures polyfills or mocks for various Node.js globals and modules.

Example:

```javascript
module.exports = {
  node: {
    global: false,
    __filename: false,
    __dirname: false
  }
};
```

## Externals

The `externals` option allows you to exclude dependencies from the output bundles.

Example:

```javascript
module.exports = {
  externals: {
    jquery: 'jQuery'
  }
};
```

This document provides an overview of the main configuration options available in webpack. For more detailed information and advanced usage, please refer to the official webpack documentation.