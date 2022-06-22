# Event Driven Applications

## **Event-Driven Programming in Node.js**

**Event-Driven Programming** is a logical pattern that we can choose to confine our programming within to avoid issues of complexity and collision

Event-Driven Programming makes use of the following concepts:

- An Event Handler is a callback function that will be called when an event is triggered.
- A Main Loop listens for event triggers and calls the associated event handler for that event.

Node.js natively provides us with a useful module called `EventEmitter` that allows us to get started incorporating Event-Driven Programming in our project right away

We access the EventEmitter class through the events module. Once imported we’ll need to create a new object from the class to start using it.

```
const EventEmitter = require('events').EventEmitter;
const myEventEmitter = new EventEmitter;
```

alert new user join a chat room example :

```
const EventEmitter = require('events').EventEmitter;
const chatRoomEvents = new EventEmitter;

function userJoined(username){
  // Assuming we already have a function to alert all users.
  alertAllUsers('User ' + username + ' has joined the chat.');
}

// Run the userJoined function when a 'userJoined' event is triggered.
chatRoomEvents.on('userJoined', userJoined);
```

```
function login(username){
  chatRoomEvents.emit('userJoined', username);
}
```

## **Removing Listeners**

To remove event listeners in EventEmitter we can use the `removeListener` or `removeAllListeners` method.

## Node docs: events

Much of the Node.js core API is built around an idiomatic asynchronous event-driven architecture in which certain kinds of objects (called "emitters") emit named events that cause Function objects ("listeners") to be called.




# References

## [Event-Driven Programming in Node.js](https://www.digitalocean.com/community/tutorials/nodejs-event-driven-programming)

## [Node docs: events](https://nodejs.org/api/events.html)


## [Back To Home Page](../../README.md)
