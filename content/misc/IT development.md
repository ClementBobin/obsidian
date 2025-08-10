# Introduction  
IT development concerns everything related to the study, design, construction, development, development, maintenance and improvement of software/applications and websites.  
  
In SIN, to perform computer development we will study several programming languages:  
  
Programming languages for software development/applications:  
- Arduino (very close to C and C++ – to develop programs on Arduino boards or ESP32 type microcontrollers). A summary sheet on the different commands and specificities of the Arduino language is available on the professor’s website.  
- Python (to develop programs on Raspberry Pi boards).  
To learn the Python language a series of courses/ problems is proposed on the site France-ioi.org  
  
#arduino_uno  
![](asset/image/Arduino_uno.png)  
#esp32  
![](asset/image/esp32.png)  
#raspberry3pi  
![](asset/image/Raspberry_pi3.png)  
  
Programming languages for WEB development:  
- [HTML](HTML.md) (HyperText Markup Language – Hypertext markup language – represents web pages).  
- [CSS](Css.md) (Cascading Style Sheet – Language for formatting a web page). You can find the HTML/CSS activity performed in first class on the teacher’s website.  
- [PHP](Php.md) (Hypertext Preprocessor – allows you to create dynamic web pages).  
The PHP language will be studied in activity.  
  
# Encoding of information  
## Principle of a base  
  
The basis is the number used to define a numeration system. The base of the decimal system is ten while that of the hexadecimal system is 16 and the base of the binary system is 2. Whatever the numerical base used, it follows the following relationship:  
![](asset/image/Principe_base.png)  
Where `bi' is the rank base number `i' and `ai' is the power of the `i' rank exponent base.  
  
*Example: base 10*  
`1986 = (1 * 103 ) + (9 * 102 ) + (8 * 101 ) + (6 * 100 )`

## The decimal system  
The decimal system is the one in which we are most used to writing. Each digit can have 10 different values: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9. Therefore, the decimal system has for base 10. Any number written in the decimal system verifies the following relationship:  
745 = 7 x 100 + 4 x 10 + 5 x 1  
745 = 7 x 10 x 10 + 4 x 10 + 5 x 1  
745 = 7 x 10^2 + 4 * 10^1 + 5 * 10^0  
  
Each digit of the number is multiplied by a power of 10: this is what is called the 'weight of the number'.  
  
The exponent of this power is zero for the right-most digit and increases by one unit for each pass to one digit to the left.  
  
12 435 = 1 x 10^4 + 2 x 10^3 + 4 x 10^2 + 3 x 10^1 + 5 x 10^0 .  
  
This way of writing numbers is called the ==position counting system==. In our conventional system, we use the powers of 10 to weight the value of the numbers according to their position, however it is possible to imagine other systems of numbers having as basis an integer  
different.  
  
## The binary system  
In the binary system, each digit can have 2 different values: 0, 1. Therefore, the system has base 2. Any number written in this system checks the following relationship:  
  
(10 110)^2 = 1 * 2^4 + 0 * 2^3 + 1 * 2^2 + 1 * 2^1 + 0 * 2^0  
(10 110)^2 = 1 * 16 + 0 * 8 + 1 * 4 + 1 * 2 + 0 * 1  
so `(10110)^2 = (22)^10`  
  
All position counting systems obey the rules we have just seen.  
  
## The hexadecimal system  
The hexadecimal system uses the following 16 symbols: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, A, B, C, D, E, F. Therefore, the system has for base 16.  
A number expressed in base 16 may be as follows: (5AF)^16.  
  
The number (5AF)^16 can be broken down as follows:  
(5AF)^16 = 5 * 16^2 + A * 16^1 + F * 16^0  
By replacing A and F with their equivalent in base 10, we obtain:  
(5AF)^16 = 5 * 16^2 + 10 * 16^1 + 15 * 16^0  
(5AF)^16 = 5 * 256 + 10 * 16 + 15 * 1
so `(5AF)^16 = (1455)^10`  
  
## The octal system  
The octal system uses a counting system having as base 8. It should be noted that in this system we will no longer have 10 symbols but only 8: 0, 1, 2, 3, 4, 5, 6, 7.  
  
Thus, a number expressed in base 8 may be presented as follows: (745)^8  
  
When writing a number, it will be necessary to specify the basis in which it is expressed to lift any indeterminations (745 also exists in base 10). Thus the number will be put in parentheses (745 in our example) and indicated by a number representing its base (8 is put in index).  
  
This base will follow the same rules as base 10, seen above, so we can decompose (745)8 as follows:  
  
(745)^8 = 7 * 8^2 + 4 * 8^1 + 5 * 8^0  
(745)^8 = 7 * 64 + 4 * 8 + 5 * 1  
(745)^8 = 448 + 32 + 5  
  
We have just seen that: `(745)^8 = (485)^10`.  
![](asset/image/Base%20convertion.png)  
## ASCII  
ASCII (American Standard Code for Information Interchange) is a computer-based standard for encoding alphanumeric characters. ASCII includes 128 7-bit combinations historically that define 95 printable characters, including Arabic numerals from 0 to 9, the letters of the Latin alphabet not accented, lowercase and uppercase, punctuation symbols and some simple mathematical characters.  
  
It is well suited for encoding texts in English, but is insufficient for French, particularly because of the absence of accented characters. It should also be noted that the first 32 combinations are not printable as well as the last, 127: all correspond to computer terminal commands.  
Thus, the combination 127 corresponds to the command to erase.

The ASCII code has been extended to 8 bits to incorporate certain accented characters (including French accents). We see below the second part of the ASCII code called extended encoded on 8 bits, the first part being the historical ASCII code on 7 bits which codes in decimal from 0 to 127, in hexadecimal from 00h to 7Fh. The extension below therefore codes in decimal from 128 to 255 and in hexadecimal from 80h to FFh.
![](asset/image/ASCII.png)

## UNICODE
Unicode is a computer standard that allows text to be exchanged in a wide variety of languages, at a global level. It is developed by the Unicode Consortium, which aims to encode written text by giving any character of any writing system a name and numeric identifier, in a unified manner, regardless of the computer platform or software used.

To date, Unicode references over 137,000 characters in over 100 scripts.

The main feature of UTF-8 (Unicode variant) is that it is backwards compatible with the ASCII standard, that is, any ASCII character is encoded in UTF-8 as a single byte, identical to the ASCII code. For example, “A” (capital A) has ASCII code 65 and is coded in UTF-8 by byte 65.