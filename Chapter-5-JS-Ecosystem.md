# JavaScript Ecosystem

This chapter is used to discuss JavaScript ecosystem. Not only requiring an interpreter per se, but to become an effective JavaScript developer, one must also understand JavaScript tooling. This chapter discuss the tooling around JavaScript.

## JavaScript Development Tools

Basically, so many categories exist for development tools. They refer to any software tool which available to help developers in developing software based on specific programming language. The hardest part would be to integrate all of those tools into development workflow. Some of them are already integrated into software bundle, while most developers choose ready-to-use packages and assemble them into their own workflow. Therefore, one might has different tooling preferences.
compares with other developers.

- __Integrated Development Environment (IDE)__. This kind of software is a ready-to-use software tool which provides editor, compiler/interpreter, profiler, debugger, help system / documentation, package manager, version control system enabled, and many other kind of software tools into one big integrated system. Example of IDE includes _IntelliJ IDEA, Eclipse,
Netbeans_, etc.
- __Self assembly.__ Developer usually has their own tooling specific for their own workflow. Minimally, they need to have compiler / interpreter, text editor with syntax highlighting and completion, library / package manager, and build system. For example, one might use _Visual Studio Code_ with plugins for JavaScript development after he/she install NodeJS (includes __npm__ or __yarn__) and _gulp.js_. Developers might also use _Atom_ editor based development environment or _Vim_ or _Emacs_ or _textadept_ or _Sublime Text_, etc. See later discussion for development tools.

## More on JavaScript Platform

For consistency, we will refer to Node.js as JavaScript platform throughout this handbook. Node.js
currently consists of two types of software release:

- __LTS (Long Term Support)__. This release is intended for enterprise and organization which more reluctant towards frequent release since it may create some unstable and breakage. It consists of stable and battle tested components.
- __Stable latest / current__. This release is intended for people or organization who are not afraid of breakage and unstable features. This release ships with latest stable feature. Developers use it if they want to use latest stable features in programming language specification (ES) eventhough not all latest ES spec usually supported.

More info about (including end-of-life) these releases are available at https://github.com/nodejs/Release

Installation guides for any platforms are available at download page (https://nodejs.org/en/download/). Although developer is free to use any installation methods, we prefer installation method from binary release which are available at Node.js landing page (https://nodejs.org). After download those two releases, extract at some location (__/opt/software/node/nodejs-lts__ for LTS version, we refer that as __$NODEJS_HOME_LTS__, and __/opt/software/node/nodejs-stable__ for CURRENT version. we refer that as __$NODEJS_HOME_STABLE__):

```
$ mkdir /opt/software/node
$ cd /opt/software/node
$ tar -xvf $PATH_TO_DOWNLOADED_BIN_PKG/node-v<LTS-VERSION>
$ mv node-v<LTS-VERSION> nodejs-1ts
$ tar -xvf $PATH_TO_DOWNLOADED_BIN_PKG/node-v<CURRENT-VERSION>
$ mv node-v<CURRENT-VERSION> nodejs-stable
```

Create two files to set environment variables: nodejs-stable for CURRENT version, and nodejs-lts for LTS version. Here, they will reside in __$HOME/env__.

_file: SHOME/env/nodejs-stable_

```
NODEJS_HOME=/opt/software/node

export PATH=$HOME/bin: $PATH: $NODEJS_HOME/nodejs-stable/bin
export MANPATH=$MANPATH: $NODEJS_HOME/nodejs-stable/man
```

_file: $HOME/env/nodejs-its_

```
NODEJS_HOME=/opt/software/node

export PATH=$HOME/bin: $PATH: $NODEJS_HOME/nodejs-1ts/bin
export MANPATH=$MANPATH: $NODEJS_HOME/nodejs-1ts/man
```

After this, to use Node.js, open terminal and source file needed, for example if you want to use CURRENT version:

    source ~/env/nodejs-stable

In other terminal, you may use another version:

    source ~/env/nodejs-1ts

## Package Manager

Basically, developers tend to create module in packages so that they can reuse them (more on module later). The package can be a library or an executable application. As JavaScript can be used
for front-end and also back-end, the package manager for JavaScript also can be categorized into front-end package manager and non front-end package manager.

### npm (Node Package Manager)

__npm__ is package manager for NodeJS. It comes as default package manager when a developer install NodeJS. Original creator of npm is _Isaac Z. Schlueter_ and now currently maintained and improved by __npm, Inc__ and community. __npm, Inc__ also provides repository / registry for free / open source libraries, private, and enterprise. npm cli usually deals with those libraries in npm, Inc server.

__npm__ install in 2 location:

- Global, the same as Node.js installation, therefore they usually accesible and can be executed. All installed files are in __$NODEJS_HOME/bin__ for executable executable symlinks and __$NODEJS_HOME/lib/node_modules__ for all files.
- Local / project based, reside in a _ project directory. All files will be in __$PROJECT_HOME/node_modules__ directory.

Central to npm is a file named package.json which is used to describe all related packaging rules of the software. Therefore, in eveery project, a package.json file should exist in project root directory. Below is an example of package.json file inside GraphQL.js package (see https://github.com/graphql/graphql-js):

```
{
  "name": "graphql",
  "version": "16.0.0-alpha.5",
  "description": "A Query Language and Runtime which can target any service.",
  "license": "MIT",
  "private": true,
  "main": "index",
  "module": "index.mjs",
  "types": "index.d.ts",
  "sideEffects": false,
  "homepage": "https://github.com/graphql/graphql-js",
  "bugs": {
    "url": "https://github.com/graphql/graphql-js/issues"
  },
  "repository": {
    "type": "git",
    "url": "https://github.com/graphql/graphql-js.git"
  },
  "keywords": [
    "graphql",
    "graphql-js"
  ],
  "engines": {
    "node": "^12.22.0 || ^14.16.0 || >=16.0.0"
  },
  "scripts": {
    "preversion": ". ./resources/checkgit.sh && npm ci",
    "version": "node resources/gen-version.js && npm test && git add src/version.ts",
    "fuzzonly": "mocha --full-trace src/**/__tests__/**/*-fuzz.ts",
    "changelog": "node resources/gen-changelog.js",
    "benchmark": "node benchmark/benchmark.js",
    "test": "npm run lint && npm run check && npm run testonly && npm run prettier:check && npm run check:spelling && npm run check:integrations",
    "lint": "eslint --cache --max-warnings 0 .",
    "check": "tsc --pretty",
    "testonly": "mocha --full-trace src/**/__tests__/**/*-test.ts",
    "testonly:cover": "nyc npm run testonly",
    "prettier": "prettier --write --list-different .",
    "prettier:check": "prettier --check .",
    "check:spelling": "cspell --no-progress '**/*'",
    "check:integrations": "npm run build:npm && npm run build:deno && mocha --full-trace integrationTests/*-test.js",
    "build:npm": "node resources/build-npm.js",
    "build:deno": "node resources/build-deno.js",
    "gitpublish:npm": "bash ./resources/gitpublish.sh npm npmDist",
    "gitpublish:deno": "bash ./resources/gitpublish.sh deno denoDist"
  },
  "devDependencies": {
    "@babel/core": "7.14.6",
    "@babel/eslint-parser": "7.14.7",
    "@babel/plugin-syntax-typescript": "7.14.5",
    "@babel/plugin-transform-typescript": "7.14.6",
    "@babel/preset-env": "7.14.7",
    "@babel/register": "7.14.5",
    "@types/chai": "4.2.19",
    "@types/mocha": "8.2.2",
    "@types/node": "15.12.5",
    "@typescript-eslint/eslint-plugin": "4.25.0",
    "@typescript-eslint/parser": "4.25.0",
    "chai": "4.3.4",
    "cspell": "5.6.6",
    "eslint": "7.29.0",
    "eslint-plugin-import": "2.23.4",
    "eslint-plugin-internal-rules": "file:./resources/eslint-internal-rules",
    "eslint-plugin-istanbul": "0.1.2",
    "eslint-plugin-node": "11.1.0",
    "eslint-plugin-tsdoc": "0.2.14",
    "mocha": "9.0.1",
    "nyc": "15.1.0",
    "prettier": "2.3.2",
    "typescript": "4.3.4"
  }
}
```

Developer may find the contents of the file are quite self-explanatory. See __package.json__ documentation for more info at https://docs.npmjs.com/files/package.json

A __package.json__ file can be created by using this command (this should be done first time only in project root directory):

    $ npm init

Then answer all questions. If one wants to assume "yes" or default contents, then add __--yes__. To change the contents, use:

```
$ npm set init.author.email "dev@8grams.dev"
$ npm set init.author.name "8grams Dev"
```

Using __npm__ cli, developer can manage package / library and their dependencies as well as other information which might be needed (a.k.a metadata). Here’s some usage of npm command, add __-g__ for global installation (see manual first, not necessarily can always be done for local and global):

```
$ npm install express 
$ npm uninstall express 
```

If one wants to save package name into package.json, add --save as the paramater:

```
$ npm install express --save
$ npm uninstall express --save
```

To search for packages, use:

    $ npm search packagename

More information can be seen at documentation site (https://docs.npmjs.com/). See also __npm --help__.

### yarn

__yarn__ is another package manager for NodeJS. It was initially developed by Facebook and made open source in 2016. It is now become one of mostly used package manager since it has focus on fast, reliable, and secure package management. Some benchmarks show that _yarn_ is faster then _npm_ (see for example https://www.sitepoint.com/yarn-vs-npm/), but this may change in the future.

To install yarn the easiest way, just use npm:

    $ npm install -g yarn

The result is yarn cli in global location. From this point, one can use, for example:

    $ yarn install packagename

For more information, you may use this:

```
$ yarn --help
$ yarn help install
```

### Bower

__Bower__ (https://bower.io) is package manager for front-end development. It has many users but currently in a state of maintenance and Bower team itself recommends using _yarn_ and _webpack_ for front-end projects. The blog post which explains how to migrate can be seen at https://bower.io/blog/2017/how-to-migrate-away-from-bower/

Bower has similar commands with npm. To install Bower, use npm:

    $ npm install -g bower

To install package in current directory:

    $ bower install jquery

After package installation, package will be install in default location: __$PROJECT_HOME/bower_components__. This might be checked by front-end developer so that they may use right location. See bower help for more info.

### Duo

Duo (http://duojs.org/) is package manager for front-end development. This software seems to be stuck from its commit time in GitHub (https://github.com/duojs/duo).

### jspm

jspm is package manager which uses SystemJS universal module loader. It can load any module format such as _ES6, AMD, CommonJs, and globals_. For production releases, this tool can also be used as bundler. More information available at https://jspm.io and its source code available at https://github.com/jspm/jspm-cli.

## Build Tool

Build tool software (also known as __build automation tool__) is a kind of software which is used by developer in automating the creation of software package release. The end result will be software package release but it is also usually used by developer in development process and its range of usage include run the software, testing, file operations, command line operations, software packaging, etc. Some build tools in JavaScript world are:

- __Brunch__ (hitps://brunch.io)
- __Grunt__ (https://gruntjs.com/)
- __Gulp__ (https://gulpjs.com/)

## Bundler

Bundler in JavaScript world is usually used to bundle front-end assets (HTML, CSS, etc) into one package for easy distribution. Some of active projects in this category are:

- __Webpack__ (https://webpack.js.org/)
- __ParcelJS__ (https://parceljs.org)
- __Browserify__ (http://browserify.org)
- __rollup.js__ (https://rollupjs.org/guide/en)

### Notes on Categorization

Since software development activities are complex and many too vendors / communities are improved their project, developers may find those tools categorization are not strict. They may usually span across more than one categorization. For example, __jspm__ is package manager but also can be used as bundler, __ParcelJS__ is bundler but can also be used as build tool, even one may use __brunch__ to bundle front-end package with the help of other command line tools.

## Front-end Development

JavaScript initially used for browser which is why it has strong domination in front-end development. Front-end part in an application is used to interact with users directly. Basically,
front-end consists of Web application front-end and mobile application front-end but usually people tend to use Web application for front-end development. To this end, many JavaScript software frameworks and libraries are available to help developers in developing front-end Web application but currently, developers usually use these frameworks / libraries very much:

- __Angular__ (https://angular.io/), available in JavaScript and TypeScript.
- __React__ (https://reactjs.org/)
- __Ember.js__ (https://www.emberjs.com/)
- __Vue.js__ (https://vuejs.org/)
- __Backbone.js__ (http://backbonejs.org/)

In its operation, front-end frameworks / libraries usually fetch data from network / back-end, therefore they have close relationship with back-end.

## Back-end Development

Back-end and front-end are the result of tiered application model. Usually, for better maintainability and scalability, application is developed using common development patterns, and the most common development pattern is to separate application into components. Using tiered application model, application usually separated into __view__ (for UI - user interaction), __controller__ (for business logic), and __model__ (for data access). View components are reside in front-end, while others are back-end.

```
            +--------------+     +--------------------------+
 User ->    |  front-end   | ->  | - backend: user request  |
            +--------------+     |   received by controller |
                    ^            | - controller may access  |
                    |            |   database or not        |
                    |            | - upon finishing, send   |
                    |            |   response to front-end  |
                    |            +--------------------------+
                    |                         |
                    |_________________________|
```

Therefore, for back-end development, these things are important:

- __Data serialization__: what kind of data format will be used between front-end and back-end. Currently, JSON is used extensively.
- __Protocol for communication between front-end and back-end__, usually HTTP(S) is used as the foundation but still need higher level abstraction such as RESTful API (see Express.js and Hapi.js for example) and GraphQL (see GraphQL.js for JavaScript library for GraphQL).
- __Database access__, depends on condition, developer may use ORM software for SQL access, direct SQL commands using SQL database driver, or vendor specific query language such as JavaScript for MongoDB, Foxx (based on JavaScript) for ArangoDB.
- __Messaging and RPC__, is used for remote procedure call inside server back-end, for example Node.js package for gRPC.
- __Architecture related__, is used to implement specific architectural pattern such as Seneca.js for microservices.

## CLI Application Development

CLI (Command Line Interface) is a kind of user interface which used in console / terminal / text-based software. Basically, this kind of development span from only simple command line and terminal / console based application with menu. Node.js also provides libraries for that purposes:

- __commander.js__ (https://github.com/tj/commander.js/), used for command line only.
- __Inquirer.js__ (https://github.com/SBoudrias/Inquirer.js), provides library for interactive command line such as requesting input, etc.
- __blessed__ (http://blessedjs.org/), provides complete text user interface library.
- __terminal-kit__ (https://github.com/cronvel/terminal-kit), provides library for colorful and interactive terminal-based user interface.

## GUI / Desktop Application Development

Communities and vendors also provide libraries for GUI (Graphical User Interface) application development. GUI provides richer user interface since it supports graphical computing
environment. Some libraries available for that purpose:

- __Electron__ (https://electronjs.org/), used by Atom Editor (https://atom.io) and Visual Studio Code.
- __NW.js__ (previously node-wehkit, https://nwjs.io/)

## Mobile Application Development

NodeJS can also be used to develop mobile application. Currently. mobile phone applications are develop for Android and / or iOS. Some frameworks exist in JavaScript to ease the development of cross platform native or hybrid mobile application. Native application is specific for mobile platform while hybrid is based on webview (displayed using web browser component). Some frameworks / libraries are available:

- __React Native__ (http://facebook.github.io/react-native/), used to build native mobile application using JavaScript. One codebase (in JavaScript) can be deployed into 2 platform (Android and iPhone). The result is native application
- __NativeScript__ (https://www.nativescript.org/), used to build native mobile application using JavaScript or TypeScript. This framework can also be used to deploy native application to Android and iPhone.
- __Apache Cordova__ (https://cordova.apache.org/), used to build hybrid mobile application.

## Other Tools

Some other tools exist in JavaScript world, for example:

- __Documentation tools__: JSDoc (http://usejsdoc.org/), jGrouseDoc  (http://jster.net/library/jgrousedoc), YUIDoc (http://yui.github.io/yuidoc/), Docco (https://jashkenas.github.io/docco/).
- __Testing tools__: Jasmine (https://jasmine.github.io/), Mocha (https://mochajs.org/).
- __Debugger__: JavaScript Debugger (https://developer.mozilla.org/en-US/docs/Tools/Debugger),  Chrome Dev Tools (https://developers.google.com/web/tools/chrome-devtools/)
- __Security tools__: RetireJS (http://retirejs.github.io/retire.js/)
- __Code optimization / analysis tools__: ESLint (http://eslint.org/), Flow (https://flow.org/).