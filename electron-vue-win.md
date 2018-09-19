# Electron with Webpack and VueJS

## Summary

1. Requirements
2. Install
3. Configure
4. How to use
5. Update
6. References

## Requirements

* NodeJS (https://nodejs.org/)
* NPM (https://www.npmjs.com/)
* Atom (https://atom.io)


## Install

* Create the project directory
```
mkdir [project-name]
cd [project-name]
```

* start the npm project
```
npm init
```

* install dependencies
```
npm install electron webpack electron-webpack vue vue-loader vue-template-compiler electron-builder --save-dev
npm install source-map-support --save
```

* still inside your project's directory, create the following folders
```
mkdir src\main src\renderer
```


* create the following files:
```
echo .> webpack.config.js
echo .> src\index.html
echo .> src\main\index.js
echo .> src\renderer\index.js
echo .> src\renderer\App.vue
```


* open atom from the project's directory
```
atom .
```


* content of "webpack.config.js"
```js
const VueLoaderPlugin = require('vue-loader/lib/plugin')
module.exports = {
  module: {
    rules: [
      {
        test: /\.vue$/,
        use: 'vue-loader'
      }
    ]
  },
  plugins: [
    new VueLoaderPlugin()
  ]
}
```


* content of "src\index.html"
```html
<!DOCTYPE html>
<html>
  <head>
    <title><%= process.env.npm_package_productName %></title>
    <meta charset="utf-8">
    <script>
      <% if (htmlWebpackPlugin.options.nodeModules) { %>
        require('module').globalPaths.push(
          '<%= htmlWebpackPlugin.options.nodeModules %>'.replace(/\\/g, '\\\\'),
        )
      <% } %>
      require('source-map-support/source-map-support.js').install()
    </script>
  </head>
  <body>
    <div id="app"></div>
  </body>
</html>
```


* content "src\main\index.js"
```js
import { app, BrowserWindow } from 'electron'
import path from 'path'
import { format as formatUrl } from 'url'

const isDevelopment = process.env.NODE_ENV !== 'production'

app.on('ready', () => {
  let window = new BrowserWindow({
    width: 1024
  })
  if (isDevelopment) {
    window.loadURL(`http://localhost:${process.env.ELECTRON_WEBPACK_WDS_PORT}`)
  } else {
    window.loadURL(formatUrl({
      pathname: path.join(__dirname, 'index.html'),
      protocol: 'file',
      slashes: true
    }))
  }
  window.on("closed", () => {
    window = null;
  })
})

app.on("window-all-closed", () => {
  if (process.platform !== "darwin") {
    app.quit();
  }
})
```


* content "src\renderer\index.js"
```js
import Vue from 'vue'
import App from './App.vue'

new Vue({
  el: '#app',
  render(h) {
    return h(App)
  }
})
```


* content "src\renderer\App.vue"
```vue
<template>
  <div class="">
    <h1>{{name}}</h1>
  </div>
</template>

<script>
export default {
  data(){
    return {
      name: 'Application'
    }
  }
}
</script>

<style lang="css">
</style>
```

* edit "package.json"
```json
"scripts": {
    "start": "electron-webpack dev",
    "build": "electron-webpack && electron-builder"
  },
```

## How to use

* Run the Application on dev mode
```
npm start
```

* Build the Application
```
npm run build
```


## Update

[empty]


## References

### Electron with webpack and Vue.js
https://www.youtube.com/watch?v=oL7vIDkDOsg
