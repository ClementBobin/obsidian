## Introduction

React is a [JavaScript](Javascript.md) library developed by Facebook for building user interfaces. It allows developers to create reusable UI components and manage the state of the application efficiently. This cheat-sheet covers the essential concepts and syntax for getting started with React.

## Installation

To use React, you need to set up a new project using a package manager like npm (Node Package Manager) or yarn. Follow these steps to create a new [React project](Vite.md):

### Using npm:

```bash
npm init react-app your-app-name cd your-app-name npm start
```

### Using yarn:

```bash 
yarn create react-app your-app-name cd your-app-name yarn start
```

This will create a new **React project** with the necessary files and start a development server.

## Components

Components are the building blocks of React applications. There are two types of components: Functional Components and Class Components.

### Functional Component

```React
import React from 'react';  

const FunctionalComponent = () => {   
	return (     
		<div>       
			<h1>Hello, I am a Functional Component!</h1>     
		</div>   
	); 
};  

export default FunctionalComponent;
```

### Class Component

```React
import React, { Component } from 'react';

class ClassComponent extends Component {   
	render() {     
		return (       
			<div>         
				<h1>Hello, I am a Class Component!</h1>       
			</div>     
		);   
	} 
}  

export default ClassComponent;
```

## Props

Props (short for properties) are used to pass data from a parent component to a child component. Props are read-only and cannot be modified by the child component.

```React
import React from 'react';

const Greeting = (props) => {   
	return (     
		<div>       
			<h1>Hello, {props.name}!</h1>     
		</div>   
	); 
};  

export default Greeting;
```

Usage:

```React
import React from 'react'; 
import Greeting from './Greeting';  

const App = () => {   
	return (     
		<div>       
			<Greeting name="John" />     
		</div>   
	); 
};  

export default App;
```

## State

State is used to manage data that can change over time within a component. Only class components can have state.

```React
import React, { Component } from 'react';

class Counter extends Component {
	constructor(props) {
	    super(props);     
	    this.state = {       
		    count: 0,     
		};   
	}    
	incrementCount = () => {     
		this.setState({ count: this.state.count + 1 });
    };    
    
    render() {     
	    return (       
		    <div>         
			    <h1>Count: {this.state.count}</h1>         
			    <button onClick={this.incrementCount}>Increment</button>
			</div>     
		);   
	} 
}  

export default Counter;
```

## Lifecycle Methods

Lifecycle methods are methods that get called at various stages of a component's lifecycle. Some commonly used lifecycle methods include:

### componentDidMount

This method is called after the component has been rendered to the screen. It is commonly used to fetch data from an API or perform other side effects.

```React
componentDidMount() {   // Fetch data from API }
```

### componentDidUpdate

This method is called after the component's state or props have been updated. It is useful for performing actions based on changes in the component.

```React
componentDidUpdate(prevProps, prevState) {   // Perform actions based on changes in props or state }
```

### componentWillUnmount

This method is called right before the component is removed from the DOM. It is used to perform cleanup tasks, such as canceling timers or cleaning up subscriptions.

```React
componentWillUnmount() {   // Cleanup tasks }
```

## Event Handling

You can handle events in React using event handlers:

```React
import React, { useState } from 'react';

const Counter = () => {   

	const [count, setCount] = useState(0);    
	const incrementCount = () => {     setCount(count + 1);   };    
	
	return (     
		<div>       
			<h1>Count: {count}</h1>       
			<button onClick={incrementCount}>Increment</button>     
		</div>   
	); 
};  

export default Counter;
```

## Conditional Rendering

You can conditionally render components or elements based on certain conditions using ternary operators or `if` statements:

```React
import React from 'react';

const Greeting = ({ isLoggedIn }) => {   
	return isLoggedIn ? <h1>Hello, User!</h1> : <h1>Hello, Guest!</h1>; 
};  

export default Greeting;
```

## Lists and Keys

You can render lists of elements in React using `.map()` and provide a unique `key` to each item:

```React
import React from 'react';  

const ListExample = ({ items }) => {   
	return (     
		<ul>       
			{items.map((item) => (
		         <li key={item.id}>{item.name}</li>       
		    ))}     
		</ul>   
	); 
};  

export default ListExample;
```

## Styling

You can apply styles to React components using inline styles or CSS classes:

```React
import React from 'react';

const StyledComponent = () => {   
	const styles = {     
		color: 'blue',     
		fontSize: '18px',
    };    
    
    return <div style={styles}>Hello, I am styled!</div>; 
};  

export default StyledComponent;
```

```React
import React from 'react'; 
import './App.css';  

const App = () => {   
	return <div className="app">Hello, React!</div>;
};  

export default App;
```

This is just a brief overview of the fundamental concepts and syntax in React. React has many more features and functionalities to explore. For more detailed information and advanced usage, refer to the official [React documentation](https://react.dev/learn). Happy coding!