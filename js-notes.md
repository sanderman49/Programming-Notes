# Strings
undefined = not assigned a value
null = intentially set to nothing

'let' allows reassignment, 'const' doesn't

Variables in JavaScript must begin with a letter, an underscore (_), or a dollar sign ($). They cannot start with a number. Don't use any other special characters.

string work with single or double quotes.

String are immutable, once a string is created, you cannot change its characters directly.

you can append to strings using the += operator: greeting += ', John!';

concat method: let result = str1.concat(' ', str2);

Semicolons are optional (adding can prevent errors). Mark the end of 'statements'.

'typeof' operator will output the type of a variable as a string: e.g. 'typeof isUserLoggedIn'.
With typeof, null = object.

A Symbol is unique and immuatable value. E.g.
const crypticKey1= Symbol("saltNpepper");
const crypticKey2= Symbol("saltNpepper");
console.log(crypticKey1 === crypticKey2); // false

strings have a 'length' property.

You escape with a backslash.

String interpolation: `Hello, ${name}!`. You make a template literal with the backticks, then use the ${} to embed an expression.

With template literals you don't need to use \n syntax for multiline, you just make a new line and it'll figure it out.

The indexOf() method allows you to find substrings within a string. indexOf("substring", searchStartIndex). It will return the index of the substring.

prompt() method is how you get user input. Optional second argrument for a default value. If you user cancels you get a null.

charCodeAt(index) gives you the ASCII code of a character.
String.fromCharCode(num) will convert an ASCII code into a character.

includes(substring, startIndex) returns a boolean depending on if the string contains the specified substring.

slice(startIndex, endIndex) will return a 'slice' of the string inbetween the two indexes (includes the only start index). You can use a negative indexes, -1 refers to the last character.

Trim(), TrimStart() and TrimEnd() can be used to trim whitespace.

string.replace(searchValue, newValue);
Search value can be regex.
There is also replaceAll

JavaScript has an 'Infinity' keyword (also -Infinity).

# Numbers and Bools

## 'Number' Type
Includes floating points, integers, NaN, Infinity and all other special numbers. They are all considered 'Numbers' by JS.

This also includes non-base-10 number systems.

### Arithmatic
You will get a NaN if you try to perform maths on non-numbers.

Division by 0 = Infinity.

% will return the remainder.

** is the exponation operator.

Adding a number and a string will concatanate them.

When doing other kinds of maths on a string, JS will try to cast the string to an integer. If it can you will get a NaN

True and False become 1 and 0.

JavaScript treats null as 0 and undefined as NaN in mathematical operations.

### Operations from Math library
- Math.random() Method: This method generates a random floating-point number between 0 (inclusive) and 1 (exclusive). This means the possible output can be 0, but it will never actually reach 1.
- Math.max() Method: This method takes a set of numbers and returns the maximum value.
- Math.min() Method: This method takes a set of numbers and returns the minimum value.
- Math.ceil() Method: This method rounds a value up to the nearest whole integer.
- Math.floor() Method: This method rounds a value down to the nearest whole integer.
- Math.round() Method: This method rounds a value to the nearest whole integer.
- Math.trunc() Method: This method removes the decimal part of a number, returning only the integer portion, without rounding.
- Math.sqrt() Method: This method will return the square root of a number.
- Math.cbrt() Method: This method will return the cube root of a number.
- Math.abs() Method: This method will return the absolute value of a number.
- Math.pow() Method: This method takes two numbers and raises the first to the power of the second.

### Order of Operations
Follows standard BIDMAS rules, left to right.

Odd cases:
- Assignment goes right to left
- Exponents go right to left.

### Incrementing/Decrementing
syntax: x++ or ++x. The prefixed one will add to x then return the value, the postfixed one will return first then add.

### Unary Operators
The unary plus operator (+var) converts its operand into a number. E.g. `+'43' === 43`.

The unary negation operator (-var) converts its operand into a number and flips the sign. E.g. `-'43' === -43`.

The bitwise NOT operator (~) flips each bit of a number (so 11001 becomes 00110).

Void takes an operand and turns it into 'undefined'.

### Bitwise Operators

## Bools
using the equality operator (==) will perform type coercion, the strict equality operator (===) won't.

### Truthy and Falsy
Evaluate to true in a boolean context:
- Non-empty strings
- Non-zero numbers (0 or -0)
- Arrays
- Objects
- The boolean true


Evaluate to false in a boolean context:
- "" (empty string)
- 0
- false
- null
- undefined
- NaN


You can check Truthiness using the Boolean(value) method. It will return true or false.

## Conditionals

### Ternary Operator
condition ? expressionIfTrue : expressionIfFalse;


### Logical AND (&&)
If both are truthy it returns the second value.
If both are falsy it returns the first falsy value.

### Logical OR (||)
Will return the first truthy value.

### Nullish Coalescing Operator (??)
Will return the second value only if the first value is null or undefined.

Good for setting default/fallback values.

## NaN
Represents a non-valid numerical value like "Jessica".

NaN is equal to nothing, not even itself. That is why the IsNan() function exists. Feeding IsNan something that can't be cast into a number will result in 'true'.

Number.IsNan() is different in that it will not attempt to cast and anything that is not actually NaN will not equal true (a random string will be false unlike the normal IsNan());

## PassFloat/PassInt
These will cast a string into an int or float. They will go until they hit an invalid character (letter, an extra decimal, etc). If the string starts in an invalid character they will return NaN.

Both ignore leading whitespace and can handle leading +/- characters correctly.

## toFixed()
Limits the number of decimal places a float can have. It will round correctly. It returns a string. Default to 0dp (integer). Not sure it rounds correctly with 0dp.

## Comparisons with Null and Undefined
They represent absense but behave differently.

Undefined = Uninitialised variables + unassigned parameters.
Null = Deliberate non-value.

Weird Behavior:
```js
console.log(null == undefined); // true (because of coercion)
console.log(null === undefined); // false

console.log(null > 0);  // false
console.log(null == 0); // false
console.log(null >= 0); // true ???????

console.log(undefined > 0);  // false
console.log(undefined < 0);  // false
console.log(undefined == 0); // false
```

Undefined always converts to NaN in numeric contexts

## Switch Statements
```js
switch (expression) {
  case value1:
    // code to be executed if expression === value1
    break;
  case value2:
    // code to be executed if expression === value2
    break;
  default:
    // code to be executed if expression doesn't match any case
}
```

Switch statements are strict.

Be careful not to omit the break or the switch statement execute the cases below it until it hits a break.

# Functions
By default return 'undefined'.

## Anonymous Functions
Anonymous functions are when you assign a function to a variable
```js
    const thing = function () {
        // code here    
    }
```
