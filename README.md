# Webpack-4-with-React-and-Sass
A workflow template starter using the newest Webpack 4 with React with ES6 binding features and SASS with no running server.

Strictly for Front-end use.

```src folder``` is where you write your code.
```public folder``` is where files compiled by Webpack.

```package.json``` contains following run scripts and library modules:
```
"scripts": {
  "dev": "webpack -w --mode development",
  "build": "webpack --mode production",
  "test": "echo \"Error: no test specified\" && exit 1"
},
"devDependencies": {
  "babel-core": "^6.26.0",
  "babel-loader": "^7.1.3",
  "babel-preset-env": "^1.6.1",
  "babel-preset-es2015": "^6.24.1",
  "babel-preset-react": "^6.24.1",
  "babel-preset-stage-1": "^6.24.1",
  "css-loader": "^0.28.10",
  "extract-text-webpack-plugin": "^4.0.0-beta.0",
  "html-loader": "^0.5.5",
  "html-webpack-plugin": "^3.0.1",
  "node-sass": "^4.7.2",
  "react": "^16.2.0",
  "react-dom": "^16.2.0",
  "sass-loader": "^6.0.6",
  "style-loader": "^0.20.2",
  "webpack": "^4.0.1",
  "webpack-cli": "^2.0.9"
}
```

```webpack.config.js``` :

```
const HtmlWebPackPlugin = require("html-webpack-plugin");
const ExtractTextPlugin = require('extract-text-webpack-plugin');
const path = require('path');

module.exports = {
  entry: './src/app.js',
  output: {
    filename: 'bundle.js',
    path: path.resolve(__dirname, './public')
  },
  module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /node_modules/,
        use: {
          loader: "babel-loader"
        }
      }, {
        test: /\.(s*)css$/,
        use: ExtractTextPlugin.extract({
          fallback: 'style-loader',
          use: ['css-loader', 'sass-loader']
        })
      }, {
        test: /\.html$/,
        use: [
          {
            loader: "html-loader",
            options: {
              minimize: true
            }
          }
        ]
      }
    ]
  },
  plugins: [
    new HtmlWebPackPlugin({template: "./src/index.html"}),
    new ExtractTextPlugin({filename: 'app.bundle.css'})
  ]
};
```

```.babelrc``` :
```
{
  "presets": ["env","es2015", "react", "stage-1"]
}

```
