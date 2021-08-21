 # JavaScript Overview

This chapter is used to give an overview of JavaScript so that the reader has a comprehensive view about JavaScript. Although this chapter has no direct connection with coding / programming,
readers need to understand this chapter in order to understand the big picture which could ease them in understanding the detals of JavaScript.

## What is JavaScript?

JavaScript is a high level programming language. It covers multiparadigm in programming. Programming paradigm invonves the point of view of how developers develop source code during their software development activities. Some of paradigm in programming are:

1. Object-Oriented Programming (OOP)
2. Prototype-Based Programming (PBP)
3. Functional Programming (FP)
4. ...and many more.

The fact that JavaScript is high level programming language shows that JavaScript uses mostly human language (english) for its syntax. JavaScript is interpreted, means that source code will be interpreted and executed directly by interpreter without compiling into native machine code (binary executable). JavaScript has the following features:

- __Dynamically typed__: verification of type is done at runtime, implies that coding is easier since developer can use and change type of variable without the need to cast the type although this will makes it possible to result in runtime error.
- __Weakly typed__: does not check the type of a variable before performing an operation on it.
- __Multi-paradigms__: JavaScript supports prototype-based, object-oriented, and functional programming paradigms.
- __Multi-layer__: JavaScript is used in front-end and back-end application development.
- __Multi-platform__: JavaScript available in most computing devices and operating system that exist in this world.

## What Problems Suitable for JavaScript?

At first, JavaScript is used only to be embedded inside web page to support dynamic HTML. Currently JavaScript can be used in the following problems domain:

- __Web page / front-end__: JavaScript is used together with HTML, CSS, and any other Web standards to display contents of web page. JavaScript now is the only language that exist in every major web browser. JavaScript function in this problem domain is to make web page more dynamic and interactive by allowing components processing dynamically (button submit, etc) and also __AJAX__ (Asynchronous JavaScript and XML) so that interaction between users and server does not need to send / receive the whole page, instead only changing component (textarea, for example, can be used to receive input and send the input to server, then put the contents into another component. See Facebook comments for example). There are many front-end frameworks in JavaScript available, such as _ReactJS (from Facebook), VueJS, Angular_, etc.
- __Mobile application development__: JavaScript is used in ReactNative and NativeScript to create native mobile application. If developers want webview, then they can use something like _Apache Cordova_.
- __Server side script__: JavaScript can be used also for server side / back-end development using __NodeJS__. Some architecture patterns on the server also supported by JavaScript such as _gRPC, microservices, RESTful API, GraphQL_, etc.
- __Database query language__: some databases use JavaScript as the query language, for example _MongoDB_ and _Apache CouchDB_.
- __Robotics__: some frameworks available for robot programming, such as _CylonJS, Nodebots, and Johny-Five_.
- __IoT / Internet of Things__: IoT is internetworking physical devices, especially embedded devices into other electornics devices. Johny-file also used as IoT framework.
- __Operating System shell script__: JavaScript can also be used as script to be executed directly on top of JavaScript interpreter to handle administrative tasks on the command line.
- __Graphics / Visualization__: Library such as _D3_ is often used for data visualization. Other libraries are also available: _Processing.js, p5.js_, etc.
- __Big Data / Data Science__: although JavaScript is not usually used in data science, some libraries are available also, for example _Flurry analytics, percipio, bloom.js, Apache Spark Node binding, or AriesJS_.
- __Artificial Intelligence__: JavaScript also seldom used in AI, but there are some libraries available, for example, _deeplearn.js_.
- __Scientific Computing__: JavaScript also weak in _Scientific Computing_ although some libraries are available, such as: _mathjs, numeric, number.js, science.js_, etc.
- __Desktop Application__: see Electron and nwjs for example.

## JavaScript Strengths and Weaknesses

Strengths and weaknesses sometimes are very subjective matter, so please treat this discussion lightly.

#### Strengths
- Relatively easy to study
- Relatively fast
- One programming langage for front-end and back-end

#### Weaknesses
- Inconsistent, sometimes it fails silently.
- Some complaints on dynamic and weakly typing.
- Some complaints on integers and floating-point number.
- Callback hell
- Complex runtime environment, especially for front-end code.

## JavaScript Standardization

JavaScript is a dialect of __ECMAScript__ (ES). In the world of programming language, usually there is a standard body (official or not) to define programming language specification. ES is the specification, developed by Ecma International, an international standard organization (used to be _European Computer Manufacturers Association_, but now just __Ecma__). ES is the result of JavaScript standardization since sometimes ago there was problem with Netscape (JavaScript) and Microsoft (JScript).

As a specification, ES only provides specification but not the software. So now, there is no ES software but JavaScript as the dialect of ES. Other implementations are: _ActionScript, JScript, QtScript, or InScript_. Javascript is implemented by many vendors as JavaScript engine which will be discussed later.

Currently, many vendors still implement ES5 (version 5.1). Since 2015, Ecma published ES6 (later renamed to ES2015), also known as __ES6 Harmony__. Later on __ES7__ or _ES2016_ is published on June 2016. In June 2017, ES8 is published. There are lots of confusion in JavaScript engine support and people usually use tool like _Babel.js_ to convert between those editions.

## JavaScript Interpreter / Engine

As an interpred language, an interpreter is needed to execute JavaScript source code. The software that provides facility to interpret JavaScript code is usually caled JavaScript engine. Many JavaScript engines are available.

- __V8__
- __Rhino__
- __SpiderMonkey__
- __JavaScriptCore / Nitro__
- __KDEJS Engine / KJS__
- __Chakra__
- __Nashorn__

## JavaScript Platform / Runtime Environment

JavaScript platform / runtime consists of JavaScript engine, libraries, and package manager. Its purpose is to provide the runtime environment to run JavaScript source code while also provide libraries for software development and tool to manage them. Although not always a must, currently
__NodeJS__ is usually used. NodeJS consists of V8 JavaScript engine, event-loop for non-blocking I/O / asynchronous programming, and npm as its package manager. This makes it suitable for server side programming.