# HTML Sheet

## Introduction

HTML (HyperText Markup Language) is the standard markup language used for creating web pages and web applications. This cheat-sheet covers essential HTML elements and attributes to help you get started with creating web content.

## Basic Document Structure

```html
<!DOCTYPE html> 
<html> 
	<head>
		<meta charset="UTF-8" />
    		<meta name="viewport" content="width=device-width, initial-scale=1.0" />
    		<meta http-equiv="X-UA-Compatible" content="IE=edge">
		<title>Your Page Title</title> 
	</head> 
	<body>
	   <!-- Your content goes here --> 
	</body> 
</html>
```

## Document Structure Explained

- `<!DOCTYPE html>`: Declares the document type and version as HTML5.
- `<html>`: The root element of an HTML document.
- `<head>`: Contains meta-information about the document, such as title, styles, scripts, etc.
- `<title>`: Sets the title of the web page, displayed in the browser's title bar or tab.
- `<body>`: Contains the visible content of the web page.

## Headings

```html
<h1>This is a heading level 1</h1> 
<h2>This is a heading level 2</h2> 
<h3>This is a heading level 3</h3> 
<h4>This is a heading level 4</h4> 
<h5>This is a heading level 5</h5> 
<h6>This is a heading level 6</h6>
```

## Paragraphs

```html
<p>This is a paragraph. It contains text and can span multiple lines.</p>
```

## Links

```html
<a href="https://www.example.com">Visit Example Website</a>
```

## Images

```html
<img src="image.jpg" alt="Image Description">
```

## Lists

### Unordered List

```html
<ul>   
	<li>Item 1</li>   
	<li>Item 2</li>   
	<li>Item 3</li> 
</ul>
```

### Ordered List

```html
<ol>   
	<li>Item 1</li>   
	<li>Item 2</li>   
	<li>Item 3</li> 
</ol>
```

## Forms

```html
<form action="/submit" method="post">   
	<label for="name">Name:</label>   
	<input type="text" id="name" name="name" required>    
	<label for="email">Email:</label>   
	<input type="email" id="email" name="email" required>    
	<input type="submit" value="Submit"> 
</form>
```

## Tables

```html
<table>   
	<tr>     
		<th>Name</th>     
		<th>Age</th>   
	</tr>   
	<tr>     
		<td>John</td>     
		<td>30</td>   
	</tr>   
	<tr>     
		<td>Jane</td>     
		<td>25</td>   
	</tr> 
</table>
```

## Divisions

```html
<div>   <!-- Your content here --> </div>
```

## Comments

```html
<!-- This is a comment. It will not be visible on the web page. -->
```

## Special Characters

Use HTML character entities to display special characters:

- `&lt;` for `<`
- `&gt;` for `>`
- `&amp;` for `&`
- `&quot;` for `"`
- `&copy;` for ©
- `&reg;` for ®
- and more...

## Conclusion

This cheat-sheet covers the basic HTML elements and attributes to create content for web pages. As you become more proficient with HTML, you can explore [additional elements and features](https://developer.mozilla.org/fr/docs/Learn/HTML) to build more complex and interactive web pages. Happy coding with HTML!
