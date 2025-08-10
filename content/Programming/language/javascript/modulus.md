# Modulus Operator in JavaScript  
The modulus operator (`%`) in programming gives the remainder of a division operation. It's often used to determine if a number is even or odd.  
## Modulus Operator (`%`)  
In JavaScript, the modulus operator (`%`) calculates the remainder of a division operation. For example, `a % b` returns the remainder when `a` is divided by `b`.  

```javascript 
const remainder = 10 % 3; // The remainder of 10 divided by 3 is 1 
console.log(remainder); // Output: 1
```

## Determining Even or Odd

The modulus operator is commonly used to determine if a number is even or odd. When a number is divided by 2, if the remainder is 0, the number is even; if the remainder is 1, the number is odd.

Here's a JavaScript function that determines whether a given number is even or odd using the modulus operator:

```js
function even_or_odd(number) {   
	return number % 2 ? "Odd" : "Even"; 
}  
console.log(even_or_odd(4)); // Output: Even 
console.log(even_or_odd(7)); // Output: Odd
```

In this function, `number % 2` calculates the remainder when `number` is divided by `2`. If the remainder is `0`, it returns `"Even"`, indicating that the number is even. If the remainder is `1`, it returns `"Odd"`, indicating that the number is odd.

## Custom Function `mango`

Here's a custom JavaScript function `mango` that calculates the price for a given quantity of mangoes, considering a special deal of buying 3 mangoes for the price of 2:

```js
function mango(quantity, price) {   
	return price * (quantity - Math.floor(quantity / 3)); 
}  

const totalCost = mango(5, 2); // Buying 5 mangoes at $2 each 
console.log(totalCost); // Output: 8 (2 mangoes at full price + 3 mangoes at discounted price)
```

In this function, `mango(quantity, price)` calculates the total cost of buying `quantity` mangoes at a given `price` per mango, considering the special deal of 3 mangoes for the price of 2.

This markdown explains the modulus operator in JavaScript, provides an example of how to use the modulus operator to determine even or odd numbers, and includes a JavaScript function (`even_or_odd`) that utilizes the modulus operator to determine whether a number is even or odd. Additionally, it introduces a custom JavaScript function (`mango`) that calculates the price for a given quantity of mangoes with a special discount offer.