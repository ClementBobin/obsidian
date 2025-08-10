# Arithmetic Operations

Binary coding involves performing arithmetic operations on binary numbers, just like in decimal arithmetic. Here are some common arithmetic operations in binary:

1. **Binary Addition:**
    
    - 0 + 0 = 0
    - 0 + 1 = 1
    - 1 + 0 = 1
    - 1 + 1 = 0 (carry 1)
    ![](addition%20binaire.jpg)
2. **Binary Subtraction:**
    
    - 0 - 0 = 0
    - 0 - 1 = 1 (borrow 1)
    - 1 - 0 = 1
    - 1 - 1 = 0
3. **Binary Multiplication:**
    
    - Multiplying two binary digits involves bitwise AND and shifting.
4. **Binary Division:**
    
    - Dividing two binary digits involves bitwise division and shifting.

# Logical Operations

Logical operations manipulate individual bits in binary numbers:

1. **AND (Logical AND):**
    
    - 0 AND 0 = 0
    - 0 AND 1 = 0
    - 1 AND 0 = 0
    - 1 AND 1 = 1
    ![](logique%20and%20binaire.jpg)
2. **OR (Logical OR):**
    
    - 0 OR 0 = 0
    - 0 OR 1 = 1
    - 1 OR 0 = 1
    - 1 OR 1 = 1
3. **NOT (Logical NOT):**
    
    - NOT 0 = 1
    - NOT 1 = 0
4. **XOR (Exclusive OR):**
    
    - 0 XOR 0 = 0
    - 0 XOR 1 = 1
    - 1 XOR 0 = 1
    - 1 XOR 1 = 0

# Signed Numbers

In binary, numbers can be represented as signed or unsigned. Signed numbers use the leftmost bit (the most significant bit) as the sign bit:

- **Positive Numbers:** The leftmost bit is 0. The remaining bits represent the magnitude of the number.
- **Negative Numbers (Two's Complement):** The leftmost bit is 1. To represent negative numbers using two's complement:
    1. Invert all bits (change 0 to 1 and vice versa).
    2. Add 1 to the inverted number.

| bit de signe | sequence | resultat |
| ----------- | --------- | -------- |
| 0 | 1 1 1 1 1 1 1 | 127 |
| 0 | 0 0 0 0 0 1 0 | 2 |
| 0 | 0 0 0 0 0 0 1 | 1 |
| 0 | 0 0 0 0 0 0 0 | 0 |
| 1 | 1 1 1 1 1 1 1 | -1 |
| 1 | 1 1 1 1 1 1 0 | -2 |
| 1 | 0 0 0 0 0 0 1 | -127 |
| 1 | 0 0 0 0 0 0 0 | -128 |


For example:

- Positive 3: 00000011
- Negative -3 (8-bit two's complement): 11111101
![](example%20bit%20signe.jpg)
Keep in mind that these are simplified explanations of binary operations. In real computer systems, there are more complexities and considerations, such as overflow and carry.

Remember that binary coding is fundamental to computer systems and underlies all digital operations and data storage.