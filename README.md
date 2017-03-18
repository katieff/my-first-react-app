# my-first-react-app

This is a project example set up for a react app.

## Prerequisites

You only need to have installed node and npm.

## Set up on your own

First you need to initialiaze the project:

```
mkdir my-first-react-app
cd my-first-react-app
npm init
```

Our App will only have two basic files `app.js` and `index.html` in a src folder:

```javascript
console.log('Hello World!');
```
```html
<!DOCTYPE html>
<html>
<head>
  <title>My first react app</title>
  <meta charset="utf-8">
</head>
<body>
  <h1>Hello</h1>
  <div id="app">
  </div>
</body>
</html>
```


Then you need to add the webpack2 and a the html-webpack-plugin dependencies:

```
npm install --save-dev webpack webpack-dev-server
npm install --save-dev html-webpack-plugin
```

webpack also needs a configuration file:

```
touch webpack.config.js
```

And we add the following:

```javascript
module.exports = {
    context: __dirname + "/src",
    entry: "./app.js",
    output: {
        filename: "my-first-react-app.js",
        path: __dirname + "/dist"
    },
    plugins: [new HtmlWebpackPlugin({
        template: "./index.html"
    })]
};
```

Now we insert two script command into the package.json:

```json
...
"scripts": {
    ...,
    "webpack": "webpack -d",
    "start": "webpack-dev-server --hot --contentBase dist"
  },
  ...
```

Now we can run from the console
```
npm run webpack
```

And we should have a dist folder which includes our `my-first-react-app.js` and `index.html`.

When executing `npm run start`a node server starts and when opening `http://localhost:8081/` in a browser of your choice you should see the title.
