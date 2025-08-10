# JavaScript Arrays  
Arrays in JavaScript are versatile data structures that can hold multiple values. Each value is referred to as an element, and elements are accessed by their index.  
## Creating an Array  
Arrays in JavaScript can be created using array literals or the `Array()` constructor.  
### Using Array Literals  
```js
javascript const fruits = ['apple', 'banana', 'cherry'];
```

### Using Array Constructor

```js
const fruits = new Array('apple', 'banana', 'cherry');
```

## Accessing Elements

Array elements can be accessed using their index. JavaScript uses zero-based indexing.

```js
const fruits = ['apple', 'banana', 'cherry'];  
console.log(fruits[0]); // Output: 'apple' 
console.log(fruits[1]); // Output: 'banana'
```

## Modifying Elements

You can modify array elements by assigning a new value to a specific index.

```js
const fruits = ['apple', 'banana', 'cherry'];  
fruits[1] = 'orange'; 
console.log(fruits); // Output: ['apple', 'orange', 'cherry']
```

## Array Properties and Methods

JavaScript provides several properties and methods to work with arrays:

### Properties

- **`length`**: Returns the number of elements in the array.

```js
const fruits = ['apple', 'banana', 'cherry']; 
console.log(fruits.length); // Output: 3
```

### Methods

- **`push()`**: Adds one or more elements to the end of the array and returns the new length.

```js
const fruits = ['apple', 'banana']; 
fruits.push('cherry'); 
console.log(fruits); // Output: ['apple', 'banana', 'cherry']
```

- **`pop()`**: Removes the last element from the array and returns that element.

```js
const fruits = ['apple', 'banana', 'cherry']; 
const lastFruit = fruits.pop(); 
console.log(lastFruit); // Output: 'cherry' 
console.log(fruits); // Output: ['apple', 'banana']
```

- **`shift()`**: Removes the first element from the array and returns that element.

```js
const fruits = ['apple', 'banana', 'cherry']; 
const firstFruit = fruits.shift(); 
console.log(firstFruit); // Output: 'apple' 
console.log(fruits); // Output: ['banana', 'cherry']
```

- **`unshift()`**: Adds one or more elements to the beginning of the array and returns the new length.

```js
const fruits = ['banana', 'cherry']; 
fruits.unshift('apple'); 
console.log(fruits); // Output: ['apple', 'banana', 'cherry']
```

## Custom Array Function

You can also define custom functions to work with arrays. For example, here's a function `array_diff` that computes the difference between two arrays:

```js
function array_diff(a, b) {   
	return a.filter(e => !b.includes(e)); 
}  

const arr1 = [1, 2, 3, 4]; 
const arr2 = [2, 4];  
const diff = array_diff(arr1, arr2); 
console.log(diff); // Output: [1, 3]
```

And here's a function `array_intersection` that computes the similarity or intersection between two arrays:


```js
function array_intersection(a, b) {   
	return a.filter(e => b.includes(e)); 
}  

const arr1 = [1, 2, 3, 4]; 
const arr2 = [2, 4, 5];  
const intersection = array_intersection(arr1, arr2); 
console.log(intersection); // Output: [2, 4]
```

## Custom Array Function for Non-Consecutive Elements

Here's a function `firstNonConsecutive` that returns the first non-consecutive element in an array:

```js
function firstNonConsecutive(arr) {   
	for (let i = 0; i < arr.length - 1; ++i) {     
		if (arr[i] + 1 !== arr[i + 1]) {       
			return arr[i + 1];     
		}   
	}   
	return null; 
}  

const numbers = [1, 2, 3, 5, 6]; console.log(firstNonConsecutive(numbers)); // Output: 5
```

## Custom Array Prototype Function

You can extend the `Array.prototype` to add custom functions that can be used with any array. For example, here's a function `myUcase` that converts all array elements to uppercase:

```js
Array.prototype.myUcase = function() {   
	for (let i = 0; i < this.length; i++) {     
		this[i] = this[i].toUpperCase();   
	} 
};
```

Now, you can use `myUcase` on any array:

```js
const fruits = ['apple', 'banana', 'cherry']; 
fruits.myUcase(); 
console.log(fruits); // Output: ['APPLE', 'BANANA', 'CHERRY']
```

## Finding the Sum of Two Smallest Numbers in an Array

To find the sum of the two smallest numbers in an array, you can use the following approach:

```JS
function sumOfTwoSmallestNumbers(arr) {   
	const numbers = arr.slice(); // Copy the array to avoid modifying the original   
	
	numbers.sort(function(a, b) {     
		return a - b;   
	});   
	
	return numbers[0] + numbers[1]; 
}  

const arr = [10, 5, 3, 8, 1]; 
const sumOfTwoSmallest = sumOfTwoSmallestNumbers(arr); 
console.log(sumOfTwoSmallest); // Output: 4
```

In this function, we create a copy of the original array using `arr.slice()` to avoid modifying the original array. We then sort the copy in ascending order and return the sum of the first two elements.

## Finding the Sum of Two Highest Numbers in an Array

To find the sum of the two highest numbers in an array, you can use the following approach:

```js
function sumOfTwoHighestNumbers(arr) {   
	const numbers = arr.slice(); // Copy the array to avoid modifying the original   
	numbers.sort(function(a, b) {     
		return b - a;   
	});   
	return numbers[0] + numbers[1]; 
}  

const arr = [10, 5, 3, 8, 1]; 
const sumOfTwoHighest = sumOfTwoHighestNumbers(arr); 
console.log(sumOfTwoHighest); // Output: 18
```
## Compact (without safety)

```js
function sumTwoSmallestNumbers(numbers){  
  numbers = numbers.sort(function(a, b){return a - b; });
  return numbers[0] + numbers[1];
};
```
```js
function sumTwoSmallestNumbers(numbers){  
  numbers = numbers.sort(function(a, b){return b - a; });
  return numbers[0] + numbers[1];
};
```
## Finding the Sum of Two Highest Numbers in an Array

To find the sum of the two highest numbers in an array, you can use the following approach:

```js
function sumOfTwoHighestNumbers(arr) {   
	const numbers = arr.slice(); // Copy the array to avoid modifying the original   
	numbers.sort(function(a, b) {     
		return b - a;   
	});   
	return numbers[0] + numbers[1]; 
}  

const arr = [10, 5, 3, 8, 1]; 
const sumOfTwoHighest = sumOfTwoHighestNumbers(arr); 
console.log(sumOfTwoHighest); // Output: 18
```

In this function, we create a copy of the original array using `arr.slice()` to avoid modifying the original array. We then sort the copy in descending order and return the sum of the first two elements.
## Conclusion

JavaScript arrays are fundamental data structures that allow you to store and manipulate collections of elements. Understanding how to create, access, modify, and utilize array properties and methods is essential for effective programming in JavaScript.

This markdown provides an overview of creating arrays, accessing and modifying elements, and using properties and methods available in JavaScript arrays. Feel free to modify and expand upon it as needed.