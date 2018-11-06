npm init
git init
.gitignore (node_modules and dist)
folders: public, src
Our public directory will handle any static assets, and most importantly houses our index.html file, which react will utilize to render your app. 

./public/index.htm (https://raw.githubusercontent.com/reactjs/reactjs.org/master/static/html/single-file-example.html)

yarn add -D @babel/core@7.1.0 @babel/cli@7.1.0 @babel/preset-env@7.1.0 @babel/preset-react@7.0.0

.babelrc

Babel also has a ton of plugins available that can be used if you only need to transform specific features or some feature you need isn’t covered by env:
https://babeljs.io/docs/plugins/

yarn add -D webpack@4.19.1 webpack-cli@3.1.1 webpack-dev-server@3.1.8 style-loader@0.23.0 css-loader@1.0.0 babel-loader@8.0.2

Webpack uses loaders to process different types of imported modules for bundling. 
It also works easily alongside the development server that we’re going to use to serve our React project in development and reload browser pages on (saved) changes to our React components. 
In order to utilize any of this though, we’ll need to configure Webpack to use our loaders and prepare the dev server

since we want to use Hot Module Replacement so we don’t have to constantly refresh to see our changes. All we do for that in terms of this file is instantiate a new instance of the plugin in the plugins property and make sure that we set hotOnly to true in devServer. We still need to set up one more thing in React before HMR works, though.

yarn add react@16.5.2 react-dom@16.5.2 -S

  "scripts": {
    "start": "webpack-dev-server --mode=development",
    "build": "webpack-dev-server --mode=production"
  },

  HMR needs to know what to actually replace and currently we haven’t given it anything. For that, we’re going to use a package one of the folks on the react team have provided us: react-hot-loader@4.3.11.

yarn add react-hot-loader@4.3.11 -S

