## Review: ES6 Classes :
Classes are a template for creating objects

 the class syntax has two components: 

- class declarations : One way to define a class by using the class keyword with the name of the class
- class expressions :  is another way to define a class. Class expressions can be named or unnamed. The name given to a named class expression is local to the class's body. However, it can be accessed via the name property
- classes must be defined before they can be constructed not like functions
 
- class members that might be inside class body

  1.Strict mode

  2.Constructor

  3.Static initialization blocks

  4.Prototype methods

  5.Generator methods

The extends keyword is used in class declarations or class expressions to create a class as a child of another class.

## Express Routing :

Routing refers to how an application’s endpoints (URIs) respond to client requests

Example of simple route :

```
const express = require('express')
const app = express()

// respond with "hello world" when a GET request is made to the homepage
app.get('/', (req, res) => {
  res.send('hello world')
})
```
### Route methods:

A route method is derived from one of the HTTP methods, and is attached to an instance of the express class.

- GET 
- POST
- DELETE
- PUT
- ALL : used to load middleware functions at a path for all HTTP request methods

Route paths, in combination with a request method, define the endpoints at which requests can be made. Route paths can be strings, string patterns, or regular expressions.

Route handlers : You can provide multiple callback functions that behave like middleware to handle a request

Route handlers can be in the form of a function, an array of functions, or combinations of both,

### **Response methods**
<br>

| Method         | Description                               |   |   |   |   |   |   |   |   |
|----------------|-------------------------------------------|---|---|---|---|---|---|---|---|
| res.download() | Prompt a file to be downloaded.           |   |   |   |   |   |   |   |   |
| res.end()      | End the response process.                 |   |   |   |   |   |   |   |   |
| res.json()     | Send a JSON response.                     |   |   |   |   |   |   |   |   |
| res.jsonp()    | Send a JSON response with JSONP support.  |   |   |   |   |   |   |   |   |
| res.redirect() | Redirect a request.                       |   |   |   |   |   |   |   |   |
| res.render()   | Render a view template.                   |   |   |   |   |   |   |   |   |
| res.send()     | Send a response of various types.         |   |   |   |   |   |   |   |   |
| res.sendFile() | Send a file as an octet stream.           |   |   |   |   |   |   |   |   |
|                |                                           |   |   |   |   |   |   |   |   |


## Using Express Routing :

- Use express.Router() multiple times to define groups of routes
- Apply the express.Router() to a section of our site using app.use()
- Use route middleware to process requests
- Use route middleware to validate parameters using .param()
- Use app.route() as a shortcut to the Router to define multiple requests on a route

## References :
[ES6 Classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)

[Express Routing](https://www.digitalocean.com/community/tutorials/learn-to-use-the-new-router-in-expressjs-4)

[Using Express Routing](https://expressjs.com/en/guide/routing.html)




