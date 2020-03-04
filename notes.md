# `Api-design in node`

## Resources

- [Slides](https://slides.com/scotups/api-design-in-node-with-express-v3)
- [Nodejs](https://nodejs.org/en/)
- [Express](https://expressjs.com/)
- [MongoDB](https://www.mongodb.com/)

## What is an API?

- Application programming interface
- tldr: a server that creates an HTTP interface for interacting with some data, basic operatings like Create, Read, Update and Destroy(CRUD).

### REST API

- Basically definition of POST, GET, PUT, very blurred.
- tldr most popular API design pattern, very blurry.
- An API design that combines DB resources, route paths, and HTTP verbs to allow applications to describe what action they are trying to perform.
- Works with basic data models, hard to scale with complex data models and client requirements.

### Node js and APIS

- tldr build for high concurrent APIs that are not CPU intensive

1. Node.js is Javascript, it's async and event driven
2. Single threaded(can optimize)
3. not great for CPU intensive work
4. when kept async, Node can handle a high amount of concurrent request
5. so many open source tools to help build APIs

### Express

- tldr the standard API framework for Node.js
- Handles all the tedious tasks like managing sockets, route matching, error handling etc. Huge community and open source and not going anywhere anytime soon

### MongoDB

- tldr the go to non-relational DB, works well with Node.js
- non-relational document store that is easy to get started and scales well
- open source and backed by a big company, tons of hosting solutions
- ORM/ODM and other libs are some of the best for any DB.

### Middleware ?

- tldr list of functions that execute in order, before your controllers
- Allow you to execute functions on an incoming request with guaranteed order
- Great for authenticating, transforming the request, tracking, error handling
- Middleware can also respond to request like a controller would, but that is not their intent.
- like the `app.use(json())` or `app.use(cors())` can transform request

### REST routes with Express

- tldr; Express was designed with REST in mind and has all you need
- express has a robust route matching system that allows for exact, regex, glob and parameter matching
- It also supports HTTP verbs on a route based level, together with the routing, you can create REST APIs.
- Routes match in the order that they were defined(top to bottom)
- For abstraction, Express allows you to create sub routers that combine to make a full router, Middleware can be added to any and all routes with many different configurations.

### Router

- Route order matters, first one that matches runs. Must mount router `app.use('/api', router);
-

## Coding

Set up get and post for localhost
For post checks can use Insomnia or Postman
using insomnia to hit post on localhost:3000 to get back our message

### Routing

- branch - `lesson-2`
- test command - `yarn test-routes` or `npm run test-routes`

This exercise will have you creating routes and sub routers for our soon the be DB resources using Express routing and routers

- [ ] create a router for the Item resource
- [ ] create full crud routes and create placeholder controllers
- [ ] mount router on the root server
- [ ] ensure all tests pass by running test command

### Create Schemas

- branch - `lesson-3`
- test command - `yarn test-models` or `npm run test-models`

In this exercise, you'll be taking what you learned about Mongoose and MongoDb to create a schema and model for the Item resource.

- [ ] create a schema for the item resource
- [ ] add the correct fields (look at test)
- [ ] add the correct validations (look at test)
- [ ] _extra_ add compund index to ensure all tasks in a list have unique names
- [ ] ensure all tests pass by running test command

### Controllers

- branch - `lesson-4`
- test command - `yarn test-controllers` or `npm run test-controllers`

So far we have routes and models. Now we need to hook our routes up to our models so we can perfom CRUD on the models based on the routes + verbs. That's exactly what controllers do.

- [ ] create CRUD resolvers in `utils/crud.js`
- [ ] create controllers for the Item resources using the base crud resolvers
- [ ] ensure all tests pass by running test command

### Authentication

- branch - `lesson-5`
- test command - `yarn test-auth` or `npm run test-auth`

In this exercise you'll be locking down our API using JWT's.

- [ ] create a signup controller
- [ ] create a signin controller
- [ ] create a protect middlware to lock down API routes
- [ ] ensure all tests pass by running test command

### Testing

The other resources don't have any test, go ahead and write some!

```js
{
  name: String,
  required: true,
  createdBy: mongoose.Types.ObjectId()
}

```

### CRUD controllers

#### Create

- model.create(), new model

```js
import { Item } from './item.model'
Item.create([{}, {}, {}])
```

#### READ

- model.find(), model.findById(), model.findOne()

#### Update

- model.update(), model.findByIdAndUpdate(), model.findOneAndUpdate()

#### Delete

- model.remove(), model.findByIdAndUpdate(), model.findOneAndRemove()

## JWT Token

- tldr tokens passed to every request to check auth on the server, bearerToken. Api will verify token to be sure it is valid
- jsonwebtoken package, `jwt.sign`, `jwt.verify`

## Frameworks

- hapi
- jsonwetoken, npm jwt
- postgress, mySQL, etc.
