# App Setup

This page will go over setting up a React application. If you would like a reference, or want a template for a project with all the setup complete, you can find it at [this link.](https://github.com/CityOfLangford/react_template)

## [Webpack](https://webpack.js.org/)

Webpack is a module bundler. Essentially, it packages all your project's JavaScript and its dependencies into a minified bundle for deployement. Additionally, through the use of loaders and plugins, you can transform the output to be in a from consumable by browsers, a feature very much desired for React applications.

As Webpack attempts to orchestrate the whole build pipeline, it can become combersome to configure in big applications.

To install webpack and the needed tools we can run the following command:

```bash
npm i -D webpack webpack-cli webpack-dev-server style-loader css-loader copy-webpack-plugin
```

We can now create a `webpack.config.js` file with the following configuration.

**Note**: This configuration needs to be a JavaScript file to support the import of plugins.

```js
const path = require("path");
const CopyPlugin = require("copy-webpack-plugin");
const ESLintPlugin = require("eslint-webpack-plugin");

module.exports = {
  mode: "production",
  entry: "./src/index.js",
  output: {
    path: path.resolve(__dirname, "dist"),
    filename: "bundle.js",
  },
  module: {
    rules: [
      {
        test: /\.js$/i,
        include: path.resolve(__dirname, "src"),
        use: {
          loader: "babel-loader",
        },
      },
      {
        test: /\.css$/i,
        include: path.resolve(__dirname, "src"),
        use: ["style-loader", "css-loader", "postcss-loader"],
      },
    ],
  },
  plugins: [
    new ESLintPlugin({ quiet: true }),
    new CopyPlugin({
      patterns: [{ from: "public" }],
    }),
  ],
  devServer: {
    liveReload: true,
  },
};
```

This configuration is a coalescense of many different configurations and work arounds so it is rather unique to this project. Below are some helpful, blogs on similar setups:

- https://medium.com/geekculture/setting-up-a-react-app-from-scratch-withwebpack-babel-and-eslint-57eb3dcaf2e9

- https://medium.com/age-of-awareness/setup-react-with-webpack-and-babel-5114a14a47e9

## [ESLint](https://eslint.org/)

Much like the API, the React app also needs a custom ESLint config to operate correctly and smoothly with our environment. In this config, we are extending ESLint with a selection of plugins/presets for React and React Hooks. Additionally, we need to enable browser features, and tell ESLint to be compatible with JSX.

First we need to install the dependencies:

```bash
npm i -D eslint eslint-plugin-react eslint-plugin-react-hooks eslint-webpack-plugin
```

Now we can create a `.eslintrc` file with the following configuration.

```json
{
  "extends": [
    "eslint:recommended",
    "plugin:react/recommended",
    "plugin:react-hooks/recommended"
  ],
  "parserOptions": {
    "sourceType": "module",
    "allowImportExportEverywhere": false,
    "ecmaFeatures": {
      "globalReturn": false,
      "jsx": true
    }
  },
  "env": {
    "es2021": true,
    "browser": true,
    "node": true
  },
  "plugins": ["react", "react-hooks"],
  "rules": {
    "react/jsx-uses-react": "error",
    "react/jsx-uses-vars": "error",
    "react/react-in-jsx-scope": "off",
    "no-unused-vars": 0,
    "react/prop-types": 0
    // "react/exhaustive-deps": 1
  }
}
```

The rules section of the configuration can be customized as needed. Here I have set up a few that work with my workflow and the current environment.

Unlike in the API when ESLint can just be called by Nodemon, with Webpack we need a plugin to have it run in the pipeline. To do this we use the eslint-webpack-plugin. This can be added to the Webpack config as follows:

```js
const ESLintPlugin = require("eslint-webpack-plugin");
// more imports
module.exports{
    // webpack config
    plugins: [
        //other plugins
        new ESLintPlugin({ quiet: true }),
    ]
}
```

## [Babel](https://babeljs.io/)

In order to transform JSX and React into JavaScript readable by the browser we need Babel. For this configuration we are going to babel presets for React and an additional one for runtime transforms.

To install Babel and its loader and plugins we can run the following commands:

```bash
npm i -D @babel/core @babel/plugin-transform-runtime @babel/preset-env babel-loader @babel/preset-react
```

We need to install a build dependency for our runtime configuration to work. For some JavaScript features, an extended runtime is required and is not provided by default. Therefore we need to include a extended runtime and tell Babel to use it instead of the default

```bash
npm i @babel/runtime
```

To configure Babel we can create a `.babelrc` file with the following configuration.

```json
{
  "presets": [
    "@babel/preset-env",
    ["@babel/preset-react", { "runtime": "automatic" }]
  ],
  "plugins": ["@babel/plugin-transform-runtime"]
}
```

## Other

### [Tailwindcss](https://tailwindcss.com/)

Tailwindcss is a CSS utility library that I have grown fond of over the past year. Tailwind is unopinionated in its approach in that, it does not pre-style things, or provide a set of styles for you to choose from. Instead, it "classifies" CSS properties, allowing you to manage your styling by simply modifying the classes of a HTML or JSX element. This minimizes the need for 95% of all CSS in a project and enables greater reusability of styling. Additionally, it auto purges all unused styles so that the bundle contains only those styles you use/resuse.

```jsx
<div className="w-10 h-10 rounded-full">This is a circle</div>
```

This solution does evidently require more time to style than if you were to use Bootstrap for example. However, the simplicity of the library allows you to customize your styling way beyond what Bootstrap is capable of.

If you choose to use TailwindCSS, I reccomend looking at their excellent [documentation](https://tailwindcss.com/docs) for installation instructions.

### [Bootstrap](https://getbootstrap.com/)

Bootstrap is arguably the most used CSS framework out there currently. It is also used in the Timesheet! Bootstrap defines a certain styling for various elements and they can be applied through classes or, in the case of the Timesheet, through a JSX library of pre styled components.
