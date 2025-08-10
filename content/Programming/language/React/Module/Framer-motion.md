## Framer Motion Cheat-Sheet

Framer Motion is a popular animation library for React that allows you to create smooth and interactive animations for your web applications. It provides an easy-to-use API to animate React components and elements with various effects. This cheat-sheet covers essential aspects of using Framer Motion to add animations to your React projects.

### Installation

1. Install Framer Motion using npm or yarn:

```bash
npm install framer-motion
```

### Basic Usage

1. Wrap your component with the `motion` higher-order component (HOC) to enable animations:

```jsx
import { motion } from 'framer-motion';  

const MyComponent = () => {   
	return (     
		<motion.div>       
			{/* Your animated content */}     
		</motion.div>   
	); 
};
```

### Animating Properties

1. Use Framer Motion's `animate` prop to apply animation to a property:

```jsx
import { motion } from 'framer-motion';  

const MyComponent = () => {   
	return (     
		<motion.div       
			initial={{ opacity: 0 }}       
			animate={{ opacity: 1 }}       
			transition={{ duration: 1 }}     
		>       
			Animated Content     
		</motion.div>   
	); 
};
```

In this example, the `opacity` property of the element is animated from 0 to 1 with a duration of 1 second.

### Variants

1. Define animation variants using the `variants` object and apply them to elements:

```jsx
import { motion } from 'framer-motion';  

const variants = {   
	hidden: { opacity: 0, scale: 0 },   visible: { opacity: 1, scale: 1 }, 
};  

const MyComponent = () => {   
	return (     
		<motion.div       
			variants={variants}       
			initial="hidden"       
			animate="visible"       
			transition={{ duration: 1 }}>     	      
			Animated Content     
		</motion.div>   
	); 
};
```

The `variants` object defines two states - `hidden` and `visible`. The `initial` state is set to `hidden`, and the `animate` state is set to `visible`.

### Interactivity

1. Use Framer Motion's `whileHover` and `whileTap` props to add interactivity:

```jsx
import { motion } from 'framer-motion';  

const MyComponent = () => {   
	return (     
		<motion.button       
			whileHover={{ scale: 1.2 }}       
			whileTap={{ scale: 0.8 }}>       
			Click Me     
		</motion.button>   
	); 
};
```

In this example, the button scales up by 20% on hover and scales down by 20% on tap.

### Chaining Animations

1. Chain multiple animations using the `animate` prop and the `transition` object:

```jsx
import { motion } from 'framer-motion';  

const MyComponent = () => {   
	return (     
		<motion.div       
			animate={{ x: 100, opacity: 0 }}       
			transition={{ duration: 1 }}       
			onAnimationComplete={() => console.log('Animation completed!')}>       
			Chained Animation     
		</motion.div>   
	); 
};
```

In this example, the element moves 100 pixels to the right and fades out simultaneously with a duration of 1 second. The `onAnimationComplete` callback is triggered when the animation is completed.

### Keyframes

1. Create custom keyframes for animation sequences using the `keyframes` prop:

```jsx
import { motion } from 'framer-motion';  

const MyComponent = () => {   
	return (     
		<motion.div       
			keyframes={[         
				{ opacity: 1, scale: 1 },         
				{ opacity: 0, scale: 0 },         
				{ opacity: 1, scale: 1 },       
			]}       
			transition={{ duration: 2, loop: Infinity }}>       
			Keyframe Animation     
		</motion.div>   
	); 
};
```

The element will go through the specified keyframes in the given order, creating an animation loop.

### Conclusion

This cheat-sheet covers the basics of using Framer Motion to add smooth and interactive animations to your React projects. Framer Motion's intuitive API makes it easy to animate components and elements with various effects. For more advanced usage and additional animation options, refer to the official Framer Motion documentation. Happy animating!