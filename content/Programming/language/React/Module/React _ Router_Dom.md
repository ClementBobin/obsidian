## React Router DOM Cheat-Sheet

React Router DOM is a popular library for handling routing and navigation in React applications. It provides components and utilities to create a smooth and seamless user experience by managing the navigation between different pages or views. This cheat-sheet covers essential aspects of using React Router DOM in your React projects.

### Installation

1. Install React Router DOM using npm or yarn:

```bash
npm install react-router-dom
```

### Basic Setup

1. Wrap your application with the `<BrowserRouter>` component to enable routing:

```jsx
import { BrowserRouter } from 'react-router-dom';  

function App() {   
	return (     
		<BrowserRouter>       
			{/* Your application components */}     
		</BrowserRouter>   
	); 
}
```

### Creating Routes

1. Use the `<Route>` component to define routes and their corresponding components:

```jsx
import { Route } from 'react-router-dom';  

function App() {   
	return (     
		<BrowserRouter>       
			<Route path="/" exact component={Home} />       
			<Route path="/about" component={About} />       
			<Route path="/contact" component={Contact} />     
		</BrowserRouter>   
	); 
}
```

In this example, when the user navigates to `/`, the `Home` component will be rendered. Similarly, `/about` will render the `About` component, and `/contact` will render the `Contact` component.

### Navigating Between Routes

1. Use the `<Link>` component to create links for navigation:

```jsx
import { Link } from 'react-router-dom';  

function Navbar() {   
	return (     
		<nav>       
			<ul>         
				<li>           
					<Link to="/">Home</Link>         
				</li>         
				<li>           
					<Link to="/about">About</Link>         
				</li>         
				<li>           
					<Link to="/contact">Contact</Link>         
				</li>       
			</ul>     
		</nav>   
	); 
}
```

The `<Link>` component ensures that the application's navigation is handled smoothly without full-page reloads.

### Accessing Route Parameters

1. Use the `useParams()` hook to access route parameters:

```jsx
import { useParams } from 'react-router-dom';  

function UserProfile() {   
	const { username } = useParams();    
	return <h1>Welcome, {username}!</h1>; 
}
```

If the route is defined with a parameter like `/users/:username`, you can access the `username` parameter using the `useParams()` hook.

### Redirecting

1. Use the `<Redirect>` component to redirect users to a different route:

```jsx
import { Redirect } from 'react-router-dom';  

function PrivatePage() {   
	const isAuthenticated = true;    
	if (!isAuthenticated) {     
		return <Redirect to="/login" />;   
	}    return <h1>Welcome to the private page!</h1>; 
}
```

If the user is not authenticated, they will be redirected to the `/login` route.

### Nested Routes

1. Create nested routes by rendering child routes within a parent route:

```jsx
import { Route } from 'react-router-dom';  

function App() {   
	return (     
		<BrowserRouter>       
			<Route path="/" exact component={Home} />       
			<Route path="/about" component={About} />       
			<Route path="/contact" component={Contact} />       
			<Route path="/user/:userId" component={UserProfile}>         
				<Route path="/user/:userId/posts" component={UserPosts} />       
			</Route>     
		</BrowserRouter>   
	); 
}
```

In this example, the `UserProfile` component will be rendered when the route matches `/user/:userId`, and the `UserPosts` component will be rendered as a child when the route matches `/user/:userId/posts`.

### History Object

1. Access the `history` object to programmatically navigate or manipulate the browser history:

```jsx
import { useHistory } from 'react-router-dom';  

function MyComponent() {   
	const history = useHistory();    
	
	const handleButtonClick = () => {     
		history.push('/new-route');   
	};    
	
	return (     
		<div>       
			<button onClick={handleButtonClick}>Go to New Route</button>     
		</div>   
	); 
}
```

The `useHistory()` hook provides access to the `history` object, which allows you to programmatically navigate to a different route.

### Conclusion

This cheat-sheet covers the basics of using React Router DOM to handle routing and navigation in your React applications. React Router DOM provides a seamless way to create dynamic and responsive applications with multiple views and routes. For more advanced usage and additional features, refer to the official React Router DOM documentation. Happy routing!