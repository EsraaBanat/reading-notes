## Node introduction :
Node : is an open-source, cross-platform runtime environment that allows developers to create all kinds of server-side tools and application and it's intended for use outside of a browser contex

## Express introduction :
Express : is the most popular Node web framework, and is the underlying library for a number of other popular Node web frameworks

It provides mechanisms to:

- Write handlers for requests with different HTTP verbs at different URL paths (routes).
- Integrate with "view" rendering engines in order to generate responses by inserting data into templates.
- Set common web application settings like the port to use for connecting, and the location of templates that are used for rendering the response.
- Add additional request processing "middleware" at any point within the request handling pipeline.

Express is unopinionated. You can insert almost any compatible middleware you like into the request handling chain, in almost any order you like

A module is a JavaScript library/file that you can import into other code using Node's require() function. Express itself is a module, as are the middleware and database libraries that we use in our Express applications.

The Express application object also provides methods to define route handlers for all the other HTTP verbs:

checkout(), copy(), delete(), get(), head(), lock(), merge(), mkactivity(), mkcol(), move(), m-search(), notify(), options(), patch(), post(), purge(), put(), report(), search(), subscribe(), trace(), unlock(), unsubscribe().


## What is NPM?

NPM (Node Package Manager):the world's largest Software Registry.Open source developers from every continent use npm to share and borrow package

npm consists of three distinct components:

- the website
- the Command Line Interface (CLI)
- the registry


### NPM Uses:

- Adapt packages of code for your apps, or incorporate packages as they are.
- Download standalone tools you can use right away.
- Run packages without downloading using npx.
- Share code with any npm user, anywhere.
- Restrict code to specific developers.
- Create organizations to coordinate package maintenance, coding, and developers.
- Form virtual teams by using organizations.
- Manage multiple versions of code and code dependencies.
- Update applications easily when underlying code is updated.
- Discover multiple ways to solve the same puzzle.
- Find other developers who are working on similar problems and projects.


## What is TDD?

“Test-driven development” refers to a style of programming in which three activities are tightly interwoven: coding, testing (in the form of writing unit tests) and design (in the form of refactoring).

## CI/CD:
CI (Continuous integration) : ensure all changes will integrate

CD (continuous deliver) : is developing to release at any time

## HTTP Status Codes :

1. Informational responses (100–199) :

- 100 Continue

2. Successful responses (200–299) :

- 200 OK 
- 201 Created
- 202 Accepted
- 203 Non-Authoritative Information
- 204 No Content
- 205 Reset Content
- 206 Partial Content

3. Redirection messages (300–399) :

- 300 Multiple Choices
- 301 Moved Permanently
- 302 Found
- 303 See Other
- 304 Not Modifieds

4. Client error responses (400–499) :

- 400 Bad Request
- 401 Unauthorized
- 402 Payment Required
- 403 Forbidden
- 404 Not Found

5. Server error responses (500–599) :

-  500 Internal Server Error
- 503 Service Unavailable
- 505 HTTP Version Not Supported
- 599 Network connect timeout error

## References :

- [Express and Node](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/Introduction)
- [NPM](https://docs.npmjs.com/about-npm)
- [TDD](https://www.agilealliance.org/glossary/tdd/)
- [CI/CD](https://www.youtube.com/watch?v=xSv_m3KhUO8)
- [http status codes](https://www.restapitutorial.com/httpstatuscodes.html)



## [Back To Home Page](../../README.md)
