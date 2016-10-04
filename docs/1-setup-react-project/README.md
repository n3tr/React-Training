# Setup React Project

```bash
git clone https://github.com/n3tr/sample-react-project-setup.git
npm install
npm start

# open http://localhost:3333
```

see also : https://github.com/n3tr/sample-react-project-setup

### What's inside

- React / ReactDOM
- Webpack / Webpack Dev Server
- Babel (Preset: ES2015, React)
- AirBnb ESLint

---

## or Manual Step-by-Step setup

```bash
mkdir sample-react-project
npm init
#
# name: (sample-react-project)
#...
# Is this ok? (yes)
#
ls
# package.json
```

### Dependencies

```bash
# React
npm install --save react react-dom

# Webpack both local and global
npm install --save-dev webpack webpack-dev-server
npm install -g webpack webpack-dev-server

# babel
npm install --save-dev babel-loader babel-core babel-preset-es2015 babel-preset-react
```

### Project Structure Setup

```
src/
  app.js
.babelrc
.eslintrc
package.json
webpack.config.js
index.html
```

`webpack.config.js`

    var path = require('path')

    module.exports = {
      entry: './src/app.js',
      output: {
        path: path.resolve(__dirname, "static"),
        filename: 'bundle.js'
      },
      devServer: {
        inline: true,
        port: 3333,
        path: 'static'
      },
      module: {
        loaders: [
          { test: /\.js$/, exclude: /node_modules/, loader: "babel" }
        ]
      }
    }

`index.html`

    <!doctype html>
    <html lang="en">
      <head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <title>React Sample Setup</title>
      </head>
      <body>
        <div id="root"></div>
        <script src="bundle.js"></script>
      </body>
    </html>

`.babelrc`

    {
      "presets": [ "es2015", "react" ]
    }

`app.js`

    import React from 'react'
    import ReactDOM from 'react-dom'

    // App Component
    class App extends React.Component {
      render() {
        return <h1>Hello, World!!</h1>
      }
    }

    // Render Component
    const root = document.getElementById('root')
    ReactDOM.render(<App />, root)

add script to `package.json`

```
"start": "webpack-dev-server"
```

Start by

```
webpack-dev-server
# or
npm start
```

---

## Extra

### ESLint Setup

```bash
(
  export PKG=eslint-config-airbnb;
  npm info "$PKG" peerDependencies --json | command sed 's/[\{\},]//g ; s/: /@/g' | xargs npm install --save-dev "$PKG"
)
```

Which produces and runs a command like:

```bash
npm install --save-dev eslint-config-airbnb eslint@^2.9.0 eslint-plugin-jsx-a11y@^1.2.0 eslint-plugin-import@^1.7.0 eslint-plugin-react@^5.0.1
```

`.eslintrc`

```js
{
  "extends": "airbnb"
}
```
