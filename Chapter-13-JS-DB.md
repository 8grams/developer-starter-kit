# Accessing Database

Database software (or somtimes DBMS - Database Management System) is a kind of software which provides container and runtime to handle data. Since many computing tasks involve I/O and data operation, DBMS has been developed since the beginning of computing era to handle data workload. This chapter is used to discuss how to handle database using

## What is DBMS?

A database is a set of organized data. To be able to organize data, developer needs software to handle that task. The software is called __Database Software__ or Database Management Software (DBMS). From this point, we will refer DBMS to point that kind of software. A DBMS needs to be able to handle data storage and query. In a more complex scenario, it should be able to handle distributed nature of data. Developer should learn how to store and retrieve data. A language usually created to handle those tasks. The problem is, so many data models (how data is organized) that a single language to handle those tasks are not enough. Therefore, vendors create their language for their DBMS. This leads to confusion since developer needs to learn more than one language and interoperabiliy is minimal. To this end, some specification exist. The most common and canonic specification is __SQL__. More on this later.

## DBMS Categorization

Generally, DBMS exist to store and manipulate data based on specific data model (although some DBMS also claim to be multimodels). Although this categorization is common enough in software development world, they are not necessarily strictly groupped like that.

### SQL

__SQL__ (Structured Query Language) is used to define and manipulate structured data model. This kind of DBMS is used in conjunction with relational data model defined in _Edgar F. Codd_ paper in 1970 (titled "A Relational Model of Data for Large Shared Data Banks"). It has __DDL__ (Data Definition Language) where developer may define database, tables, and their relationships altogether. This is done by using normalization process and put tables (normalization result) into SQL command to define data container (DDL). Other type of command is __DML__ (Data Manipulation Language) to manipulate data inside database.

SQL became international standard in ANSI SQL (since 1986) and ISO SQL since 1987. Latest specification as of March 2018 is SQL 2016.

## NoSQL

__NoSQL__ (sometimes also "NOSQL" or "Non SQL" or "non relational") is a category of DBMS which handles semi structured, unstructured, and non relational data model. This kind of DBMS has no standard and developer must prepare to learn each of them since they define their own query and storage model. This kind of DBMS exist since not all problems suitable with structured and relational data model. This is because so many problems (existing probles such as data for AI and new problem such as graph data for social networking) exist and they can not be solved effectively using SQL DBMS. Complete list of NoSQL DBMS can be seen at http://nosq|-databases.org/.

## NewSQL

__NewSQL__ is a brand new category which enforce __ACID__ (Atomicity, Consistency, Isolation, Durabiliry) of SQL database while still possible for scalability of NoSQL DBMS. Just as its name implies, NewSQL still uses SQL command but usually are more scalable then traditional SQL system. Some examples are:

- CockroachDB
- Google Spanner
- TiDB

## Using JavaScript for DBMS Operation

### SQL with MySQL / MariaDB

There is a driver which can be used by Node.js developer to connect and doing query on MySQL / MariaDB database. See https://github.com/mysqljs/mysql for the repo and examples.

### NoSQL with MongoDB

To use MongoDB with Node.js, developer may use Mongoose as its library to access MongoDB data. See http://mongoosejs.com/ for more information. In this example, we will populate data first and then use an example source code to access employees data.

```
~$ mongo
MongoDB shell version v3.6.3\
connecting to: mongodb://127.0.0.1:27017
MongoDB server version: 3.6.3
Welcome to the MongoDB shell.
For interactive help, type "help".
For more comprehensive documentation, see http://docs.mongodb.org/
Questions? Try the support group http://groups.google.com/group/mongodb-user
> db
test
> use mydb
switched to db mydb
> show dbs
admin 0.000GB
local 0.000GB
> empl = { name : "Glend", address : "Gubeng Kertajaya" }
{ "name" : "Glend", "address" : "Kertajaya" }
> emp2 = { name : "Steven", address : "Gubeng", email : "steven@gmail.com" }
{ "name" : "Steven", "address" : "Gubeng", "email" : "steven@gmail.com" }
> emp3 = { name : "Maatita", address : "Surabaya", phone: "085686995585" }
{ "name" : "Maatita", "address" : "Surabaya", "phone" : "085686995585" }
> db.employees.insert( emp1 )
WriteResult({ "nInserted" : 1 })
> db.employees.insert( emp2 )
WriteResult({ "nInserted" : 1 })
> db.employees.insert( emp3 )
WriteResult({ "nInserted" : 1 })
> show dbs
admin 0.000GB
local 0.000GB
mydb 0.000GB
> show collections
employees
> db.employees.find()
{ "_id" : ObjectId("5aa9b47bc58fc8679cc3ee14"), "name" : "Glend", "address" : "Kertajaya" }
{ "_id" : ObjectId("5aa9b47ec58fc8679cc3ee15"), "name" : "Steven", "address" : "Gubeng", "email" : "steven@gmail.com" }
{ "_id" : ObjectId("5aa9b483c58fc86/9cc3ee16"), "name" : "Maatita", "address" : "Surabaya", "phone" : "@085686995585" }
> db.employees.findOne()
{
    "id" : ObjectId("5aa9b47bc58fc86/9cc3ee14"),
    "name" : "Glend",
    "address" : "Kertajaya"
}
> db.employees.find().limit(2)
{ "_id" : ObjectId("5aa9b47bc58fc8679cc3ee14"), "name" : "Glend", "address" : "Kertajaya" }
{ "_id" : ObjectId("5aa9b47ec58fc8679cc3ee15"), "name" : "Steven", "address" : "Gubeng", "email" : "steven@gmail.com" }
>
```

An example of how developer may use Node.js to get all of those employees data:

```js
var mongoose = require('mongoose'),
    Schema = mongoose.Schema;

mongoose.connect('mongodb://localhost/mydb' );

var employeeSchema = new Schema({
    name: String,
    address: String,
    phone: String,
    email: String
});

var Employee = mongoose.model('Employee', employeeSchema);

Employee. find(function(err, employees) {
    console. log(employees) ;
});
```