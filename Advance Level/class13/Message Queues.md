# Message Queues

The main idea behind Socket.IO is that you can send and receive any events you want, with any data you want. Any objects that can be encoded as JSON will do, and binary data is supported too.

## Rooms

The main idea behind Socket.IO is that you can send and receive any events you want, with any data you want. Any objects that can be encoded as JSON will do, and binary data is supported too.

![](https://socket.io/images/rooms.png
)

- to join room :
```
io.on("connection", (socket) => {
  socket.join("some room");
});
```

also we use `to` or `in` (they are the same) when broadcasting or emitting:

```
io.to("some room").emit("some event");
```

emit to several rooms at the same time:
```
io.to("room1").to("room2").to("room3").emit("some event");
```

broadcast to a room from a given socket:

```
io.on("connection", (socket) => {
  socket.to("some room").emit("some event");
});
```

To leave a channel you call `leave` in the same fashion as `join`

Each Socket in Socket.IO is identified by a random, unguessable, unique identifier Socket#id. For your convenience, each socket automatically joins a room identified by its own id.

- broadcast data to each device / tab of a given user

```
io.on("connection", async (socket) => {
  const userId = await fetchUserId(socket);

  socket.join(userId);

  // and then later
  io.to(userId).emit("hi");
});
```

- send notifications about a given entity:

```
io.on("connection", async (socket) => {
  const projects = await fetchProjects(socket);

  projects.forEach(project => socket.join("project:" + project.id));

  // and then later
  io.to("project:4321").emit("project updated");
});
```

### Broadcasting to rooms also works with multiple Socket.IO servers.You just need to replace the default Adapter by the Redis Adapte

![](https://socket.io/images/rooms-redis.png)

The "room" feature is implemented by what we call an Adapter. This Adapter is a server-side component which is responsible for:

storing the relationships between the Socket instances and the rooms
broadcasting events to all (or a subset of) clients

- Starting with `socket.io@3.1.0`, the underlying Adapter will emit the following events:

   - `create-room` (argument: room)
   - `delete-room` (argument: room)
   - `join-room` (argument: room, id)
   - `leave-room` (argument: room, id)



## Namespaces

A **Namespace** is a communication channel that allows you to split the logic of your application over a single shared connection (also called "multiplexing").

![](https://socket.io/assets/images/namespaces-088745a8a8882118740f50b6b1232588.png)

- to create Namespace :

```
const orderNamespace = io.of("/orders");
```

### **Reserved events**

On each side, the following events are reserved and should not be used as event names by your application:

- `connect`
- `connect_error`
- `disconnect`
- `disconnecting`
- `newListener`
- `removeListener`


# References

## [Socket.io Chat Example](https://socket.io/get-started/chat/)

## [Rooms](https://socket.io/docs/v4/rooms)

## [Namespaces](https://socket.io/docs/v4/namespaces/)

## [Socket.io Emit Cheatsheet](https://socket.io/docs/v4/emit-cheatsheet/)

## [Back To Home Page](../../README.md)
