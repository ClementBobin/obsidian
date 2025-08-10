# CSS Sheet

## Introduction

CSS (Cascading Style Sheets) is a styling language used to control the presentation and layout of HTML documents. It allows developers to style elements and create visually appealing web pages. This cheat-sheet covers essential CSS concepts and properties to help you get started with styling your web pages.

## CSS Syntax

```css
selector {   
	property: value;   
	/* more properties and values */ 
}
```

- **Selector**: Selects the HTML element to style.
- **Property**: Specifies the style property to modify.
- **Value**: Sets the value of the style property.

## Applying CSS

### Inline CSS
Apply CSS directly to an HTML element using the `style` attribute:

```html
<p style="color: blue; font-size: 18px;">
	This is a paragraph with inline CSS.
</p>
```

### Internal CSS (In the `<head>` section)
Define CSS rules within the `<style>` element in the `<head>` section of your HTML:

```html
<head>   
	<style>     
		p {       
			color: blue;       
			font-size: 18px;     
		}   
	</style> 
</head>
```

### External CSS (Using a separate .css file)

Create a new file named `styles.css`:

```css
/* styles.css */ 
p {   
	color: blue;   
	font-size: 18px; 
}
```

In the `<head>` section of your HTML file, link the external CSS file:

```html
<head>   
	<link rel="stylesheet" href="styles.css"> 
</head>
```

## Selectors

### Type Selector

```css
p {   
	/* styles applied to all <p> elements */ 
}
```

### Class Selector

```css
.button {   
	/* styles applied to elements with class="button" */ 
}
```

### ID Selector

```css
#header {   
	/* styles applied to the element with id="header" */ 
}
```

### Universal Selector

```css
* {   
	/* styles applied to all elements */ 
}
```

### Descendant Selector

```css
article p {   
	/* styles applied to <p> elements inside <article> elements */ 
}
```

## Box Model

### Content Box

```css
.box {   
	width: 200px;   
	height: 100px;   
	border: 1px solid black; 
}
```

### Box with Padding

```css
.box {   
	width: 200px;   
	height: 100px;   
	padding: 20px;   
	border: 1px solid black; 
}
```

### Box with Margin

```css
.box {   
	width: 200px;   
	height: 100px;   
	margin: 20px;   
	border: 1px solid black; 
}
```

## Typography

```css
body {   
	font-family: Arial, sans-serif;   
	font-size: 16px;   
	line-height: 1.5;   
	color: #333; 
}  

h1 {   
	font-size: 32px;   
	font-weight: bold; 
}  

p {   
	font-size: 18px; 
}
```

## Colors

```css
.element {   
	color: #ff0000; /* Red */   
	background-color: #f0f0f0; /* Light gray */ 
}
```

## Background

```css
.element {   
	background-image: url("image.jpg");   
	background-color: #f0f0f0;   
	background-size: cover;   
	background-repeat: no-repeat;   
	background-position: center; 
}
```

## Display and Positioning

```css
/* Display */ 
.element {   
	display: block; /* or inline, inline-block, flex, etc. */ 
}  

/* Positioning */ 
.element {   
	position: relative; /* or absolute, fixed, static */   
	top: 10px;   
	left: 20px;   
	z-index: 1; 
}
```

## Flexbox

```css
.container {   
	display: flex;   
	justify-content: center; /* or flex-start, flex-end, space-between, space-around */   
	align-items: center; /* or flex-start, flex-end, center, stretch */ 
}
```

## Media Queries

```css
/* For screens with a width less than 600px */ 
@media (max-width: 600px) {   
	.element {     
		font-size: 14px;   
	} 
}
```

## Transitions and Animations

```css
/* Transitions */ 
.element {   
	transition: all 0.3s ease; /* property duration timing-function */ 
}  

.element:hover {
	background-color: #ff0000; 
}  


/* Keyframe Animations */ 
@keyframes fadeIn {
	from {
		opacity: 0;   
	}   to {     
		opacity: 1;   
	} 
}  

.element {   
	animation: fadeIn 2s ease-in-out infinite; 
}
```

## Conclusion

This cheat-sheet covers essential CSS concepts and properties to help you style your web pages. As you continue working with CSS, you'll [discover more](https://devdocs.io/css/) advanced features and techniques to create beautiful and