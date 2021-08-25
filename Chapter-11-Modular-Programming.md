# Modular Programming in JavaScript

Modular programming is common in any programming language. Almost any mainstream programming language has constructs for modular programming. JavaScript also has features for modular programming although it may more complex than any other programming language because of its origin in multitier (front-end to back-end), browser support (means JavaScript engine support), specification, module solution, etc. In this chapter we will discuss some important things in JavaScript modular programming

## What is Modular Programming?

Modular programming is a programming technique to separate program into components each with specific funtionality. The programming language which handle this separation also provides construct that enable developer to use the component. The component is independent and can be used everywhere, therefore it must be loosely-coupled.

Independecy is a hard requirement of module, eventhough in its implementation it may needs other component. Therefore, dependency management is a must in any package manager in any programming language. The component sometimes called __component, package, module, library__, to name a view. In JavaScript, it is usually called package or module. Component can be a class with a set of properties and methods, or a set of functions, or a set of objects.

Developers usually use modular programming for these purposes:

- Maintainability
- Avoiding namespace collision
- Reusable component.

Generally, in JavaScript world, there are __CommonjJS__ and __AMD__ handle modular programming. _CommonJs_ is not for asynchronous, while _AMD_ for asynchronous. Later on, there is __UMD__ to support both CommonJS and AMD features. CommonJS and AMD exist since JavaScript does not embrace syntax and semantic for modules.

## CommonJS

CommonJS (http://www.commonjs.org/) is initially developed by Kevin Dangoor, a Mozilla engineer to handle JavaScript outside browser environment. Example of the implementation is Node.js package. CommonJS has compact syntax and designed for synchronous loading.

## AMD

AMD (Asynchronous Module Definition) is another specification of module in JavaScript (pre ES6). Its syntax is more complex but it is meant to be used and loaded asynchronously. RequireJS (http://requirejs.org/) is an example implementation which is also possible to be used outside browser.

## UMD

UMD (Universal Module Definition - https://github.com/umdjs/umd) tries to handle both features of CommonJS and AMD, therefore it claims to be able to be used in client, server, and any other environment. Some of its implementation and variation can be seen in its repo.

## Module in ES6

In ES6, JavaScript module is handled natively in its specification. This is a good thing since now developers has one specific solution. In the long run, it is hoped that JavaScript ecosystem is much more simple. An example of this module syntax can be seen below (taken from ExploringJS):

```js
//----- lib.js ------
export const sqrt = Math.sqrt;
export function square(x) {
    return x * x;
}

export function diag(x, y) {
    return sqrt(square(x) + square(y));
}

//------- main.js ------
import { square, diag } from 'lib';
console.log(square(11)); // 121
console.log(diag(4, 3)); // 5
```

ReactJS (and React Native) use this module with the help of __BabelJS__.