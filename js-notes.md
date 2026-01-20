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

arguments are what you pass into the function. Parameters are the placeholders.

## Anonymous Functions
Anonymous functions are when you assign a function to a variable
```js
    const thing = function () {
        // code here    
    }
```

### Arrow Syntax
```js
    const functionName = (parameter) => {
        // code
    }
```

One parameter can exclude the parentheses:
```js
    const functionName = parameter => {
        // code
    }
```

One line with no return:
```js
    const functionName = parameter => console.log("code");
```

One line with return:
```js
    const functionName = parameter => parameter * b; // will return the result of 'parameter * b' implicitly. Can't use an explicit return with this syntax.
```

# Scope
Global, local and block.

## Global
Outermost scope.

## Local
Accessible within a function only.

## Block
Introduced later, code section within {}. (if statements, loops, etc);

# Arrays
Can hold anything.

.length to access number of elements.

Acessing a non-existant index will return undefined.

You update elements by assigning a new value to a specific index.
You can add new elements by assigning to an index that doesn't exist yet, if you assign to an index far above what exists, the values inbetween will still be undefined.

You can create a 2d array by creating an array in an array.

## Shallow Copies
Spread operator lets you make a shallow copy of the array: `let copy = [...original];`

JS by default will make a copy when you assign a variable to another but when copying arrays, any inner arrays and stuff will have the same memory reference in both arrays unless you use the above syntax.

## Methods
- push(): Adds an element to the end of the array (returns the new length of the array).
- pop(): Remove the last element (also returns what it removed).
- shift(): Remove the first element from an array (also returns what it removed).
- unshift(): Adds to the beginning of the array (returns the new length of the array).
- split(separator): Divides a string into an array of strings.
- reverse(): Reverses an array.
- join(separator): Converts an array into a string.
- indexOf(element, fromIndex): Not found = -1.
- splice(startIndex, itemsToRemove, item1, item2): items 1 and 2 will be added in place of the removed items. It will insert before the startIndex.
- includes(): Returns bool. Uses strict equality.
- concat(): Makes a new array by merging two or more arrays.
- slice(): returns a new array with a shallow copy of a portion of the original array.

push() and unshift() can add multiple elements. Pop and shift can't remove multiple.

## Destructuring
```js
let fruits = ["apple", "banana", "orange"];

let [first, second, third] = fruits;
```

skip elements:
```js
let colors = ["red", "green", "blue", "yellow"];
let [firstColor, , thirdColor] = colors;
```

default values: 
```js
let numbers = [1, 2];
let [a, b, c = 3] = numbers;
```

rest syntax:
```js
let fruits = ["apple", "banana", "orange", "mango", "kiwi"];
let [first, second, ...rest] = fruits;

console.log(first);  // "apple"
console.log(second); // "banana"
console.log(rest);   // ["orange", "mango", "kiwi"]
```
Rest must be the las element of the deconstruction.

# Objects
Use bracket notation to access property names that aren't valid JS identifiers, e.g.
```js
thing["property name"]
```
Also lets you access properties using variables (dynamically).

example object (quotes are optional for valid js identifiers):
```js
const oddObject = {
  "1stProperty": "Hello",
  "property with spaces": "World"
};
```

## Deleting Properties
`delete` keyword:
```js
delete object.property
```

Destructuring:
```js
const { job, city, ...remainingProperties } = person;

// The remainingProperties variable won't have job or city.
```

## Checking For Properties
- `object.hasOwnProperty("propertyToFind")`. Returns boolean.
- `in`: e.g. `"propertyToFind" in object`. Returns boolean.
- Checking for `undefined`: `object.propertyToFind !== undefined`. May cause false negative if a property is intentially undefined.

## Nested Objects
`object.property.nestedProperty` or `object['property']['nestedProperty']`.

## Arrays
`object.arrayProperty[index].propertyInArrayObject`

## Primatives vs Non-Primatives
Primatives are immutable (they can't be modified after creation). This is why they can be copied.

Non-Primatives are objects (objects, arrays, functions, etc). They can hold multiple values as properties or elements. If a variable contains a non-primative value, you are holding a reference to that object. If you assign that object to another variable without making an explicit copy, you are just copying a pointer.

## Functions vs Object Methods
Object methods are functions associated with an object:
```js
const person = {
    name: "Bob",
    age: 30,
    sayHello: function() {
        return "Hello, my name is " + this.name;
    }
};
```

functions are called by name, methods are called using dot notation (`person.sayHello()`).

Functions have their own scope and don't have a built-in reference to an object.

Methods are bound to their object, and access its properties and other methods using `this`.

Methods organise code into logical objects, while functions are for more general reusable code.

## Object Constructor
You can use `Object()` or `new Object()`. It behaves differently in some way that wasn't explained.

You can use `Object()` to wrap a value in an object. E.g. `Object(45)`. This is useful if you need an object wrapper for a primative value for some reason.

## JSON
Supports lots of data types.

Keys need to be wrapped in double quotes.

Importing JSON:
```js
import data from "./example.json" with { type: "json" };

console.log(data.age);
```

### JSON.parse() and JSON.stringify()
`JSON.stringify(object, replacer, spacer)` converts a JS Object into JSON. Replacer is optional and is an array of the parameters you want in the JSON. Spacer lets you control the spacing (formatting).

`JSON.parse()` turns JSON into a JS Object.

## Optional Chaining
Lets you access potentially non-existant object values without throwing an error:
```js
const user = {
  name: "John",
  profile: {
    email: "john@example.com",
    address: {
      street: "123 Main St",
      city: "Somewhere"
    }
  }
};

console.log(user?.profile?.address?.street); // "123 Main St"
console.log(user?.profile?.phone?.number);   // undefined
```

## Object Destructuring
Lets you extract multiple properties in one statement:
```js
const person = { name: "Alice", age: 30, city: "New York" };

const { name, age } = person;

console.log(name); // Alice
console.log(age);  // 30
```

You can also choose your own variable names: `let { name: personName, age: personAge } = person;`.

Additionally, you can set default values `let { name, age, country = "Unknown" } = person;`.

Shorthand for creating objects: `let person = { name, age }; // person: { name: "Bob", age: 25 }`. Useful for returning objects from functions.

### Nested Object Destructuring
```js
const recipe = {
  name: "Chocolate Cake",
  ingredients: {
    flour: "2 cups",
    sugar: "1 cup"
  }
};

// Extract `flour` from `ingredients`
const { ingredients: { flour } } = recipe;

console.log(flour); // "2 cups"
```

# Loops
`break` exit the loop early.
`continue` go to the next iteration.

You can use lables on these as well to control the flow of nested loops:
```js
outerLoop: for (let i = 0; i < 3; i++) {
  innerLoop: for (let j = 0; j < 3; j++) {
    if (i === 1 && j === 1) {
      break outerLoop;
    }
    console.log(`i: ${i}, j: ${j}`);
  }
}
```

## For Loop
Structure:
```js
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```

### For Of Loop
Structure:
```js
for (variable of iterable) {
  // code block to be executed
}
```

Both `let` and `const` are valid for initialising the variable but obviously const won't let you change the variable inside of the loop.

Works on arrays, strings, etc.

### For In Loop
When iterating over properties in an object:
```js
for (variable in object) {
  // code block to be executed
}
```

The variable will be the property name, you have to reference the object inside of the for loop to actually access its values.

It is recommended to use a for of loop for things that aren't objects.

## Do While
```js
do {
} while(condition);
```
Will run the loop once before checking the condition.
