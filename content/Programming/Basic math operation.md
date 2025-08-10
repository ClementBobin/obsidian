```cpp
// C++ Class 
#include <cmath>  

class MathOperations { 
	public:     
		int add(int a, int b) {         
			return a + b;     
		}          
		int subtract(int a, int b) {         
			return a - b;     
		}          
		int multiply(int a, int b) {         
			return a * b;     
		}          
		double divide(double a, double b) {         
			if (b != 0) {             
				return a / b;         
			} else {             
				throw "Division by zero";         
			}     
		}          
		double squareRoot(double num) {         
			return std::sqrt(num);     
		}          
		double exponent(double base, double power) {         
			return std::pow(base, power);     
		} 
		int modulus(int a, int b) { 
			return a % b; 
		} 
		double absoluteValue(double num) { 
			return std::abs(num); 
		} 
		double floor(double num) { 
			return std::floor(num); 
		} 
		double ceil(double num) { 
			return std::ceil(num); 
		} 
		double max(double a, double b) { 
			return std::max(a, b); 
		} 
		double min(double a, double b) { 
			return std::min(a, b); 
		}
};
```

```C#
// C# Class 
using System;  

class MathOperations {     
	public int Add(int a, int b) {         
		return a + b;     
	}          
	public int Subtract(int a, int b) {         
		return a - b;     
	}          
	public int Multiply(int a, int b) {         
		return a * b;     
	}          
	public double Divide(double a, double b) {         
		if (b != 0) {             
			return a / b;         
		} else {             
			throw new DivideByZeroException("Division by zero");         
		}     
	}          
	public double SquareRoot(double num) {         
		return Math.Sqrt(num);     
	}          
	public double Exponent(double baseNum, double power) {        
		return Math.Pow(baseNum, power);     
	} 
	public int Modulus(int a, int b) { 
		return a % b; 
	} 
	public double AbsoluteValue(double num) { 
		return Math.Abs(num); 
	} 
	public double Floor(double num) { 
		return Math.Floor(num); 
	} 
	public double Ceiling(double num) { 
		return Math.Ceiling(num); 
	} 
	public double Max(double a, double b) { 
		return Math.Max(a, b); 
	} 
	public double Min(double a, double b) { 
		return Math.Min(a, b); 
	}
}
```

```python
# Python Class 
import math  

class MathOperations:     
	def add(self, a, b):         
		return a + b          
	def subtract(self, a, b):         
		return a - b          
	def multiply(self, a, b):         
		return a * b          
	def divide(self, a, b):         
		if b != 0:             
			return a / b         
		else:             
			raise ZeroDivisionError("Division by zero")          
	def square_root(self, num):         
		return math.sqrt(num)          
	def exponent(self, base, power):         
		return math.pow(base, power)
	def modulus(self, a, b): 
		return a % b 
	def absolute_value(self, num): 
		return abs(num) 
	def floor(self, num): 
		return math.floor(num) 
	def ceil(self, num): 
		return math.ceil(num) 
	def max(self, a, b): 
		return max(a, b) 
	def min(self, a, b): 
		return min(a, b)
```

```javascript
// JavaScript Class 
class MathOperations {     
	add(a, b) {         
		return a + b;     
	}      
	subtract(a, b) {         
		return a - b;     
	}      
	multiply(a, b) {         
		return a * b;     
	}      
	divide(a, b) {         
		if (b !== 0) {             
			return a / b;         
		} else {             
			throw new Error("Division by zero");         
		}     
	}      
	squareRoot(num) {         
		return Math.sqrt(num);     
	}      
	exponent(base, power) {         
		return Math.pow(base, power);     
	} 
	modulus(a, b) { 
		return a % b; 
	} 
	absoluteValue(num) { 
		return Math.abs(num); 
	} 
	floor(num) { 
		return Math.floor(num); 
	} 
	ceil(num) { 
		return Math.ceil(num); 
	} 
	max(a, b) { 
		return Math.max(a, b); 
	} 
	min(a, b) { 
		return Math.min(a, b); 
	}
}
```

```ts
// TypeScript Class 
class MathOperations {     
	add(a: number, b: number): number {         
		return a + b;     
	}      
	subtract(a: number, b: number): number {         
		return a - b;     
	}      
	multiply(a: number, b: number): number {         
		return a * b;     
	}      
	divide(a: number, b: number): number {         
		if (b !== 0) {             
			return a / b;         
		} else {             
			throw new Error("Division by zero");         
		}     
	}      
	squareRoot(num: number): number {         
		return Math.sqrt(num);     
	}      
	exponent(base: number, power: number): number {         
		return Math.pow(base, power);     
	} 
	modulus(a: number, b: number): number { 
		return a % b; 
	} 
	absoluteValue(num: number): number { 
		return Math.abs(num); 
	} 
	floor(num: number): number { 
		return Math.floor(num); 
	} 
	ceil(num: number): number { 
		return Math.ceil(num); 
	} 
	max(a: number, b: number): number { 
		return Math.max(a, b); 
	} 
	min(a: number, b: number): number { 
		return Math.min(a, b); 
	}
}
```

```java
// Java Class 
public class MathOperations {     
	public int add(int a, int b) {         
		return a + b;     
	}      
	public int subtract(int a, int b) {         
		return a - b;     
	}      
	public int multiply(int a, int b) {         
		return a * b;     
	}      
	public double divide(double a, double b) {         
		if (b != 0) {             
			return a / b;         
		} else {             
			throw new ArithmeticException("Division by zero");         
		}     
	}      
	public double squareRoot(double num) {         
		return Math.sqrt(num);     
	}      
	public double exponent(double base, double power) {         
		return Math.pow(base, power);     
	}
	public int modulus(int a, int b) { 
		return a % b; 
	} 
	public double absoluteValue(double num) { 
		return Math.abs(num); 
	} 
	public double floor(double num) { 
		return Math.floor(num); 
	} 
	public double ceil(double num) { 
		return Math.ceil(num); 
	} 
	public double max(double a, double b) { 
		return Math.max(a, b); 
	} 
	public double min(double a, double b) { 
		return Math.min(a, b); 
	} 
}
```

Feel free to use these classes in your programming projects to perform various math operations in each of the mentioned programming languages.