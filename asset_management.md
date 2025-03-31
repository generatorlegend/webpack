# Asset Management

Webpack is not only capable of bundling JavaScript, but it can also handle various types of assets such as images, fonts, and stylesheets. This guide explains how webpack manages these assets and how you can configure asset management in your project.

## Asset Modules

Webpack 5 introduces Asset Modules, which allow you to use asset files (fonts, icons, etc.) without configuring additional loaders.

There are four types of asset modules:

1. `asset/resource`: Emits a separate file and exports the URL.
2. `asset/inline`: Exports a data URI of the asset.
3. `asset/source`: Exports the source code of the asset.
4. `asset`: Automatically chooses between `asset/resource` and `asset/inline` based on file size.

### Basic Usage

To use Asset Modules, add the appropriate `type` to the module rule:

```javascript
module.exports = {
  module: {
    rules: [
      {
        test: /\.(png|jpg|gif)$/i,
        type: 'asset/resource'
      }
    ]
  }
};
```

### Custom Output Filename

You can customize the output filename of asset modules using the `assetModuleFilename` option in the output configuration:

```javascript
module.exports = {
  output: {
    assetModuleFilename: 'images/[hash][ext][query]'
  }
};
```

### Inlining Assets

To inline assets as data URIs, use the `asset/inline` type:

```javascript
module.exports = {
  module: {
    rules: [
      {
        test: /\.(png|jpg|gif)$/i,
        type: 'asset/inline'
      }
    ]
  }
};
```

### Exporting Source Code

To export the source code of an asset, use the `asset/source` type:

```javascript
module.exports = {
  module: {
    rules: [
      {
        test: /\.txt$/i,
        type: 'asset/source'
      }
    ]
  }
};
```

### General Asset Type

The `asset` type automatically chooses between `asset/resource` and `asset/inline` based on file size:

```javascript
module.exports = {
  module: {
    rules: [
      {
        test: /\.(png|jpg|gif)$/i,
        type: 'asset',
        parser: {
          dataUrlCondition: {
            maxSize: 8 * 1024 // 8kb
          }
        }
      }
    ]
  }
};
```

## URL Handling in CSS

Webpack can handle URLs in your CSS files. When you use `url()` in your CSS, webpack will treat it as a dependency and resolve it.

To enable this feature, use the `css-loader`:

```javascript
module.exports = {
  module: {
    rules: [
      {
        test: /\.css$/i,
        use: ['style-loader', 'css-loader']
      }
    ]
  }
};
```

## Loading Fonts

You can use Asset Modules to handle font files:

```javascript
module.exports = {
  module: {
    rules: [
      {
        test: /\.(woff|woff2|eot|ttf|otf)$/i,
        type: 'asset/resource'
      }
    ]
  }
};
```

## Loading Data

Webpack supports importing JSON files out of the box. To import other data formats like CSV, XML, etc., you can use specific loaders:

```javascript
module.exports = {
  module: {
    rules: [
      {
        test: /\.(csv|tsv)$/i,
        use: ['csv-loader']
      },
      {
        test: /\.xml$/i,
        use: ['xml-loader']
      }
    ]
  }
};
```

## Conclusion

Webpack's asset management capabilities allow you to handle various types of assets in your project efficiently. By using Asset Modules and appropriate loaders, you can streamline your build process and optimize your application's performance.

Remember to consider file size, caching strategies, and performance implications when working with assets in your webpack configuration.