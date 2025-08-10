# Vite framework for React

## Introduction

Vite is a fast build tool and development server that is designed to work with modern frontend frameworks like React, Vue, and others. It aims to provide a quick development experience by leveraging native ES modules in the browser. This cheat-sheet covers the essential commands and configurations for setting up a React project using Vite.

## Installation

To create a new React project with Vite, you need to have Node.js installed on your system. Follow these steps to set up a new React project:

### Using npm:

```bash
npm create vite@latest
```
Or:

```bash
npm init @vitejs/app your-app-name --template react cd your-app-name npm install
```

### Using yarn:

```bash
yarn create @vitejs/app your-app-name --template react cd your-app-name yarn
```

## Development Server

To start the development server and run your React app, use the following command:

```bash
npm run dev
```

or

```bash
yarn dev
```

This will launch the development server, and your app will be accessible at [`localhost:3000`](http://localhost:3000).

## Building for Production

To build your React app for production, use the following command:

```bash
npm run build
```

or

```bash
yarn build
```

This will generate optimized and minified files for deployment in the `dist` folder.

## Configuration

Vite allows you to customize your project's configuration by creating a `vite.config.js` file in the root directory of your project. Here's an example configuration:

```js
// vite.config.js 
export default {   
	// Customize the base URL for deployment (default is '/')   
	base: '/your-app-name/',    
	// Customize the output directory (default is 'dist')   
	outDir: 'build',    
	// Enable or disable CSS modules (default is true)   
	css: {     modules: true,   },
    // Configure the development server   
    server: {     port: 3000,   },    
    // Configure additional plugins   
    plugins: [], 
};
```

## Environment Variables

Vite supports loading environment variables using the `.env` files. Create an `.env` file in the root directory of your project, and use it to define environment-specific variables:


```env
// .env 
VITE_API_BASE_URL=https://api.example.com 
VITE_APP_TITLE=My React App
```

You can then access these variables in your code using `import.meta.env`:

```js
// src/App.js 
const apiUrl = import.meta.env.VITE_API_BASE_URL; 
const appTitle = import.meta.env.VITE_APP_TITLE;
```


## Importing Modules

Vite supports native ES module imports, allowing you to import modules using the `import` statement in your code:

```js
// src/App.js 
import React from 'react'; 
import ReactDOM from 'react-dom'; 
import App from './App';  

ReactDOM.render(<App />, document.getElementById('root'));
```


## Hot Module Replacement (HMR)

Vite provides Hot Module Replacement, which allows your changes to be updated in the browser without a full page reload during development. This helps in faster development and debugging:

```js
// src/App.js 
import React from 'react';  

const App = () => {   
	return <h1>Hello, React with Vite!</h1>; 
};  

export default App;
```


## CSS Preprocessors

Vite supports CSS preprocessors like Sass, Less, and Stylus out of the box. Simply install the desired preprocessor and use it in your code:

```bash
npm install -D sass
```

```js
// src/App.sass 
$primary-color: blue;  h1 {   color: $primary-color; }
```

## Conclusion

This cheat-sheet covers the basic usage and configurations for setting up a React project using Vite. Vite's fast development server, native ES module support, and other features make it a great choice for building modern React applications.

For more detailed information and advanced usage, refer to the official [Vite documentation](https://vitejs.dev/guide/). Happy coding with React and Vite!