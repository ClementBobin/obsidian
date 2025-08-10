Writing comments in code is a common practice to provide explanations and context. However, the idea of "Don't Write Comments" suggests that code should be self-explanatory and well-organized enough to eliminate the need for excessive comments. While comments can be valuable, over-reliance on them may indicate code that lacks clarity, maintainability, or proper structuring.

# Key Points:

1. **Self-Documenting Code:** Aim to write code that is clear and understandable without the need for extensive comments. Well-named variables, functions, and classes contribute to self-documenting code.
    
2. **Code Readability:** Code should read like a narrative, making it easy for other developers (including your future self) to understand its purpose and functionality.
    
3. **Comments as Clarity Indicators:** Comments should focus on explaining complex algorithms, edge cases, and non-obvious behavior rather than describing what obvious code is doing.
    
4. **Maintenance Challenges:** Excessive comments can become outdated when code evolves, leading to confusion and misinformation.
    
5. **Refactor for Clarity:** Instead of adding comments to clarify confusing code, consider refactoring the code to make it more intuitive.
    
6. **Use Comments Sparingly:** Use comments only when necessary and when they genuinely add value. Avoid repetitive or redundant comments.
    

# Examples:

1. **Avoid:**
    
```js
// Calculate total price 
let totalPrice = quantity * price;
```
    
2. **Preferred:**
    
    ```js
let totalPrice = quantity * price;
```
    
3. **Avoid:**
    
    ```js
// Loop through the array and find the largest element 
for (let i = 0; i < arr.length; i++) {     
	if (arr[i] > largest) {         
		largest = arr[i];     
	} 
}
```
    
4. **Preferred:**
    
    ```js
for (let i = 0; i < arr.length; i++) {     
	if (arr[i] > largest) {         
		largest = arr[i]; // Update the largest element     
	} 
}
```
    

# Guidelines for Using Comments:

1. **Explain Why, Not What:** Focus on explaining the reasoning, decisions, and nuances behind the code rather than explaining the obvious.
2. **Complex Algorithms:** Use comments to provide insights into complex algorithms or mathematical calculations.
3. **Edge Cases:** Comment on edge cases or exceptional scenarios that might not be immediately obvious from the code.
4. **TODOs and FIXMEs:** Use comments to indicate areas that need attention or improvements (e.g., `// TODO: Refactor this code`).
5. **Documentation:** Document public APIs, functions, and classes to guide other developers in using your code.

# Benefits of Minimal Comments:

1. **Faster Understanding:** Developers can quickly understand and navigate through code that is self-explanatory.
2. **Reduced Maintenance:** Code changes are less likely to introduce inconsistencies between comments and code behavior.
3. **Simpler Refactoring:** Refactoring becomes easier when code is clean and expressive.

# Drawbacks of Excessive Comments:

1. **Outdated Comments:** Comments may become outdated over time as code evolves, leading to confusion.
2. **Clutter:** Too many comments can clutter the code and make it harder to read.
3. **Lack of Focus:** Excessive comments can divert attention from the actual logic of the code.

# Conclusion:

While comments can be valuable for explaining complex concepts or non-obvious behavior, the principle of "Don't Write Comments" encourages developers to prioritize writing clean, self-explanatory code. Focus on code readability, meaningful variable names, and proper structuring to make comments unnecessary or minimal. When used thoughtfully, comments can enhance understanding and maintenance without cluttering the codebase.

# Out Source
![Don't Write Comments](https://www.youtube.com/watch?v=Bf7vDBBOBUA)