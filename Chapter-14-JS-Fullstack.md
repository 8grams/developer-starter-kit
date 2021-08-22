# Full-stack Application Development

This chapter discuss software stack or tier which form a complete software product. Generally a software product does not stand alone by itself. It usually consists of more than one solution stack except for very simple software stand alone text-based and GUI software.

## What is Full-stack?

The term full-stack (sometimes maybe fullstack, multi-tiered) is a terminology which refers to solution stack for software product which comprise of front-end and back-end part of the software product. Front-end (FE) deals with providing users with interface so that users can communicate with the software. FE sends request(s) to back-end (BE) which responsible for logic and data processing workload. Between FE and BE, there should be a communication protocol and data serialization to send requests - receive responses. For BE to be able in request processing, there should be a mechanism to expose service whether they need to be accessed directly or via middleware (proxy).

## JavaScript for Front-End

JavaScript enables developer to build front-end stack. Currently, in FE, developer may use JavaScript for:
- __Mobile front-end__ (React Native, NativeScript, Apache Cordova)
- __Web front-end__ (ReactJS, Angular, Vue, EmberJS)
- __Text-based / terminal__ (Commander, terminal-kit, blessed)
- __GUI__ (Electron, NW,js)


## Data Serialization and Communication Protocol

Many data serialization is available and one mostly used currently is JSON. JSON is native JavaScript format so JavaScript developer should not feel difficult to handle it. Other serialization formats are:
- MessagePack
- Google Protocol Buffer
- Cap 'n Proto
- Apache Thrift
- Binary JSON (BSON)
- XML
- and many more.

For communcation protocol between FE and BE, usually involves standard which is in application layer of _TCP/IP_. The use of standard such as __HTTP/2__ is considered important so that both FE and BE can reuse readily available components (http client and http server). For internal BE, there are more loosely requirements since everything usually controlled for example developer may use _gRPC_ on top of _HTTP/2_.

## JavaScript for Back-End

JavaScript can also be used for back-end processing using Node.js and frameworks / libraries for back-end processing. In this side, developer usually need to master protocol for BE communication and BE libraries / frameworks to implement specific BE architectural patterns. Some examples:

- Use __database drivers__ / ORM (Object-Relational Mapping) / ODM (Object-Document Mapper) to implement data processing at the BE.
- Use __Seneca.js__ to implement microservices architectural pattern.
- Use __NodeJS__ for gRPC to handle
- Use RESTful API implemented with HapiJS or ExpressJS to expose services from inside.
- Use __GraphQL__ to expose services from inside to outside.
- etc.