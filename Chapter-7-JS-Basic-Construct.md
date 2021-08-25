# JavaScript Basic Constructs

This chapter is used to discuss basic operation and syntax in JavaScript. We will use NodeJS platform for this purpose.

## Overview of Tools

To follow the discussion in this chapter, one should has these minimum requirements:

- __NodeJS__, can be LTS or latest stable
- __Text editor or IDE__

It’s good to have a solid understanding of command line / shell knowledge since most of operation will be done in shell. The source code can be executed using __node__ and / or REPL.

## Execute JavaScript Source Code

Using this mechanism, one should write source code into a file and have them executed using node:

    ~$ node filename.js

If the project is complex enough, __npm__ is recommended. One should preserve one special directory for all project files then inside that directory, do:

    ~$ npm init

and then anwer all the questions.

## Understanding NodeJS REPL

For trivial codebase, one may use REPL (Read-Eval-Print Loop). REPL is executed using __node__:

_File: src/console-log.js_

```
~$ node
> .help
.break      Sometimes you get stuck, this gets you out
.clear      Alias for .break
.editor     Enter editor mode
.exit       Exit the repl
.help       Print this help message
.load       Load JS from a file into the REPL session
.save       Save all evaluated commands in this REPL session to a file
> .load src/ch-03/01-console-log.js @
console.log('hello') ®

hello
undefined
>
```

## Identifier

An identifier is a name to identify an object / thing in programming language syntax. An Identifier has to satisfy these requirements:
- Can only be prefixed with alphanumeric characters or underscore or dollar sign.
- Should not have space(s)

As JavaScript only gives those two rules, some developers / communities / projects / vendors propose their own coding style. For example, it is better to use camelCase for variable name. More can be seen at https://addyosmani.com/blog/javascript-style-guides-and-beautifiers/ and also see Google JavaScript style guide (https://google.github.io/styleguide/jsguide.html).

## Variables

A variable is a container to store a value. JavaScript is scripting language, it has dynamically typed as its typing discipline which means that once the storage (i.e variable) is used to store a value of type X, later on the variable can be used to store another type.

*File: src/variables-declare.js*

```js
var employeeID, employeeName;
let employeeAddress, employeePhone;

console.log(employeeID);
console.log(employeeName);
console.log(employeeAddress);
console.log(employeePhone);

employeeID='123'
employeeName='Mr. X'
employeeAddress='Yogyakarta'
employeePhone=' 123234343'

console.log(employeeID)
console.log(employeeName)
console.log(employeeAddress)
console.log(employeePhone)
```

## Comments

Comment in JavaScript may be written using these rules:
- __//__ for single line or until end of line comment.
- For multilines comment, use this:

```js
...
...
/*
this is
muLtilines
comment
*/
```

## Constant

Constant is used for any identifier which can not be reasigned and redeclared. JavaScript uses const and by convention uses all uppercase for const identifier.

_file: src/const.js_

```js
/*
* const.js
* although possible to use camelCase or Lowercase,
* convention is to use ALL UPPERCASE.
*
* this is still simple, we do not put error catching
*/

const NAME = 'JavaScript';
console.log(NAME)
NAME = 'TypeScript'
console.log(NAME)
```

The result is error:

```
~$ node src/const.js
JavaScript
const.js:13
NAME = 'TypeScript'
^
TypeError: Assignment to constant variable.
at Object.<anonymous> (@3-const.js:13:6)
at Module._compile (module.js:649:30)
at Object.Module. extensions..js (module. js:660:10)
at Module.load (module. js:561:32)
at tryModuleLoad (module. js:501:12)
at Function.Module._load (module.js:493:3)
at Function.Module.runMain (module. js:690:10)
at startup (bootstrap_node.js:194:16)
at bootstrap_node. js:666:3
```

## Expressions and Operators

Expression is any valid statement / syntax in JavaScript which evaluates to a single value. Expression may assign a value to a variable or simply just have value. Expression usually involves
operator which operates on operands (values).

```
> numOfWeeks = 365 / 7
52.14285/14285/146
> 365 /7
52.142857142857146
> console.log(num0fWeeks )
52.14285/714285/146
undefined
>
```

JavaScript provides many operators, Complete operators for JavaScript can be seen at Mozilla Developer Networks website (https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators).

## Literals

Literals are used to represent values. JavaScript has these literals:

- __Array literals__: see data structures
- __Boolean literals__: consists of true and falses
- __Floating-point literals__: numbers with fraction, can be used E and e also for exponential part
- __Integers__: binary (0b), base 10, octal (00), and hexadecimal (Ox) numbers
- __Object literals__: see Object-based programming
- __RegExp literals__: regular expression
- __String literals__: zero or more characters, inside "" or ".

## Conditionals

Conditional statement is used to branch logic of program based on a situation. An example would be the case that someone should not have discount if he/she is not a member.

### Conditional Operator

For simple conditional, use this syntax:

    condition ? expr1 : expr2

```
> var res = 10;
undefined
> (res==10) ? "yes 10" : "not 10"
"yes 10'
>
```

### If Statement

```js
if (condition) {
    ...
    statement which will be executed if condition is true
    ...
```

```js
if (condition) {
    ...
    statement which will be executed if condition is true
    ...
} else {
    ...
    otherwise, this will be executed
    ...
}
```

```js
if (condition1) {
    ...
    statement which will be executed if condition is true
    ...
} else if (condition2) {
    ...
    statement which will be executed if condition is false and condition2 is true
    ...
} else {
    ...
    otherwise, this will be executed
    ...
}
```

### Switch

One may use this statement to evaluate expression and check whether expression result match the specific value.

```js
switch (expression) {
    case a:
        statement if a is matched
        break;
    
    case b:
        statement if b is matched
        break;
    
    default:
        if all else fail
}
```

## Looping

Looping statement is used to repeat a code block until one condition is fulfilled. Looping for is more straight forward, it is used for looping n times, while loopinig while is based on situation.

### Looping for

```
> for (i = 0; i < 5; i++) {
    console. Llog(i);
}

0
1
2
3
4
```

### Looping while

There are two kind of __while__:

```js
while (condition) {
    ...
    statement
    ...
}
```

```js
do {
    ...
    statement
    ...
}
while (condition);
```

## JavaScript Statement Structures

Developer write algorithm (or steps to solve problems) into set of instructions. In JavaScript, those set of instructions is called statements. Although developer may write statement without _semicolon (;)_, it is recommended that semicolon always written to remark end of statement.

### Functions

Basically, __function__ is a specific construct in almost any programming language to define a code block which will be used throughout the codebase. By using function developer abstract the problems into a unit of working solution so that the unit can be used again anywhere. In programming, this kind of solution is called __reusable code__. Basic syntax declaration for JavaScript function:

```js
function functionName(parameters) {
    ...
    statement
    ...
}
```

Function can be declared or be made an expression. The difference is in __function hoisting__. In function declaration, in runtime function always put on top so that any reference to that function is valid. In function as expression, during runtime function is not put on top so that any reference to that function is invalid if it is called before function expression.

JavaScript also makes it possible to define __anynymous function__, a function without a name, to be saved in a variable:

    var f1 = function (a, b) {return a * b};

A self-invoking function also possible so that anytime JavaScript interpreter find the self-invoking function, it will be executed directly.

```js
(function () {
    ...
    statement
    ...
}
```

## Basic Data Type and Structures in JavaScript

JavaScript is a dynamic programming language, means that developer can assign a value of one type and then reassigned the value to another type. This is sometimes also called __loosely-typed__. Eventhough this is simple but it sometimes leads to a weak solution: not quite robust software release.

JavaScript has five primitives data type (in ES6, there is sixth data type: __symbol__) and one object: - Boolean - Null - Undefined - Number - String.

Note that in JavaScript data type primitives, number is double-precision 64-bit floating point format (IEEE 754) and there is no integer data type.

### Array Literals

Array is a kind of indexed collections. JavaScript only provides one dimension array although developer may use array inside array to provide multidimensional arrays. Here is an example of a session with array.

```
> var arrStudents = []
undefined
> arrStudents.length
0
> arrStudents.push(1)
1
> arrStudents.length
1
> arrStudents.push(2,3,4,5)
5
> arrStudents.length
5
> arrStudents
[1, 2, 3, 4, 5 ]
>arrStudents.unshift(0)
6
> arrStudents
[0, 1, 2, 3, 4, 5 J
> arrStudents[0]
0
> arrStudents[1]
1
> arrStudents.unshift(2,"after 2")
8
> arrStudents
[2, 'after 2', 0, 1, 2, 3, 4, 5 ]
> arrStudents.pop()
5
> arrStudents
[ 2, ‘after 2', 0, 1, 2, 3, 4]
>
```

There is also am Array constructor to create and initialize array:

```
> var arrNum1 = new Array()
undefined
> var arrNum2 = new Array(1,2,3,4,"after 4")
undefined
> var arrNum3 = new Array(10)
undefined
> arrNum1
[]
> arrNum2
[ 1, 2, 3, 4, ‘after 4' ]
> arrNum3
[ <10 empty items> ]
>
```

In ES6, there is another type of array which is called __Typed Array__, but this is special, it is used to present and array like view of binary data buffer.