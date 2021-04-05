# Javascript Shorthand Techniques

This really is a must read for any JavaScript developer. I have written this guide to shorthand JavaScript coding techniques that I have picked up over the years. To help you understand what is going on, I have included the longhand versions to give some coding perspective. 

Please if you have something to share, please update this git. :smile:

# Ternary Operator
 This is a great code saver, when you want to write an `if...else` statement in just one line.
 
### Longhand:
 ```javascript
 const x = 20;
 let answer;
 
 if(x > 10) {
     answer = "greater than 10";
 } else {
     answer = "less than 10";
 }
 ```
### Shorthand:
 ```javascript
 const answer = x > 10 ? "greater than 10" : "less than 10"
 ```
 
 You can also nest your `if` statement like this:
 ```javascript
 const answer = x > 10 ? "greater than 10" : x < 5 ? "less than 5" : "between 5 and 10";
 ```

# Short-circuit Evaluation Shorthand
When assigning a variable value to another variable, you may want to ensure that the source variable is not null, undefined, or empty. You can either write a long `if` statement with multiple conditionals, or use a short-circuit evaluation.
 
 ### Longhand:
```javascript
if (variable1 !== null || variable1 !== undefined || variable1 !== '') {
     let variable2 = variable1;
}
```

### Shorthand:
```javascript
const variable2 = variable1  || 'new';
Don’t believe me? Test it yourself (paste the following code in es6console):

let variable1;
let variable2 = variable1  || 'bar';
console.log(variable2 === 'bar'); // prints true

variable1 = 'foo';
variable2 = variable1  || 'bar';
console.log(variable2); // prints foo
```
Do note that if you set `variable1` to `false` or `0`, the value `bar` will be assigned.

# Declaring Variables Shorthand
It’s good practice to declare your variable assignments at the beginning of your functions. This shorthand method can save you lots of time and space when declaring multiple variables at the same time.

### Longhand:
```javascript
let x;
let y;
let z = 3;
```
### Shorthand:
```javascript
let x, y, z=3;
```

# If Presence Shorthand
This might be trivial, but worth a mention. When doing “if checks”, assignment operators can sometimes be omitted.

### Longhand:
```javascript
if (likeJavaScript === true)
```

### Shorthand:
```javascript
if (likeJavaScript)
```

> **Note:** these two examples are not exactly equal, as the shorthand check will pass as long as likeJavaScript is a truthy value.

Here is another example. If `a` is NOT equal to true, then do something.

### Longhand:
```javascript
let a;
if ( a !== true ) {
// do something...
}
```
### Shorthand:
```javascript
let a;
if ( !a ) {
// do something...
}
```

# JavaScript For Loop Shorthand
This little tip is really useful if you want plain JavaScript and don’t want to rely on external libraries such as jQuery or lodash.

### Longhand:
```javascript
const fruits = ['mango', 'peach', 'banana'];
for (let i = 0; i < fruits.length; i++)
```

### Shorthand:
```javascript
for (let fruit of fruits)
```

If you just wanted to access the index, do:
```javascript
for (let index in fruits)
```
This also works if you want to access keys in a literal object:
```javascript
const obj = {continent: 'Africa', country: 'Kenya', city: 'Nairobi'}

for (let key in obj)
  console.log(key) // output: continent, country, city
  ```
### Shorthand for Array.forEach:
```javascript
function logArrayElements(element, index, array) {
  console.log("a[" + index + "] = " + element);
}

[2, 5, 9].forEach(logArrayElements);
// Output
// a[0] = 2
// a[1] = 5
// a[2] = 9
```

# Short-circuit Evaluation
Instead of writing six lines of code to assign a default value if the intended parameter is null or undefined, we can simply use a short-circuit logical operator and accomplish the same thing with just one line of code.

### Longhand:
```javascript
let dbHost;
if (process.env.DB_HOST) {
  dbHost = process.env.DB_HOST;
} else {
  dbHost = 'localhost';
}
```
### Shorthand:
```javascript
const dbHost = process.env.DB_HOST || 'localhost';
```

# Decimal Base Exponents
You may have seen this one around. It’s essentially a fancy way to write numbers without the trailing zeros. For example, 1e7 essentially means 1 followed by 7 zeros. It represents a decimal base (which JavaScript interprets as a float type) equal to 10,000,000.

### Longhand:
```javascript
for (let i = 0; i < 10000; i++) {}
```

### Shorthand:
```javascript
for (let i = 0; i < 1e7; i++) {}

// All the below will evaluate to true
1e0 === 1;
1e1 === 10;
1e2 === 100;
1e3 === 1000;
1e4 === 10000;
1e5 === 100000;
```

# Object Property Shorthand
Defining object literals in JavaScript makes life much easier. ES6 provides an even easier way of assigning properties to objects. If the variable name is the same as the object key, you can take advantage of the shorthand notation.

### Longhand:
```javascript
const x = 1920, y = 1080;
const obj = { x:x, y:y };
```

### Shorthand:
```javascript
const obj = { x, y };
```

# Arrow Functions Shorthand
Classical functions are easy to read and write in their plain form, but they do tend to become a bit verbose and confusing once you start nesting them in other function calls.

### Longhand:
```
function sayHello(name) {
  console.log('Hello', name);
}

setTimeout(function() {
  console.log('Loaded')
}, 2000);

list.forEach(function(item) {
  console.log(item);
});
```
### Shorthand:
```
sayHello = name => console.log('Hello', name);
setTimeout(() => console.log('Loaded'), 2000);
list.forEach(item => console.log(item));
```

It’s important to note that the value of `this` inside an arrow function is determined differently than for longhand functions, so the two examples are not strictly equivalent.

# Implicit Return Shorthand
Return is a keyword we use often to return the final result of a function. An arrow function with a single statement will implicitly return the result its evaluation (the function must omit the braces (`{}`) in order to omit the return keyword).

To return a multi-line statement (such as an object literal), it’s necessary to use `()` instead of `{}` to wrap your function body. This ensures the code is evaluated as a single statement.

### Longhand:
```javascript
function calcCircumference(diameter) {
  return Math.PI * diameter
}
```
### Shorthand:
```javascript
calcCircumference = diameter => (
  Math.PI * diameter;
)
```

# Default Parameter Values
You can use the `if` statement to define default values for function parameters. In ES6, you can define the default values in the function declaration itself.

### Longhand:
```javascript
function volume(l, w, h) {
  if (w === undefined)
    w = 3;
  if (h === undefined)
    h = 4;
  return l * w * h;
}
```
### Shorthand:
```javascript
volume = (l, w = 3, h = 4 ) => (l * w * h);
volume(2) //output: 24
```

# Template Literals
Aren’t you tired of using `' + '` to concatenate multiple variables into a string? Isn’t there a much easier way of doing this? If you are able to use ES6, then you are in luck. All you need to do is use is the backtick, and `${}` to enclose your variables.

### Longhand:
```javascript
const welcome = 'You have logged in as ' + first + ' ' + last + '.'
const db = 'http://' + host + ':' + port + '/' + database;
```
### Shorthand:
```javascript
const welcome = `You have logged in as ${first} ${last}`;
const db = `http://${host}:${port}/${database}`;
```

# Destructuring Assignment Shorthand
If you are working with any popular web framework, there are high chances you will be using arrays or data in the form of object literals to pass information between components and APIs. Once the data object reaches a component, you’ll need to unpack it.

### Longhand:
```javascript
const observable = require('mobx/observable');
const action = require('mobx/action');
const runInAction = require('mobx/runInAction');

const store = this.props.store;
const form = this.props.form;
const loading = this.props.loading;
const errors = this.props.errors;
const entity = this.props.entity;
```
### Shorthand:
```javascript
import { observable, action, runInAction } from 'mobx';

const { store, form, loading, errors, entity } = this.props;
```

You can even assign your own variable names:
```javascript
const { store, form, loading, errors, entity:contact } = this.props;
```

# Multi-line String Shorthand
If you have ever found yourself in need of writing multi-line strings in code, this is how you would write it:

### Longhand:
```javascript
const lorem = 'Lorem ipsum dolor sit amet, consectetur\n\t'
    + 'adipisicing elit, sed do eiusmod tempor incididunt\n\t'
    + 'ut labore et dolore magna aliqua. Ut enim ad minim\n\t'
    + 'veniam, quis nostrud exercitation ullamco laboris\n\t'
    + 'nisi ut aliquip ex ea commodo consequat. Duis aute\n\t'
    + 'irure dolor in reprehenderit in voluptate velit esse.\n\t'
```

But there is an easier way. Just use backticks.

### Shorthand:
```javascript
const lorem = `Lorem ipsum dolor sit amet, consectetur
    adipisicing elit, sed do eiusmod tempor incididunt
    ut labore et dolore magna aliqua. Ut enim ad minim
    veniam, quis nostrud exercitation ullamco laboris
    nisi ut aliquip ex ea commodo consequat. Duis aute
    irure dolor in reprehenderit in voluptate velit esse.`
```

# Spread Operator Shorthand
The **spread operator**, introduced in ES6, has several use cases that make JavaScript code more efficient and fun to use. It can be used to replace certain array functions. The spread operator is simply a series of three dots.

### Longhand:
```javascript
// joining arrays
const odd = [1, 3, 5];
const nums = [2 ,4 , 6].concat(odd);

// cloning arrays
const arr = [1, 2, 3, 4];
const arr2 = arr.slice()
```
### Shorthand:
```javascript
// joining arrays
const odd = [1, 3, 5 ];
const nums = [2 ,4 , 6, ...odd];
console.log(nums); // [ 2, 4, 6, 1, 3, 5 ]

// cloning arrays
const arr = [1, 2, 3, 4];
const arr2 = [...arr];
```

Unlike the `concat()` function, you can use the spread operator to insert an array anywhere inside another array.

```javascript
const odd = [1, 3, 5 ];
const nums = [2, ...odd, 4 , 6];
```

You can also combine the spread operator with ES6 destructuring notation:
```javascript
const { a, b, ...z } = { a: 1, b: 2, c: 3, d: 4 };
console.log(a) // 1
console.log(b) // 2
console.log(z) // { c: 3, d: 4 }
```

# Mandatory Parameter Shorthand
By default, JavaScript will set function parameters to undefined if they are not passed a value. Some other languages will throw a warning or error. To enforce parameter assignment, you can use an if statement to throw an error if undefined, or you can take advantage of the ‘Mandatory parameter shorthand’.

### Longhand:
```javascript
function foo(bar) {
  if(bar === undefined) {
    throw new Error('Missing parameter!');
  }
  return bar;
}
```

### Shorthand:

```javascript
// This function can be used generally
mandatory = () => {
  throw new Error('Missing parameter!');
}

foo = (bar = mandatory()) => {
  return bar;
}
```

# Array.find Shorthand
If you have ever been tasked with writing a find function in plain JavaScript, you would probably have used a for loop. In ES6, a new array function named find() was introduced.

### Longhand:
```javascript
const pets = [
  { type: 'Dog', name: 'Max'},
  { type: 'Cat', name: 'Karl'},
  { type: 'Dog', name: 'Tommy'},
]

function findDog(name) {
  for(let i = 0; i<pets.length; ++i) {
    if(pets[i].type === 'Dog' && pets[i].name === name) {
      return pets[i];
    }
  }
}
```
### Shorthand:
```javascript
pet = pets.find(pet => pet.type ==='Dog' && pet.name === 'Tommy');
console.log(pet); // { type: 'Dog', name: 'Tommy' }
```

# Object [key] Shorthand
Did you know that Foo.bar can also be written as Foo['bar']? At first, there doesn’t seem to be a reason why you should write it like that. However, this notation gives you the building block for writing re-usable code.

Consider this simplified example of a validation function:
### Longhand:
```javascript
function validate(values) {
  if(!values.first)
    return false;
  if(!values.last)
    return false;
  return true;
}

console.log(validate({first:'Bruce',last:'Wayne'})); // true
```
This function does its job perfectly. However, consider a scenario where you have very many forms where you need to apply the validation but with different fields and rules. Wouldn’t it be nice to build a generic validation function that can be configured at runtime?

### Shorthand:
```javascript
// object validation rules
const schema = {
  first: {
    required:true
  },
  last: {
    required:true
  }
}

// universal validation function
const validate = (schema, values) => {
  for(field in schema) {
    if(schema[field].required) {
      if(!values[field]) {
        return false;
      }
    }
  }
  return true;
}


console.log(validate(schema, {first:'Bruce'})); // false
console.log(validate(schema, {first:'Bruce',last:'Wayne'})); // true
```

Now we have a validate function we can reuse in all forms without needing to write a custom validation function for each.

# Double Bitwise NOT Shorthand
Bitwise operators are one of those features you learn about in beginner JavaScript tutorials and you never get to implement them anywhere. Besides, who wants to work with ones and zeroes if you are not dealing with binary?

There is, however, a very practical use case for the Double Bitwise NOT operator. You can use it as a replacement for `Math.floor()`. The advantage of the Double Bitwise NOT operator is that it performs the same operation much faster. You can read more about Bitwise operators here.

### Longhand:
```javascript
Math.floor(4.9) === 4  //true
```

### Shorthand:
```javascript
~~4.9 === 4  //true
```

# Exponent Power Shorthand
Shorthand for a Math exponent power function:

### Longhand:
```javascript
Math.pow(2,3); // 8
Math.pow(2,2); // 4
Math.pow(4,3); // 64
```

### Shorthand:
```javascript
2**3 // 8
2**4 // 4
4**3 // 64
```

# Converting a String into a Number
There are times when your code receives data that comes in String format but needs to processed in Numerical format. It’s not a big deal, we can perform a quick conversion.

### Longhand:
```javascript
const num1 = parseInt("100");
const num2 =  parseFloat("100.01");
```
### Shorthand:
```javascript
const num1 = +"100"; // converts to int data type
const num2 =  +"100.01"; // converts to float data type
```

# Object Property Assignment
Consider the following piece of code:
```javascript
let fname = { firstName : 'Black' };
let lname = { lastName : 'Panther'}
```

How would you merge them into one object? One way is to write a function that copies data from the second object onto the first one. Unfortunately, this might not be what you want — you may need to create an entirely new object without mutating any of the existing objects. The easiest way is to use the `Object.assign` function introduced in ES6:

```javascript
let full_names = Object.assign(fname, lname);
```

You can also use the object destruction notation introduced in ES8:
```javascript
let full_names = {...fname, ...lname};
```
There is no limit to the number of object properties you can merge. If you do have objects with identical property names, values will be overwritten in the order they were merged.

# Bitwise IndexOf Shorthand
When performing a lookup using an array, the `indexOf()` function is used to retrieve the position of the item you are looking for. If the item is not found, the value `-1` is returned. In JavaScript, `0` is considered ‘falsy’, while numbers greater or lesser than `0` are considered ‘truthy’. As a result, one has to write the correct code like this.

### Longhand:
```javascript
if(arr.indexOf(item) > -1) { // Confirm item IS found

}

if(arr.indexOf(item) === -1) { // Confirm item IS NOT found

}
```
### Shorthand:
```javascript
if(~arr.indexOf(item)) { // Confirm item IS found

}

if(!~arr.indexOf(item)) { // Confirm item IS NOT found

}
```

The bitwise(~) operator will return a truthy value for anything but -1. Negating it is as simple as doing !~. Alternatively, we can also use the includes() function:

```javascript
if(arr.includes(item)) { // Returns true if the item exists, false if it doesn't

}
```

# Object.entries()
This is a feature that was introduced in ES8 that allows you to convert a literal object into a key/value pair array. See the example below:
```javascript
const credits = { producer: 'John', director: 'Jane', assistant: 'Peter' };
const arr = Object.entries(credits);
console.log(arr);

/** Output:
[ [ 'producer', 'John' ],
  [ 'director', 'Jane' ],
  [ 'assistant', 'Peter' ]
]
**/
```

# Object.values()
This is also a new feature introduced in ES8 that performs a similar function to Object.entries(), but without the key part:
```javascript
const credits = { producer: 'John', director: 'Jane', assistant: 'Peter' };
const arr = Object.values(credits);
console.log(arr);

/** Output:
[ 'John', 'Jane', 'Peter' ]
**/
```

# Array.reduce()
The `reduce()` method executes a `reducer` function (that you provide) on each element of the array, resulting in single output value.

The reducer function takes four arguments:

- Accumulator
- Current Value
- Current Index
- Source Array

Your reducer function's returned value is assigned to the accumulator, whose value is remembered across each iteration throughout the array, and ultimately becomes the final, single resulting value.

```javascript
# Syntax
arr.reduce(callback( accumulator, currentValue, [, index[, array]] )[, initialValue])
```

### Longhand
```javascript
const value = 0;

const numbers = [5, 10, 15];

for(let i = 0; i < numbers.length; i++) {
  value += numbers[i];
}
```

### Shorthand
```javascript
/* this is our initial value i.e. the starting point*/
const initialValue = 0;

/* numbers array */
const numbers = [5, 10, 15];

/* reducer method that takes in the accumulator and next item */
const reducer = (accumulator, item) => {
  return accumulator + item;
};

/* we give the reduce method our reducer function
  and our initial value */
const total = numbers.reduce(reducer, initialValue)
```

# Pseudo Switch Statement
Dynamically Adding Cases to a pseudo switch Statement

### Code Example
```javascript
var callbacks = {};

function add(_case, fn) {
   callbacks[_case] = callbacks[_case] || [];
   callbacks[_case].push(fn);
}

function pseudoSwitch(value) {
   if (callbacks[value]) {
      callbacks[value].forEach(function(fn) {
          fn();
      });
   }
}

// you can add new code case-block, using:
add('something', function() {
   // case for something
});
```

# Suggest One?
I really do love these and would love to find more, so please, if you have any, please do edit and push to this Git Repository. :heart:
