# Asynchronous Programming in JavaScript

Asynchronous programming also known as non-blocking is the opposite of synchronous programming or blocking. Another term which refers to asynchronous programming is non- sequential.

## What is Asynchronous Programming?

Asynchronous programming is a form of __asynchrony__ which refers to events outside normal program flow. Those events may occur from another concurrent program or maybe bacause of input/output which needs to be processed and probably takes time. In runtime, if this I/O operation is not handled properly, program flow will wait until I/O process finish then continue program execution. Asynchronous programming deals with this kind of situation so that program flow shoud not stop if there is I/O process, instead program execution will continue the if I/O is finish, the result will be handled by unit that handle the results.

## How JavaScript Handle Asynchronous Programming

JavaScript normally uses callback function to handle asynchronous problem. However, this callback may leads to unmantained code since readibility is bad, therefore in ES6 adn ES7 specifications, __promises__ and __async/await__ is used.

## Callback

In this method, callback is defined in a function:

```
var fs = require('fs');

// fs.readFile(file[, options], callback)
// file <string> | <Buffer> | <integer> filename or file descriptor
// options <Object> | <string>:
// encoding <string> | <null> default = null
// flag <string> default = 'r
// callback <Function>

console.log('Start reading the file...');
fs.readFile('./pegawai.json', ‘utf-8', function(err, data) {
    if (err) throw err;
    console. log(data);
});
console. log('After reading the file ...');

//result:
//Start reading the file...
//After reading the file ...
//{
//  "pegawai": [
//      {
//          "id": "1",
//          "nama": "Zaky",
//          "alamat": "Purwomartani"
//      },
//      {
//          "id": "2",
//          "nama": "Ahmad",
//          "alamat": "Kalasan"
//      },
//      {
//          "id": "3",
//          "name": "Aditya",
//          "alamat": "Sleman"
//      }
//  ]
//}
```

## Promise

Using promise, asynchronous I/O is done in a function and __Promise__ returned by the function. The __.then__ will be used to check the results, and if there is broken promise then it will be catched in __.catch__. This example below is used to read all of __.txt__ files in a directory and rename them into __.txtp__.

```
var fs = require('fs');

if (process.argv.length <= 2) {
    console.log("Usage: " + __filename + " path/to/directory");
    process.exit(-1);
}

var path = process.argv[2];

function readDirContents() {
    return new Promise(
        function(resolve, reject) {
            fs.readdir(path, function(err, list) {
                if (err) {
                    reject(err);
                } else {
                    resolve(List);
                }
            })
        }
    }
}

readDirContents()
    .then(Llist => {
        for (var i=0; i<list.length; i++) {
            var fullName = path + '/' + list[i];
            var newFullName = fullName + '.txtp';

            fs.rename(fullName, newFullName, (err) => {
                if (err) throw err;
            );
        }
    })
    .catch(err => { console.log(err) });
```

## Async/Await

Async/await is combined with __Promise__ to make results more readable.

```
var fs = require('fs');

if (process.argv.length <= 2) {
    console. log("Usage: " + __filename + " path/to/directory");
    process.exit(-1);
}
var path = process.argv[2];

function readDirContents(thePath) {
    promise = new Promise(function(resolve, reject) {
        fs.readdir(path, function(err, list) {
            if (err) {
                reject(err);
            } else {
                resolve(List);
            }
        })
    });
    return promise
}

var a = main();
async function main() {
    var rdir = await readDirContents(path)
        .then(list => {
            for (var i=@; i<list.Length; i++) {
                console. log(listli]);
            }
        })
        .catch(err => { console.log(err) });
    return rdir;
};
```

## Generators

Generator is an object used to represent sequences. It is generated using __generator function__. A generator function is a function with asterisk after last function character or at the beginning of function name.

```
function *genWithParam(x) {
    x++;
    yield x
    yield x/2;
}

var gwp = genWithParam(5);
console.log(gwp.next());
console.log(gwp.next());
console.log(gwp.next());

function *genNoParam() {
    var a = [1,2,3]
    yield a[Q]
    yield a[1]
    yield a[2]
}

var gnp = genNoParam();
console.log(gnp.next(‘a'));
console.log(gnp.next('b'));
console.log(gnp.next());
console.log(gnp.next());

// results:
// { value: 6, done: false }
// { value: 3, done: false }
// { value: undefined, done: true }
// { value: 1, done: false }
// { value: 2, done: false }
// { value: 3, done: false }
// { value: undefined, done: true }