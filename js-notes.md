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

## String Object
`new String("string")`
Wraps the string primative in an object. I have no clue why you would want to do this but you can for some reason.

Convert back into string literal with `.stringify()`

## toString()
You can convert values to strings using this. Works on numbers, arrays, etc. 

When using it on a number you can input a radix to output that number in a certain base (obviously defaults to base10). E.g.
```js
const num = 10;
console.log(num.toString(2)); // "1010" Base 2.
```

### Objects
This wont stringify an object it will just output `"[object Object]"`.
To stringify an object use JSON.stringify();

# Numbers and Bools

## 'Number' Type
Includes floating points, integers, NaN, Infinity and all other special numbers. They are all considered 'Numbers' by JS.

This also includes non-base-10 number systems.

## Number Constructor
If you call it without the `new` keyword, it will return a primitive type. This can be be used for type coercion (e.g. converting a string to a number).
An empty string will be 0, random characters will be `NaN`, `true` and `false` will return 1 and 0 respectively, `null` will be 0 and `undefined` will be `NaN`.
Additionally, an empty array will return 0, an array with a single number will return that number and an array with multiple numbers or any strings will return `NaN`.
Finally, an object will be `NaN`.

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

## Arrays of Fixed Length
Use the Array object: `new Array(n)`.
If you want to fill the array with a default value, use `new Array(n).fill(default)`.

You can also use `Array.from({ length: n })`. The difference is that `Array.from()` will fill the array with `undefined` explicitly, rather than leaving each position empty. I assume you can input another array into this can get a copy of it. You can also use callbacks to do this.

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

# Linters and Formatters

A linter is a static code analysis tool which flags programming errors, bugs and style errors.

A formatter will automatically format your code to match a style guide.

# Closures
When an inner function has access to variables in its outer inclosing scope: e.g.
```js
function outerFunction(x) {
    let y = 10;
    function innerFunction(){
        console.log(x + y);
    }
    return innerFunction;
}

let closure = outerFunction(5);
console.log(closure()); // 15
```

`innerFunction()` still has access to the variable in `outerFunction()`, even though `outerFunction()` finished executing. Also, if the variable in the `outerFunction()` changes, the `innerFunction()` will also see it, it's capturing a reference not a value.

# The `var` Keyword
Basically `var` is old, doesn't support block scoping, can be redeclared multiple times in the same scope without error and probably shouldn't be used because of this.

# Hoisting
The process of moving variable declarations to the top of their scope.

In the context of variables, you can use a variable within a scope before you declare it because JavaScript 'hoists' it and allocates memory before running any code. It will be `undefined` though until you get to the part in the execution where it is assigned. It only works this way with `var` and not `let` or `const`. If you use `let` or `const` before they're declared you will get a `ReferenceError`.

In the context of functions, it will hoist the whole function so you can use it fully before it has been declared.

# Modules
Allows you to create functionality within another JavaScript file and import exported functions, classes and/or variables.

You can export these using the `export` keyword:
```js
export function add(a, b) {
    return a + b;
}

export function subtract(a, b) {
    return a - b;
}

const PI = 3.14159;
export { PI };
```

You can then import them into another file like this:
```js
import { add, subtract, PI } from './math.js';

console.log(add(5, 3));        // Outputs: 8
console.log(subtract(10, 4));  // Outputs: 6
console.log(PI);               // Outputs: 3.14159
```
or use the `*` syntax to import everything:
```js
import * as Math from './math.js';

console.log(Math.add(5, 3));        // Outputs: 8
console.log(Math.subtract(10, 4));  // Outputs: 6
console.log(Math.PI);               // Outputs: 3.14159
```

You can have 1 default export per module:
```js
// In math.js
export default function multiply(a, b) {
    return a * b;
}

// In app.js
import multiply from './math.js';

console.log(multiply(4, 5));  // Outputs: 20
```

# Arguments Object
Functions contain an 'arguments' object array thing which allows you to have functions with a variable amount of arguments:
```js
function logArgs() {
  for (const arg of arguments) {
    console.log(arg);
  }
}

logArgs(1, 2, 3);
// result:
// 1
// 2
// 3

logArgs("example"); // "example"
```

You can't access most of the default Array methods with this because that wouldn't make sense.
Most apps don't use this, they use 'rest parameter syntax'.

# Rest Parameters
Self-explanatory:
```js
function logArgs(...args) {
  for (const arg of args) {
    console.log(arg);
  }
}

logArgs(1, 2, 3);
// result:
// 1
// 2
// 3
```

The rest parameter is a real array so you can use all the array methods.

# Naming Best Practice
Examples:
```js
// Bools
let isLoading = true;
let hasPermission = false;
let canEdit = true;

// Functions
function getUserData() { /* ... */ }
function isValidEmail(email) { /* ... */ }
function getProductDetails(productId) { /* ... */ }
function setUserPreferences(preferences) { /* ... */ }
function handleClick() { /* ... */ }

// Loop vars (single letters).
for (let i = 0; i < array.length; i++) { /* ... */ }
```

# Callbacks and Higher-Order Functions
## Callbacks
A function that is passed as an argument into another function.

Using an arrow function as the callback:
```js
let numbers = [1, 2, 3, 4, 5];
numbers.forEach(number => console.log(number * 2));
```

### `forEach()`
Lets you do an operaration each element in an array, e.g:
```js
let numbers = [1, 2, 3, 4, 5];

numbers.forEach(function(number) {
  console.log(number * 2);
});
```

the `forEach()` callback function can take 3 parameters `number`, `index`, `array`

If you have an independent function that can handle the parameters of the higher-order function you can just do this: `higherOrderFunc(callbackFunc)`

## Higher-Order Functions
Takes one or more functions as arguments, returns a function, or both.

Allows you to describe what you want to accomplish rather than describing it step-by-step (declarative vs imperative programming).

### 'Function Factories'
Using functions to create more specific functions
```js
function multiplyBy(factor) {
  return function(number) {
    return number * factor;
  }
}

let double = multiplyBy(2);
let triple = multiplyBy(3);

console.log(double(5)); // 10
console.log(triple(5)); // 15
```

## Map()
Lets you create a new array by applying a function to each element of the original array:
```js
const doubled = numbers.map((num) => num * 2);
```

It needs to have the same number of items as the original (I think).

The callback function can take up to 3 arguments:
```js
const numbers = [3, 4, 5, 6, 7].map((element, index, array) => {
  console.log("Element:", element);
  console.log("Index:", index);
  console.log("Array:", array);
  return element * 2;
});
```

## Filter()
Used to make a new array with elements that pass a test:
```js
const evenNumbers = numbers.filter((num) => num % 2 === 0);
```

Callback function can take the same three arguments as map.

Returns an empty array if nothing passes the test.

## Reduce()
Lets you process an array into a single value: Can be a number, string, object or another array.

Runs on each element of the array and passes on the running result (the accumulator) and the current value:
```js
const numbers = [1, 2, 3, 4, 5];
const sum = numbers.reduce(
  (accumulator, currentValue) => accumulator + currentValue,
  0
);

console.log(sum); // 15
```

The 0 above is reduces second argument and sets an initial value for the accumulator. If you don't set this it will use the initial value of the array.

## Method Chaining
A method would have to return the object its apart of in order to chain.

## Sort()
By default worts based on UTF-16 code unit values (so it will sort alphabetically but not usefully in any other way).

You can provide an optional sort callback function:
```js
const numbers = [414, 200, 5, 10, 3];

numbers.sort((a, b) => a - b);

console.log(numbers); // [3, 5, 10, 200, 414]
```
a is the first value, b is the second value. Should return a negative valid if a should come before b, a positive if a should come after b and 0 if they are equal.

## Every() and Some()
Allows you to check if all or some of the elements in an array meet a condition:
```js
const hasAllEvenNumbers = numbers.every((num) => num % 2 === 0);
```

# Dates and Times
Creating a new date: `const now = new Date();`
With a specific date/time: `const specificDate = new Date("July 4, 1776 12:00:00");` (format needs to be recognisable to the Date object).

If you don't set a value it will be 'now':
```js
const now = new Date();
const date = now.getDate(); // Will get day of the month.
```

In JavaScript, months are zero-based when using `Date.getMonth()`.

Format date in ISO:
```js
const date = new Date();
console.log(date.toISOString());
```

toLocaleDateString(locales, options): format the date to the users local by default. Options is an object:
```js
const date = new Date();
const options = {
  weekday: "long",
  year: "numeric",
  month: "long",
  day: "numeric",
};
console.log(date.toLocaleDateString("en-GB", options));
```

`Date.now()` returns the number of milliseconds from the UNIX epoch.

# Sets
Like an array but it will make sure that values only appear in it once.

You create a set using the `Set()` constructor (can be initialised with or without values):
```js
const treeSet = new Set(['Baobab', 'Jackalberry', 'Mopane Tree', 'Breadfruit']);
```
## Methods
- `add()`
- `delete()`
- `has()`
- `entries()`: Returns a `SetIterator` which contains an array of the values in a `[value, value]` format
- `forEach()`
- `keys()`: Alias for `values()`
- `values()`: Shows values in the set.
- `clear()`: Removes all items.
- `size()`: Returns the number of items in the set.


## WeakSet()
A `WeakSet()` is a type of set with fewer features that lets you store weakly held object references and symbols. `WeakSet()` does not support primitives.

The 'weak' part means that the set doesn't prevent the objects inside of it from being garbage collected if there are no other references to them.

Weak sets also aren't iterable and don't expose their context directly

Has the `add()`, `delete()` and `has()` methods.

| Feature                | Set                                                                             | WeakSet                                        |
|------------------------|---------------------------------------------------------------------------------|------------------------------------------------|
| Type of Values Stored  | Stores any data type                                                            | Stores only objects                            |
| Referencing            | Strong referencing                                                              | Weak referencing                               |
| Iteration              | Supports iteration with forEach and loops                                       | Does not support iteration                     |
| Methods and Properties | add(), delete(), has(), keys(), values(), size, and more                        | add(), delete(), and has() only                |
| Use case               | General-purpose collection of unique values and removing duplicates from arrays | Efficient memory tracking of object references |

# Maps
Stores key-value pairs similar to an object but it allows keys of any type, including objects and functions.

A Map provides better performance over the standard object when it comes to frequent addition and removals of key-value pairs.

Remembers the order in which keys are inserted.

If you set the same key twice it will update the value.

Creating a map (you can also do this without setting its values):
```js
const myTreesMap = new Map([
 [{ type: 'deciduous' }, 'Maple tree'],
 [['forest', 'grove'], 'Pine tree'],
 [42, 'Oak tree'],
 [true, 'Birch tree'],
 [function() { return 'I am a function key'; }, 'Willow tree'],
]);
/*
Map(5) {{…} => 'Maple tree', Array(2) => 'Pine tree', 42 => 'Oak tree', true => 'Birch tree', ƒ => 'Willow tree'}
  [[Entries]]
    0:{Object => "Maple tree"}
      key: {type: 'deciduous'}
      value: "Maple tree"
    1:{Array(2) => "Pine tree"}
      key: (2)
      value: "Pine tree"
    2:{42 => "Oak tree"}
      key: 42
      value: "Oak tree"
    3:{true => "Birch tree"}
      key: true
      value: "Birch tree"
    4:{function () { return "I'm a function key"; } => "Willow tree"}
      key: f ()
      value: "Willow tree"
    size: 5
    [[Prototype]]: Map
*/
```

Or:
```js
myTreesMap.set({ type: 'deciduous' }, 'Maple tree');
```

| Feature       | Map                                                                                   | WeakMap                                                          |
|---------------|---------------------------------------------------------------------------------------|------------------------------------------------------------------|
| Key Type      | Keys can be of any data type, including strings, numbers, objects, or even functions. | Keys must be objects.                                            |
| Use Case      | Use a Map when you need to associate data with any type of key.                       | Use a WeakMap when you only need to associate data with objects. |
| Iteration     | You can loop through a Map using forEach(), keys(), values(), or entries().           | A WeakMap is not iterable.                                       |
| Size Property | Map has a size property to get the number of key-value pairs.                         | WeakMap does not have a size property.                           |

## Methods
- `set()`: Allows you to add values.
- `get(key)`: Gets the value associated with the key. Returns a reference to the object.
- `has(key)`
- `delete(key)`: Will return whether or not the delete was sucessful.
- `clear()`: Deletes all key-value pairs.
- `entries()`: Check the entries of the map (returns entries as `MapIterator`).
- `keys()`: returns an iterable MapIterator of the keys in the map.
- `values()`: returns an iterable MapIterator of the values in the map.
- `forEach((value, key) => {})`: To loop through all entires.
- `size`: Number of key-value pairs in the map.

## WeakMap
Also a collection of key-value pairs but it uses weak references for its keys. The keys must be objects while the values can be any type.

Has the `set()`, `get()`, `has()` and `delete()` methods.

```js
const myTreeWeakMap = new WeakMap();

myTreeWeakMap.set({ id: 1 }, 'Maple tree');
myTreeWeakMap.set({ id: 2 }, 'Pine tree');
myTreeWeakMap.set({ id: 3 }, 'Oak tree');
myTreeWeakMap.set({ id: 4 }, 'Birch tree');
myTreeWeakMap.set({ id: 5 }, 'Willow tree');
/*
WeakMap {{…} => 'Willow tree', {…} => 'Maple tree', {…} => 'Pine tree', {…} => 'Oak tree'}
  [[Entries]]
    No properties
  [[Prototype]]: WeakMap
*/
```

# Classes
Blueprints which let you define multiple objects of the same kind.

Basic syntax:
```js
class MyClassName {
  // Class Methods
  constructor(value) { 
    this.property1 = value;
  }
  method1() { ... }
  method2() { ... }
  ...
}
```
Properties and methods can be accessed using dot notation when you create an instance of the object.

You can also define a class as a class expression, you make an anonymous class and assign it to a variable:
```js
const Dog = class {
  constructor(name) {
    this.name = name;
  }

  bark() {
    console.log(`${this.name} says woof!`);
  }
};
```

## `this` Keyword
The context where code is supposed to run. E.g. when used in a method `this` is a reference to the object the method is associated with:
```js
class Dessert {
  constructor(name, price) {
    this.name = name;
    this.price = price;
  }

  showPrice() {
    console.log(`The price of ${this.name} is $${this.price}.`);
  }
}
```

`this` works differently in arrow functions. They are helpful for callbacks but in that context 'this' won't refer currrent object in object methods; `this` gets inherited from their parent scope.

## Inheritence
Use `extends` syntax:
```js
class Vehicle {
  constructor(brand, year) {
    this.brand = brand;
    this.year = year;
  }
}

class Car extends Vehicle {
  honk() {
    console.log("Honk! Honk!");
  }
}
```

You don't need a constructor if you aren't defining new properties.

There is also `super()` which when used in a child classes' constructor will invoke the constructor of the superclass and can be used to access the parent class's methods, constructors and fields:
```js
class Vehicle {
  constructor(brand, year) {
    this.brand = brand;
    this.year = year;
  }
}

class Car extends Vehicle {
  constructor(brand, year, numDoors) {
    super(brand, year);
    this.numDoors = numDoors;
  }
}
```

## Static
Often used for data/methods relevant to all instances of a class 
Conceptually the same as C#:
```js
class Movie {
  static numberOfMovies = 0

  constructor(title, rating) {
    this.title = title;
    this.rating = rating;
    Movie.numberOfMovies++;
  }

  static compareMovies(movieA, movieB) {
    if (movieA.rating > movieB.rating) {
      console.log(`${movieA.title} has a higher rating.`);
    } else if (movieA.rating < movieB.rating) {
      console.log(`${movieB.title} has a higher rating.`);
    } else {
      console.log("These movies have the same rating.");
    }
  }

}

let movieA = new Movie("Movie A", 80);
let movieB = new Movie("Movie B", 45);
Movie.compareMovies(movieA, movieB);
console.log(movieA);
```

### Factory Methods
To create specific objects based on a class within the class:
```js
class Pizza {
  constructor(type, price) {
    this.type = type;
    this.price = price;
  }

  static createMargherita() {
    return new this("Margherita", 6.99);
  }
}
```

In the context of static methods, `this` refers to the class itself rather than the object you are creating.

# Recursion
A way of creating a loop where a function calls itself repeatedly. Example:
```js
const recursiveCountdown = (number) => {
  if (number < 1) {
    return;
  }
  console.log(number);
  recursiveCountdown(number - 1);
};

recursiveCountdown(5);
```

You can take advantage of the call stack which is the idea that JS will wait for a function to finish before continuing. This operates on a LIFO basis. This means you can make the counter count up by simply swapping the logging and recursion step.
```js
const recursiveCounter = (number) => {
  if (number < 1) {
    return;
  }
  recursiveCountdown(number - 1);
  console.log(number);
};

recursiveCounter(5); 
```
Any code after the recursion step will happen AFTER that specific recursion step is complete, so you essentially reverse the execusion order for code below the recursion.

# Async
The event handler thing + callbacks is how async used to happen.
Now promises are used apparently.

## Async in `script` Elements
The `async` and `defer` attributes in the HTML `script` tag determine how the JS file is loaded and executed in web pages.

When using the `async` attribute, the browser will continue to pass the HTML while the script is being downloaded, then it will pause and execute the script before continuing to parse the HTML. The `defer` attribute is different in that it will wait until the HTML parsing is complete berfore executing.

`defer` scripts will also execute in the order they appear in the HTML instead of running immediately on download at some random time.

## Fetch API
Lets you make network requests, example of a `GET` request:
```js
fetch('https://api.example.com/data')
```

Can fetch text, JSON, images, videos, etc.

The `fetch()` method returns a response, you can use the, `then` method to access it. You can also chain `then`s:
```js
fetch('https://api.example.com/data')
  .then(response => response.json())
  .then(data => console.log(data))
```

The response from the fetch API is a `Promise`. The use of multiple `then`s is known as promise chaining.

Option setting with fetch for other kinds of requests:
```js
fetch('https://api.example.com/users', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    name: 'John Doe',
    email: 'john@example.com'
  })
})
```

## Promises
An object that represents the eventual completion or failure of an async operation:
```js
const aPromise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("Operation successful!");
  }, 1000);
});
```

You can then use `then` or `catch` to handle success or errors:
```js
aPromise.then((result) => {
  console.log(result);  // Outputs: "Operation successful!"
}).catch((error) => {
  console.error(error);
});
```

Then chaining is a Promise feature. Allows you to perform multiple async operations one after the other on the response.

## Async/Await
These are built on top of Promises and are meant to make reading and writing async code easier. Used like this:
```js
async function delayedGreeting(name) {
  console.log("A Messenger entered the chat...");
  await new Promise(resolve => setTimeout(resolve, 2000));
  console.log(`Hello, ${name}!`);
}

delayedGreeting("Alice");
console.log("First Printed Message!");
```

`await` lets you wait for an async function to finish before continuing. An advantage of this is being able to to handle errors using a `try`/`catch`:
```js
async function fetchUserData() {
  try {
    let response = await fetch(`https://api.example.com/users`);
    let userData = await response.json();
    console.log(userData);
  } catch (error) {
    console.log("Error fetching user data:", error);
  }
}

fetchUserData();
```
You need to await the JSON thing above to wait for the JSON to parse.
Async functions will always return a `Promise`.

# JS Runtimes
JavaScript runtimes provide extra tools (the DOM for browsers, Fetch API for network requests, etc).

Node.js is one of the most popular non-browser runtimes built on Google's V8 engine.

# Try... Catch... Finally
Finally part usually used for like cleanup and stuff.

# Debugger
Put the `debugger` statement somewhere you your code to pause execution.

`console.dir()`: Display interactive list of the properties of a JS object.
`console.table()`: Displays tabular data is a table in the console. Must be array or object. Lets you spectify which properties (columns) to display.

# HTTP Methods
GET Method: This is used to fetch data from a server.
POST Method: This is used to submit data to a server which creates a new resource.
PUT Method: This is used to update a resource by replacing it entirely.
PATCH Method: This is used to partially update a resource.
DELETE Method: This is used to remove records from a database.

# Local Storage
Available until explicitly removed.
localStorage.setItem() Method: This method is used to store a key-value pair in localStorage.
localStorage.getItem() Method: This method is used to retrieve the value of a given key from localStorage.
localStorage.removeItem() Method: This method is used to remove a specific item from localStorage using its key.
localStorage.clear() Method: This method is used to clear all of the stored data in localStorage.

# Session Storage
Available only for the current session. Clears when the window is closed or the browser tab is closed.


