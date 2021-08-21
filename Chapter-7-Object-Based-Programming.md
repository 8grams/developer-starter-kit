# Prototype-Based Programming in JavaScript

Initially, JavaScript uses prototype extensively for reusable component / code. Later in ES6, JavaScript as the dialect of ES start to use normal OOP using class construct. More on this later.

## What Is Prototype-Based Programming?

Prototype-based programming is a stype of OOP (Object-Oriented Programming). In prototype-based programming, object hold a very important role. Sometomes, PBP is considered the same as Object-based Programming in which object is used to encapsulate state and operations. OBP does not support inheritance or subtyping (subclass in OOP).

PEP provides support for reusable code (inheritance) by reuse existing object via delegation that serve as __prototype__. This __prototype__ act as a template which can be extended to include properties specific to the extension. Since PBP in JavaScript is implemented in object, an understanding of object in JavaScript is important.

## Understanding JavaScript Object

An object in JavaScript is used to store unordered list of primitive data types as key-value pairs. Each key-value pairs item is called property. Inside object, function can also be defined. If function is defined inside the object, it will be called __method__.

For one and simple definition, direct definition like the source code below is enough.

```
> var person = {
... firstName: 'Zaky',
... middleName: 'Ahmad',
... lastName: ‘Aditya’,
... address: 'Kalasan, Yogyakarta’,
... drive: function() {
..... console. log('mountain bike’);
..... }
... }
undefined
> person
{ firstName: 'Zaky',
middleName: 'Ahmad',
lastName: ‘Aditya’,
address: ‘Kalasan, Yogyakarta’,
drive: [Function: drive] }
> person. firstName
'Zaky'
> person['lastName' ]
'Aditya’
> person.drive()
mountain bike
undefined
>
```

The source code above has the same effect with this:

``` 
> var person = new Object();
undefined
> person.firstName = 'Zaky';
'Zaky'
> person.middleName = 'Ahmad';
'Ahmad'
> person.lastName = 'Aditya’;
‘Aditya’
> person.address = 'Kalasan, Yogyakarta’;
'Kalasan, Yogyakarta’
> person.drive = function() {
... console. Llog('mountain bike’);
... }
[Function]
> person
{ firstName: 'Zaky',
middleName: 'Ahmad',
lastName: 'Aditya’,
address: 'Kalasan, Yogyakarta’,
drive: [Function] }
> person. firstName
'Zaky'
> person.drive()
mountain bike
undefined
>
```

However, problem may arise if we want to create more than instance. In this case, we would be better if we create object using constructor pattern below.

```
> function Person (theFirstName, theMiddleName, theLastName, theAddress, theDrive) {
... this.firstName = theFirstName;
... this.middleName = theMiddleName;
... this. LastName = theLastName;
... this.address = theAddress;
... this.drive = function() {
.....  console. log(theDrive);
..... }
...}
undefined
> Person
[Function: Person]
> var zaky = new Person('Zaky','Ahmad', 'Aditya', 'Kalasan, Yogyakarta', 'mountain bike');
undefined
> zaky
Person {
    firstName: ‘Zaky',
    middleName: 'Ahmad',
    lastName: ‘Aditya’,
    address: ‘Kalasan, Yogyakarta’,
    drive: [Function] }
> zaky.drive()
mountain bike
undefined
> zaky.firstName
'Zaky'
>
```

## Prototype

In JavaScript, prototype can be used for inheritance purpose.

```
> function Person (theFirstName, theMiddleName, theLastName, theAddress, theDrive) {
... this.firstName = theFirstName;
... this.middleName = theMiddleName;
... this.lastName = theLastName;
... this.address = theAddress;
... this.drive = function() {
..... console. log(theDr ive) ;
..... }
... }
undefined
> var zaky = new Person('Zaky','Ahmad', 'Aditya','Kalasan, Yogyakarta', 'mountain bike');
undefined
> zaky.drive()
mountain bike
undefined
> Person.prototype.showFullName = function() {
... console. log(this.firstName + ' ' + this.middleName + ' ' + this.lastName);
... }
[Function]
> Person
[Function: Person]
> zaky.showFullName()
Zaky Ahmad Aditya
undefined
>
```