## React.js - installation

This guide is based on the assumption that Node.js is already installed. To install Node.js: 
https://nodejs.org/en/download/package-manager/

1. In terminal, cd to the local repo.
2. Type 
	`npm init`
3. Enter
	`npm i --save react`
4. Enter
	`npm i --save react-dom`
5. Install _babel_ as a dev (only needed in the development phase, not in the production phase). Enter
	`npm i --save-dev babel-core babel-loader babel-preset-react`
6. Optionally: 
	`npm i --save-dev babel-preset-es2015`

### Configure _babel_ manually
1. Make sure you're in the root directory of the project.
2. Create a new file and name it `.babelrc` without any prefix.
3. In the .babelrc file, type
	`{ presets: ['react'] }`

### Install _webpack_ module as dev
1. Install _webpack_ (manages the processes that convert React code into code that the browser can use).
	`npm i --save-dev webpack webpack-dev-server html-webpack-plugin`
2. Make sure you're in the root directory of the project.
3. Create a new file and name it `webpack.config.js`.

### Configure the _webpack.config.js_ file
1. Example directory and file names: `app`, `transformed.js`, `build` (adjust the name and path as necessary). 
2. In this file, you need to instruct the _babel_ loader to process all .js files of the React app, *excluding* the React code as such and to configure the HTMLWebpackPlugin.
3. In the _webpack.config.js_ file type at the very top:
	```const HTMLWebpackPlugin = require('html-webpack-plugin');
	const HTMLWebpackPluginConfig = new HTMLWebpackPlugin({
	template: __dirname + '/app/index.html',    // the filepath the main .html file
	filename: 'index.html',                     // the resulting .html file in the build folder
	inject: 'body'	                             // specify where the resulting JS script will go so that it can be loaded.
	});		                             // The script can go in the header or body. Placing it in the body improves loading speed.
	
	module.exports = {
	entry: __dirname + '/app/index.js',
	module: { loaders: [
	{
	test: /\.js$/, 
	exclude: /node_modules/,
	loader: 'babel-loader'
	}] 
	},
	output: {
	filename: 'transformed.js',	
	path: __dirname + '/build'
	},
	plugins: [HTMLWebpackPluginConfig]	
	};

### Add your scripts to the package.json 
1. To run _webpack_, you need to type `npm run build` in the command line. Similarly, to start the local server, you need to type `npm run start` or `npm start` in the terminal. For these commands to execute, you need to include the scripts in the project's _package.json_ file.
2. Open the _package.json_ file and replace the contents of the `scripts` object with the following:
	```scripts: {
		build: 'webpack',
		start: 'webpack-dev-server'
		}
### Create the main .html file
1. In the _app_ folder, create an `index.html` file. Both the main *.html* file and the entry file should be located in the same folder. 
2. In the main *.html* file, specify the path to the entry file. If the folder is named `app`, in the _index.html_ file type
	`<script src="./index.js"></script>`

### Require React and the relevent modules in the _app/index.js_ file:

	const React = require('react');
	const ReactDOM = require('react-dom');
	const App = require('./components/App');  // Specify the path to the App.js file that lives in the project's _app/components_ folder. 
	
	ReactDOM.render(
	<App />, 
	document.getElementById('app')
	);
    
3. The component class that you will include in _App.js_ will be rendered by ReactDom. 
4. The App.js needs to require React at the top and the component class it will contain needs to be exported with `module.exports` at the very bottom of the file.
5. Once the App.js has a React component, build the file in terminal with 
    `npm run build`.
    
### Sources
https://www.twilio.com/blog/2015/08/setting-up-react-for-es6-with-webpack-and-babel-2.html

https://www.codecademy.com/articles/react-setup-v

https://www.tutorialspoint.com/reactjs/reactjs_environment_setup.htm
