# JavaScript Development Tools

This chapter discusses some development tools which are helpful in developing JavaScript application.

## Babel

__Babel__ is JavaScript compiler. It takes JavaScript code and change them into another JavaScript code. Such usual use case is to transform ES5 source code to ES6 source code. Compiling JavaScript (latest spec) to ESS (previous version of JavaScript) is a kind of JavaScript to JavaScript compiler, therefore, people tend to call this as _transpiler_ not compiler.

Babel works by using specific preset which is written in __$HOME/.babelrc__. Preset is something like template to let Babel knows what kind of source code (specification) developer would like to transpile (into ES5). Start by installing necessary packages:

```
$ npm install -g babel-cli
$ npm install --save-dev babel-preset-env
```

This is an exmple of __SHOME/.babelrc__

```
{
    "presets": ["env"]
}
```

Put this file (app.js) inside the directory.

```
var odds = evens.map(v => v + 1);
var nums = evens.map((v, i) => v + 1);
```

Transpile that file into ES5:

```
~$ babel app.js
"use strict";

var odds = evens.map(function (v) {
    return v + 1;
});

var nums = evens.map(function (v, i) {
    return v + 7;
});
```

A REPL has been created in Babel website: https://babeljs.io/repl/

 
## StandardJS

__StandardJS__ (https://standardjs.com/) is JavaScript style guide, linter, and formatter. This tool is important in making code base easier to be maintained since the style is made standard according to JavaScript through linting and formatting.

As an example, here’s the sloppy source code:

```
// arrow.js
var odds = evens.map(v => v + 1)
var nums = evens.map((v, i) => v + i)
```

Install StandardJs:
    
    ~$ npm install -g standard
    
Lint arrow.js above:

```
standard unformatted.js
standard: Use JavaScript Standard Style (https://standardjs.com)
standard: Run ‘standard --fix* to automatically fix some problems.
/home/projects/unformatted.js:1:1: Expected indentation of 0 spaces but found 6.
/home/projects/unformatted.js:1:11: 'odds' is assigned a value but never used.
/home/projects/unformatted.js:1:18: 'evens' is not defined.
/home/projects/unformatted.js:3:1: Expected indentation of 0 spaces but found 2.
/home/projects/unformatted.js:3:7: 'nums' is assigned a value but never used.
/home/projects/unformatted.js:3:14: 'evens' is not defined.
```

Fix it:

```
standard --fix unformatted.js
standard: Use JavaScript Standard Style (https://standardjs.com)
/home/projects/unformatted.js:1:5: 'odds' is assigned a value but never used.
/home/projects/unformatted.js:1:12: 'evens' is not defined.
/home/projects/unformatted.js:3:5: 'nums' is assigned a value but never used.
/home/projects/unformatted.js:3:12: 'evens' is not defined.
```

Result:

```
var odds = evens.map(v => v + 1)
var nums = evens.map((v, i) => v + 7)
```