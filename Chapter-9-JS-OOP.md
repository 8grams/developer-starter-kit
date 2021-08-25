# Object-Oriented Programming in JavaScript

__Object-oriented Programming_ (OOP) usually refers to class-based. Initially JavaScript does not have this semantic but since ES6, class is defined in ES specification. In OOP, developer define blueprint of an object with class and then whenever there is a need to create an object, a keyword is used to instantiate an object. If needed, a class can be subclassed so that inheritance can be fulfilled. OOP uses natural way of thinking: an object has properties (features - like a person need to have ID, address, etc) and also able to do something (called method) such as student is capable of reading the manual. An abstraction is used to draw the line so that a blueprint can be described in a class.

A mechanism of class and instance / object can be described below:

```
      +-----------+              +------------------+
      |  Class A  | ------------ |    Volkswagen    |
      +-----------+              +------------------+
            |                             |
            V                             V
    +---------------+          +----------------------+
    | instance of A | -------- | Volkswagen AB 123 ZA |
    +---------------+          +----------------------+
```

For inheritance, once a class is inherited from base class, it has the whole properties and methods of class plus properties and methods specific to that class.

```
      +-----------+              +------------------+
      |  Class A  | ------------ |       Car        |
      +-----------+              +------------------+
            |                             |
            V                             V
    +---------------+          +----------------------+
    | subclass of A | -------- |      Volkswagen      |
    +---------------+          +----------------------+
```

## Class Definition

Class can be defined using class reserved word. JavaScript execute constructor when a new object is instantiated. If no constructor, then JavaScript will insert __constructor() {}__ which means empty constructor. See this example:

```
> class Person {
... constructor(theFirstName, theMiddleName, theLastName, theAddress) {
.... this.firstName = theFirstName;
.... this.middleName = theMiddleName;
.... this.lastName = theLastName;
.... this.address = theAddress;
.... }

... getFullName() {
..... return this.firstName + this.middleName + ' ' + this.lastName;
..... }
... printName() {
..... console. log(this.getFullName());
..... }
... }
undefined

> Person
[Function: Person]
> var zaky = new Person('Zaky', 'Ahmad', 'Aditya', 'Kalasan', 'Yogyakarta');
undefined
> zaky.printName();
Zaky Ahmad Aditya
undefined
>
```

Beside class declaration form above, there is also class expression like this:

```js
const Person = class {
    constructor(theFirstName, theMiddleName, theLastName, theAddress) {
        this.firstName = theFirstName;
        this.middleName = theMiddleName;
        this.lastName = theLastName;
        this.address = theAddress;
    }

    getFullName() {
        return this.firstName + this.middleName + this.lastName;
    }
    
    printName() {
        console.log(this.getFullName());
    }
}

var zaky = new Person('Zaky','Ahmad','Aditya','Kalasan');
zaky.printName();
```
or:

```js
var Person = class {
    constructor(theFirstName, theMiddleName, theLastName, theAddress) {
        this.firstName = theFirstName;
        this.middleName = theMiddleName;
        this.lastName = theLastName;
        this.address = theAddress;
    }
    
    getFullName() {
        return this.firstName + this.middleName + this.lastName;
    }
    
    printName() {
        console.log(this.getFullName());
    }
}

var zaky = new Person('Glend', 'Steven', 'Maatita', 'Surabaya');
zaky.printName();
```

Please note that both ways of class definition is not __hoisted__, means that class should be defined first before its usage.

## Inheritance / Subclassing

Inheritance can be done via extends keyword. Here is an example:
 
```js
var Person = class {
    constructor(theFirstName, theMiddleName, theLastName, theAddress) {
        this.firstName = theFirstName;
        this.middleName = theMiddleName;
        this.lastName = theLastName;
        this.address = theAddress;
    }
    
    getFullName() {
        return this. firstName + this.middleName + this.lastName;
    }
    
    printName() {
        console.log(this.getFullName());
    }
}

var zaky = new Person('Glend', 'Steven', 'Maatita', 'Surabaya');
zaky.printName();

class Programmer extends Person {
    constructor(theFirstName, theMiddleName, theLastName, theAddress, theProfession) {
        super(theFirstName, theMiddleName, theLastName, theAddress);
        this.profession = 'Programmer';
    }
    
    printProfession() {
        this.printName();
        console.log(this.profession)
    }
}

var tannenbaum = new Programmer('Andrew', 'S', 'Tannenbaum', 'Kalasan', 'Programmer');
tannenbaum. printProfession();
```

## Abstract Subclass / Mix-ins

There is no abstract class in JavaScript. To workaround this limitation, developer can throw an error object in a method which needs to be implemented. Here is an example of error because of unimplemented "abstract" method:

```js
class Person {
    constructor(theFirstName, theMiddleName, theLastName, theAddress) {
        this.firstName = theFirstName;
        this.middleName = theMiddleName;
        this.lastName = theLastName;
        this.address = theAddress;
    }
    
    getFullName() {
        return this.firstName + this.middleName + this.lastName;
    }
    
    printName() {
        console.log(this.getFullName());
    }
    
    printComplete() {
        throw new Error('You have to implement printComlete() method! ');
    }
}

var zaky = new Person('Glend', 'Steven', 'Maatita', 'Surabaya');
zaky.printName();

class Programmer extends Person {
    constructor(theFirstName, theMiddleName, theLastName, theAddress, theProfession) {
        super(theFirstName, theMiddleName, theLastName, theAddress);
        this.profession = 'Programmer';
    
    }
    
    printProfession() {
        this.printName();
        console. log(this.profession);
    }
}

var tannenbaum = new Programmer('Andrew', 'S', 'Tannenbaum', 'Kalasan', 'Programmer');
tannenbaum. printComplete();
```

This example below is an example of "abstract" method which has been implemented:

```js
class Person {
    constructor(theFirstName, theMiddleName, theLastName, theAddress) {
        this.firstName = theFirstName;
        this.middleName = theMiddleName;
        this.lastName = theLastName;
        this.address = theAddress;
    }
    
    getFullName() {
        return this.firstName + this.middleName + this.lastName;
    }    
    
    printName() {
        console.log(this.getFullName());
    }
    
    printComplete() {
        throw new Error('You have to implement printComlete() method! ');
    }
}

var zaky = new Person('Glend', 'Steven', 'Maatita', 'Surabaya');
zaky.printName();

class Programmer extends Person {
    constructor(theFirstName, theMiddleName, theLastName, theAddress, theProfession) {
        super(theFirstName, theMiddleName, theLastName, theAddress);
        this.profession = 'Programmer';
    }
    
    printProfession() {
        this.printName();
        console.log(this.profession);
    }
    
    printComplete() {
        this.printName();
        console.log(this.address);
        console.log(this. profession);
    }
}

var tannenbaum = new Programmer('Andrew', 'S', 'Tannenbaum', 'Kalasan', 'Programmer');
tannenbaum. printComplete();
```