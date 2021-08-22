# Testing in JavaScript

The same as another product, software also needs to be tested. Software testing is a classic discussion in software engineering. While software testing has been around since the beginning of software technology, software engineering world massively undergo changing point of view. This chapter is used to discuss that with an example of JavaScript testing tools and frameworks.

## Overview of Software Testing

Software testing is a very complex subject and it is very important since it may be able to detect any bugs and failures of software product. Software testing relates to QA (quality assurance). Therefore, since the beginning, there are many techniques developed to handle software QA. For example:

- Functional and non-function testing
- Based on scope: integration testing, unit testing, component interface testing, system testing, operational acceptance testing.
- White box testing and Black box testing.
- and many others.

Since agile approach signifficantly being common in software development world, software testing also change drastically. In pre-agile, software or source code that implement software functionality has to be exist first and then being tested. In agile approach, things are different. Developer create a skeleton of testing first (which of course 100% failed if run), then one by one create and improve source code until 100% succeed. Currently, some frameworks and testing tools are available to handle that.

## JavaScript Testing Tool and Framework

To handle testing, some vendors and communities has created testing tools and frameworks. Some of them are specific for client side code, while other are for non browser envionment and for both. Testing tools and frameworks sometimes also combined with build tools. There is am overview of them in https://medium.com/welldone-software/an-overview-of-javascript-testing-in-2018-£68950900bc3:

- Provide a testing structure (Mocha, Jasmine, Jest, Cucumber)
- Provide assertions functions (Chai, Jasmine, Jest, Unexpected)
- Generate, display, and watch test results (Mocha, Jasmine, Jest, Karma)
- Generate and compare snapshots of component and data structures to make sure changes from previous runs are intended (Jest, Ava)
- Provide mocks, spies, and stubs (Sinon, Jasmine, enzyme, Jest, testdouble)
- Generate code coverage reports (Istanbul, Jest, Blanket)
- Provide a browser or browser-like environment with a control on their scenarios execution (Protractor, Nightwatch, Phantom, Casper)

The URL for all those tools and frameworks are listed below.

- Mocha: https://mochajs.org/
- Jasmine: https://jasmine.github.io/
- Jest: https://facebook.github.io/jest/
- Cucumber: https://cucumber.io/
- Chai: http://www.chaijs.com/
- Unexpected: http://unexpected.js.org/
- Karma: https://karma-runner.github.io/2.0/index.htm]
- Ava: https://github.com/avajs/ava
- Sinon: http://sinonjs.org/
- enzyme: http://airbnb.io/enzyme/
- testdouble: https://github.com/testdouble/testdouble.js/
- Istanbul: https://github.com/gotwarlost/istanbul
- Blanket: http://blanketjs.org/
- Protractor: https://www.protractortest.org/
- Nightwatch: http://nightwatchjs.org/
- Phantom: http://phantomjs.org/
- Casper: http://casperjs.org/

## Using Jest for Testing

Jest can be used for project specific or from global with Jest CLI. For controlled environment and exercise, one may go to https://repl.it/repls/UnluckyHardChords.