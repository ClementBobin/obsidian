# JavaScript Sheet

## Introduction

JavaScript is a high-level, interpreted programming language used for web development. It allows developers to create interactive and dynamic web pages. This cheat-sheet covers essential JavaScript concepts and syntax to help you get started with writing JavaScript code.

## Variables and Data Types

```js
// Variable declaration 
let age = 30;  // Data Types 
let name = "John"; // String 
let isStudent = true; // Boolean 
let score = null; // Null
let person = { name: "John", age: 30 }; // Object 
let fruits = ["Apple", "Banana", "Orange"]; // Array
```

## Operators

```js
let x = 10; let y = 5;  

// Arithmetic Operators 
let sum = x + y;
let difference = x - y; 
let product = x * y; 
let quotient = x / y; 
let remainder = x % y;  

// Assignment Operators 
x += y; // x = x + y;
x -= y; // x = x - y;
x *= y; // x = x * y;
x /= y; // x = x / y; 

// Comparison Operators 
let isEqual = x === y; 
let isNotEqual = x !== y; 
let isGreater = x > y; 
let isLess = x < y; 
let isGreaterOrEqual = x >= y; 
let isLessOrEqual = x <= y;  

// Logical Operators 
let isTrue = true; 
let isFalse = false;
let logicalAnd = isTrue && isFalse; // false 
let logicalOr = isTrue || isFalse; // true 
let logicalNot = !isTrue; // false
```

## Conditional Statements

```js
let age = 18;

if (age >= 18) {   
	console.log("You are an adult."); 
} else if (age >= 13) {   
	console.log("You are a teenager."); 
} else {   
	console.log("You are a child."); 
}
```

## Loops

```js
//For Loop 
for (let i = 0; i < 5; i++) 
{   
	console.log(i); 
}  

//While Loop 
let count = 0; 
while (count < 5) {   
	console.log(count);   
	count++; 
}  

//Do-While Loop
let num = 1; 
do {   
	console.log(num);
	num++;
} while (num <= 5);  

//For...of Loop (for arrays) 
let fruits = ["Apple", "Banana", "Orange"]; 
for (let fruit of fruits) {
	console.log(fruit); 
}  

//For...in Loop (for objects)
let person = { name: "John", age: 30 };
for (let key in person) {
	console.log(key + ": " + person[key]); 
}
```

## Functions

```js
// Function Declaration 
function greet(name) {   
	return "Hello, " + name + "!"; 
}  

let greeting = greet("John"); 
console.log(greeting);  

// Arrow Function
const add = (a, b) => a + b; 
let sum = add(2, 3); 
console.log(sum);
```

## Arrays

```js
let fruits = ["Apple", "Banana", "Orange"];  

// Accessing Elements 

console.log(fruits[0]); // Apple  

// Modifying Elements 

fruits[1] = "Mango";  


// Array Methods 
let length = fruits.length; 

let lastIndex = fruits.length - 1; 

fruits.push("Grapes"); // Add an element to the end 

let lastFruit = fruits.pop(); // Remove the last element 

fruits.unshift("Kiwi"); // Add an element to the beginning 

let firstFruit = fruits.shift(); // Remove the first element 

let indexOrange = fruits.indexOf("Orange"); // Find index of an element 

let citrusFruits = fruits.slice(1, 3); // Extract elements from index 1 to 2 (not including 3)
```

## Objects

```js
let person = {   name: "John",   age: 30,   isStudent: true, };  
// Accessing Properties 
console.log(person.name); // John  

// Modifying Properties 
person.age = 35;  

// Adding Properties 
person.city = "New York";  

// Deleting Properties 
delete person.isStudent;
```

## DOM Manipulation

```html
<!DOCTYPE html> 
<html> 
	<body>   
		<h1 id="title">Hello, World!</h1>   
		<button onclick="changeTitle()">Change Title</button>    
		<script>     
			function changeTitle() {
				document.getElementById("title").innerHTML = "New Title";     
			}   
		</script> 
	</body> 
</html>
```

## Events

```html
<!DOCTYPE html> 
<html> 
	<body>   
		<button id="btn">Click Me</button>    
		<script>     
			const button = document.getElementById("btn");
			
			button.addEventListener("click", () => {
				alert("Button Clicked!");     
			});   
		</script> 
	</body> 
</html>
```

## Conclusion

This cheat-sheet covers the fundamental concepts and syntax of JavaScript. JavaScript is a versatile language that can be used for various applications, including web development, server-side scripting, and more. As you continue [learning JavaScript](https://devdocs.io/javascript/), explore its extensive features and capabilities to create powerful and interactive web applications. Happy coding with JavaScript!