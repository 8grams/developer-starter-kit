# Functional Programming in JavaScript

JavaScript is not intended for functional programming language, however there are functional programming features which can be implemented in JavaScript but since JavaScript also support other paradigm (imperative, OOP, Prototype-based Programming), purely functional features are not necessarily enforced.

## What is Functional Programming?

Functional programming is programming paradigm which rooted from mathematical functions, immutability, and avoids changing-state. Doing so can improve understanding and prediction of program behaviour. Although almost any programming language has function, it does not mean that they are functional programming languages. Embrace functional programming language is more depends on functional programming way of thinking except when a developer use a purely functional programming language such as Haskell in which a developer is forced to write program in functional style. In multiparadigm programming language, they are harder because developers are free to use any programming style. JavaScript is multiparadigm so developer may find more than one programming style. The downside is, it will reduce readibility and maintainability.

## Pure and Impure Function in JavaScript

Function can be pure or impure. Function is said to be pure function if it has no side-effects (any operation which has no relationship with the goal of the function, such as writing to a log file, or manipulation of unpredictable resources such as I/O, etc).

```js
var fs = require('fs');

// this is pure function, it always return
// the same results no matter what, provided
// that the parameter is the same

function square(operand) {
    return operand*operand;
}

// the result is always 400
console.log(square(2));
console.log(square(20));
console.log(square(20));
console.log(square(20));
console.log(square(20));
console.log(square(20));
console.log(square(20));
console.log(square(20));

// This is impure function since it has side-effects
// (read input from a file), it makes behaviour
// unpredictable
function impureSquare(origin) {
    var contents = fs.readFileSync(origin, 'utf8');
    return contents*contents;
}
```

Immutability

Immutability is core in functional programming. It refers to an object which is immutable (can not be changed after object is created and initialized). Therefore, an object should be copied into another new object to avoid object mutability. This will increase predictability of runtime and can leads to easier debugging process. In JavaScript, developer may use const, Object.freeze, for example to make immutable object.

## Recursion

In programming, recursion refers to calling function inside its own function. The case of recursion usually involves something like factorial:

```js
var factorial = function(number) {
    if (number <= 0) {
        return 1;
    } else {
        return (number * factorial(number - 1));
    }
};
```

## Higher-order Functions

Higher-order function (also known as *functor) is function which uses one or more function(s) asits parameter / argument or provide function as a return value.

```
function forEach(array, action) {
    for (var i = 0; i < array.length; i++) {
        action(array[i]);
    }
    
    function print(word) {
        console.log(word);
    }
    
    function makeUpperCase(word) {
        console.log(word. toUpperCase());
    }
    
    forEach(["satu", "dua", "tiga"], print);
    forEach(["satu", "dua", "tiga"], makeUpperCase);
}
```

Currying

Currying allows partial application of a function’s arguments. Developer may create function that pass all of the arguments or a subset of argument and get back a function that waits for the rest of the arguments.

```js
// Slightly modified from:
// http://javascriptweblog.wordpress.com/2018/04/05/
// curry-cooking-up-tastier-functions/

function toArray(fromEnum) {
    return Array.prototype.slice.call(fromEnum);
}

Function.prototype.curry = function() {
    if (arguments.length<1) {
        return this; //nothing to curry with - return function
    }
    
    var __method = this;
    var args = toArray(arguments);
    
    return function() {
        return __method.apply(this, args.concat(toArray(arguments)));
    }
}

var add = function(a,b) {
    return a + b;
}

//create function that returns 1@ + argument
var addTen = add.curry(10);
var addTwoNumbers = add(1,4);
console.log(addTen(30));
console.log(addTwoNumbers);
```

## Library for Functional Programming

There are some well-developed libraries to ease developer in applying functional programming principles in JavaScript. There is a dedicated repo in GitHub for that purpose: https://github.com/stoeffel/awesome-fp-js