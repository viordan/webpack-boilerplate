# webpack-boilerplate

> Contains webpack, babble, css-loader, file-loader.  


> To install run $npm install

---

## package.json

```javascript

{
  "name": "webpack-boilerplate",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "dev": "webpack --mode development",
    "build": "webpack --mode production"
  },
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "@babel/core": "^7.8.4",
    "@babel/preset-env": "^7.8.4",
    "babel-loader": "^8.0.6",
    "css-loader": "^3.4.2",
    "file-loader": "^5.0.2",
    "html-webpack-plugin": "^3.2.0",
    "style-loader": "^1.1.3",
    "webpack": "^4.30.0",
    "webpack-cli": "^3.3.0"
  }
}
```

## webpack.config.json

```javascript

const HtmlWebpackPlugin = require("html-webpack-plugin");
const path = require('path');

module.exports = {
    entry: './src/index.js',
    output: {
        filename: '[name].bundle.js',
        path: path.resolve(__dirname, 'dist')
    },
    module: {
        rules: [
            {
                test: /\.(png|jpe?g|gif)$/i,
                loader: 'file-loader',
                options: {
                  outputPath: 'images',
                },
              },
            {
                test: /\.css$/,
                use: [{ loader: 'style-loader' }, { loader: 'css-loader' }],
            },
            {
                test: /\.js$/,
                exclude: /node_modules/,
                use: {
                    loader: 'babel-loader',
                        options: {
                        presets: ['@babel/preset-env']
                    }
                }
            }
        ]
    },
    plugins: [
        new HtmlWebpackPlugin({
        title: "webpack-boilerplate",
        }),
    ],
};
```

Modified from https://www.sitepoint.com/webpack-beginner-guide/
