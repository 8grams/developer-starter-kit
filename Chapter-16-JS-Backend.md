# Back-end Development

Many things can happen inside back-end or server. It usually intended for heavy workload processing of front-end. One of them has been discussed earlier in __database processing__. This chapter discussed things which might be exist in back-end.

## Microservices architecture

Actually, microservices architecture does not have any differences with SOA (Service Oriented Architecture). They are conceptually the same, but the implementation is different since they both created at the different era. Conceptually, both refers to distribute application into services which might be interact to provide integrated functionalities. Separation into services makes application more robust and easier to debug since developer must distribute application into independent service so that any failure in functionalities can be traced back to services failures.

```
                    +------------+
                    |    User    |
                    +------------+
                           ^
                           |
                           V
                +---------------------+
                |    User Interface   |
                +---------------------+
                          ^
                          |
                          V
+---------------------------------------------------------+
| Application             |                               |
|                +--------------------+                   |
|      +-------->| Controller/Manager |<------+           |
|      |                  ^                   |           |
|      |                  |                   |           |
|      V                  V                   V           |
|  +---------+       +---------+      +---------+         |
|  | Service | <-->  | Service | <--> | Service |         |
|  +---------+       +---------+      +---------+         |
|                                                         |
+---------------------------------------------------------+
```

Services are defined using communication protocol together with higher level abstraction to expose service to outside parties (eventhough outside parties in microservices architecture is parties inside the same application). SOA also uses the same concept but at that time, it deals more with Web specification, therefore a term to describe SOA realization is web services.

Oh the other side, eventhough microservices has the same concept, it deals more with _continuous delivery_, _modular programming_, and _DevOps principles_. It mostly uses PaaS and IaaS technology in its deployment. Almost any programming language now support this architectural style. In JavaScript, developer may uses __Seneca__ (http://senecajs.org/) or __cote__ (http://cote.js.org/). More available as _npm package_ in https://www.npmjs.com/browse/keyword/microservices. They both provides all-in-one necessary packages for microservices (including service locator, etc). If needed, developer may also be able to use only RESTful API and / or GraphQL to expose service and that is all - only service exposure.

## Web Application

A Web application is a multi-tier application. It consists of (usually) three tier:
- __View__ (the Web page, the part where user can use browser to see the view).
- __Model__ (Data storage and manipulation).
- __Controller__ (business logic).

Those three component usually also known as __MVC__ (Model-View-Controoler), Basically, this is how it works:

```
User --> View / Web UI --Request--> Controller
             ^                          |
             |                 +-----------------+
             |                 |                 |
             |           Business Logic        Model
             |          \___________________________/
             |                         |
             |                         V
             |                      Response
             |                        |
             +------------------------+
```

To implement this architecture, some frameworks exist in JavaScript:
- MeteorjJS
- hapijs
- Express.js
- and many others.

In this chapter, we will use one example using Express.js. As always, create an directory and then do __npm init__ inside the directory:

```
~$ mkdir /project/express-proj
~$ cd /project/express-proj
~$ npm init
```

Answer all of the questions, then install Express.js:

    $ npm install express

This is an example of the simplest applicaton, it just display "Hello" string when user access http://server:3000

```
// app.js
const express = require('express')
const app = express()

app.get('/', (req, res) => res.send('Hello'))

app.listen(3000, () => console.log('Port 3000 initialized and ready!'))
```

To run the application:

    ~$ node app.js

What next?

- Learn about routing (the controller) at: https://expressjs.com/en/guide/routing.html
- Learn DBMS and how to handle data storage and querying. This component will become model.
- Learn about the view. Usually, view is the result of template engine. In Express, pug is the default for template engine. See https://expressjs.com/en/guide/using-template-engines.html.

## RESTful API

__RESTful__ or sometimes also only REST (REpresentational State Transfer) is an architectural style which was created by _Roy T. Fielding_ in his Ph.D dissertation (___"Architectural Styles and the Design of Network-based Software Architectures"___).

REST is an architectural style which uses HTTP as its underlying protocol to communicate between client and server. Client send request in the form of HTTP method (GET, PUST, DELETE, etc) and the contents of the requests. Upon arrival, server get the request and do something based on the method. For example, client may sent HTTP GET to __/employees__. Server knows that client requests __/employees__ with GET as its method. The server handle the request by GETting all of employees data and send them as the response. When client requests __/employee/1__ and HTTP method is DELETE then server handler will delete employee data with ID=1.

To expose RESTful API (Application Programming Interface), developer may use any HTTP server or maybe also Web framework. The only requirement is they are able to capture HTTP request from client and provide the way to handle them. In __Express.js__, RESTful API is handled using routing. See https://expressjs.com/en/guide/routing.html for more documentation. Here is an example of how developer my provide GET from http://server/employees to return all employees data in JSON.

```
const express = require('express' )
const app = express()

var employees = require('path/to/your/employees.json');
app.get('/employees', (req, res) => res.send(employees) )

app.listen(3@00, () => console.log('Employees RESTful API active on port 3000!'))
```

## GraphQL

__GraphQL__ is a query language for API which was created by Facebook. It is used to describe and expose data to client, hence graphql-client and graphql-server. This spec also uses HTTP as the underlyting protocol but there is no other HTTP methods other than GET and POST. The specification reside on top of HTTP although HTTP is not always the preferred way since GraphQL makes it possible to use other communication protocol. The reference implementation of GraphQL server is _graphql-js_ (https://github.com/graphql/graphql-js).


 
