# PHP Sheet

## Introduction

PHP is a server-side scripting language designed for web development. It is widely used to create dynamic and interactive web applications. This cheat-sheet covers essential PHP syntax and concepts to help you get started with PHP.

## Installation

To use PHP, you need to have it installed on your web server. Follow these steps to install PHP:

### Windows

1. Download PHP from the official website: [https://windows.php.net/download/](https://windows.php.net/download/)
2. Extract the downloaded files to a directory of your choice.
3. Add the PHP directory to your system's PATH environment variable.

### macOS

PHP comes pre-installed on macOS. You can check the installed version using the terminal:

```bash
php -v
```

### Linux (Ubuntu)

1. Install PHP using the package manager:

```php
sudo apt update sudo apt install php
```

## Running PHP Code

1. Create a new PHP file with the `.php` extension (e.g., `index.php`).
2. Add your PHP code inside the file.

To run the PHP code, you have several options:

### Using a Web Server:

Place the PHP file in your web server's document root (e.g., `/var/www/html`) and access it through a web browser.

### Using PHP Built-in Server:

Open the terminal, navigate to the directory containing the PHP file, and run:

```bash
php -S localhost:8000
```

Then, access the PHP file in your browser at [`localhost:8000`](http://localhost:8000).

### Using Command-Line Interpreter:

Open the terminal, navigate to the directory containing the PHP file, and run:

```bash 
php your_file.php
```

## Basic PHP Syntax

### Variables

```php
$name = "John"; 
$age = 30;
```

### Output

```php
echo "Hello, World!";
```

### Strings

```php
$name = "John"; 
$message = "Hello, $name!";
```


### Arrays

```php
$fruits = array("Apple", "Banana", "Orange");
```

### Conditionals

```php
if ($age >= 18) {    
	echo "You are an adult."; 
} elseif ($age >= 13) {     
	echo "You are a teenager."; 
} else {     
	echo "You are a child."; 
}
```

### Loops

```php
for ($i = 1; $i <= 5; $i++) {     
	echo "$i "; 
}  while ($x <= 10) {     
	echo "$x ";     $x++; 
}
```

### Functions

```php
function greet($name) {     
	echo "Hello, $name!"; 
}  

greet("John");
```

## Working with Forms

### HTML Form

```html
<form action="process_form.php" method="post">   
	<input type="text" name="username" placeholder="Username">   
	<input type="password" name="password" placeholder="Password">   
	<input type="submit" value="Submit"> 
</form>
```

### Processing Form Data

```php
// process_form.php  
if ($_SERVER["REQUEST_METHOD"] == "POST") {     
	$username = $_POST["username"];     
	$password = $_POST["password"];      
	// Perform validation and further processing 
}
```

## Working with Databases

### Connecting to MySQL Database

```php
$servername = "localhost"; 
$username = "db_user"; 
$password = "db_password"; 
$dbname = "database_name";  

$conn = new mysqli($servername, $username, $password, $dbname);  
if ($conn->connect_error) {     
	die("Connection failed: " . $conn->connect_error); 
}
```

### Querying Data

```php
$sql = "SELECT * FROM users"; 
$result = $conn->query($sql);  

if ($result->num_rows > 0) {     
	while ($row = $result->fetch_assoc()) {         
		echo "Name: " . $row["name"] . " - Email: " . $row["email"] . "<br>";
	} 
} else {     
	echo "0 results"; 
}
```
### Basic SQL Database Operations

#### Add Data

```php
$sql = "INSERT INTO table_name (column1, column2, column3) VALUES ('value1', 'value2', 'value3')"; 
if ($conn->query($sql) === TRUE) {     
	echo "New record created successfully"; 
} else {     
	echo "Error: " . $sql . "<br>" . $conn->error; 
}
```

#### Change Data

```php
$sql = "UPDATE table_name SET column1='new_value1' WHERE condition"; 
if ($conn->query($sql) === TRUE) {     
	echo "Record updated successfully"; 
} else {     
	echo "Error updating record: " . $conn->error; 
}
```

#### Check Data

```php
$sql = "SELECT * FROM table_name WHERE condition"; 
$result = $conn->query($sql);  
if ($result->num_rows > 0) {     
	// Output data 
} else {     
	echo "0 results"; 
}
```

#### Delete Data

```PHP
$sql = "DELETE FROM table_name WHERE condition"; 
if ($conn->query($sql) === TRUE) {     
	echo "Record deleted successfully"; 
} else {     
	echo "Error deleting record: " . $conn->error; 
}
```

#### Get Data

```php
$sql = "SELECT * FROM table_name"; 
$result = $conn->query($sql);  
if ($result->num_rows > 0) {     
	while($row = $result->fetch_assoc()) {         
		// Output data     
	} 
} else {     
	echo "0 results"; 
}
```
## Conclusion

This cheat-sheet covers the basic usage and syntax of PHP for web development. PHP is a powerful language that allows you to create dynamic and interactive web applications. As you become more comfortable with PHP, you can explore its extensive [documentation](https://www.php.net/docs.php) for more advanced features and functionalities. Happy coding with PHP!