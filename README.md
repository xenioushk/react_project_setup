# react_project_setup
Steps to setup react projects

1. Initialize npm package.json file.
<code>npm init -y</code>

2. setup and install 'react' and 'react-dom'

<code>npm install react react-dom</code>

3. create a folder called "app". In this folder all the project files will be setup. create a index.html and Main.js file into the "app" folder.
4. Now, install webpack. Webpack will convert the "jsx" code syntax to regular "javascrript" code.

npm install webpack webpack-cli webpack-dev-server

5. Next, we need to create a config file called 'webpack.config.js'. Add the following lines of code into the 'webpack.config.js' file.

<code>
const path = require("path")
module.exports = {
  entry: "./app/Main.js",
  output: {
    publicPath: "/",
    path: path.resolve(__dirname, "app"),
    filename: "bundled.js",
  },
  mode: "development",
  devtool: "source-map",
  devServer: {
    port: 3000,
    static: {
      directory: path.join(__dirname, "app"),
    },
    hot: true,
    liveReload: false,
    historyApiFallback: { index: "index.html" },
  },
  module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /(node_modules)/,
        use: {
          loader: "babel-loader",
          options: {
            presets: ["@babel/preset-react", ["@babel/preset-env", { targets: { node: "12" } }]],
          },
        },
      },
    ],
  },
}
</code>

6. Now, time to install "babel" packages. 

<code> npm install @babel/core @babel/preset-dev @babel/preset-react babel-loader </code>

7. Next, go to the package.json file and add the following line of code to the "scripts" block.

<code> "dev": "webpack serve"
  
8. Finally, open the Main.js file and add following lines of code to automate the referesh proecess.
  
<code>
  
if (module.hot) {
  module.hot.accept()
}

</code>
