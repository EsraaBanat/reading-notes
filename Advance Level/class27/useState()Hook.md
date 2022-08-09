# useState() Hook

# Introducing Hooks


**Hooks** are a new addition in React 16.8. They let you use state and other React features without writing a class.

```js
import React, { useState } from 'react';
```

What was the motivation for introducing Hooks?

- Hooks solve a wide variety of seemingly unconnected problems in React that we’ve encountered over five years of writing and maintaining tens of thousands of components.

- With Hooks, you can extract stateful logic from a component so it can be tested independently and reused. **Hooks allow you to reuse stateful logic without changing your component hierarchy**. This makes it easy to share Hooks among many components or with the community.

- Hooks let you split one component into smaller functions based on what pieces are related (such as setting up a subscription or fetching data).

- Hooks let you use more of React’s features without classes.

# Hooks API

##  State Hook

What is a Hook?

**Hooks** are functions that let you “hook into” React state and lifecycle features from function components. Hooks don’t work inside classes — they let you use React without classes

This example renders a counter. When you click the button, it increments the value:

```js
import React, { useState } from 'react';

function Example() {
  // Declare a new state variable, which we'll call "count"
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

## Effect Hook

**The Effect Hook `useEffect`** adds the ability to perform side effects from a function component. It serves the same purpose as `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount` in React classes, but unified into a single API

For example, this component sets the document title after React updates the DOM:

```js
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  // Similar to componentDidMount and componentDidUpdate:
  useEffect(() => {
    // Update the document title using the browser API
    document.title = `You clicked ${count} times`;
  });

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```
When you call useEffect, you’re telling React to run your “effect” function after flushing changes to the DOM. Effects are declared inside the component so they have access to its props and state.

### Name two rules imposed by React Hook usage.

- **Only call Hooks at the top level**. Don’t call Hooks inside loops, conditions, or nested functions.

- **Only call Hooks from React function components**. Don’t call Hooks from regular JavaScript functions. (There is just one other valid place to call Hooks — your own custom Hooks. We’ll learn about them in a moment.)

## Other Hooks

There are a few less commonly used built-in Hooks that you might find useful. For example,

 `useContext` lets you subscribe to React context without introducing nesting:
```js
function Example() {
  const locale = useContext(LocaleContext);
  const theme = useContext(ThemeContext);
  // ...
}
```

And `useReducer` lets you manage local state of complex components with a reducer:
```js
function Todos() {
  const [todos, dispatch] = useReducer(todosReducer);
```
# Using the State Hook

**What is a Hook?** A Hook is a special function that lets you “hook into” React features. For example, useState is a Hook that lets you add React state to function components. We’ll learn other Hooks later.

**When would I use a Hook?** If you write a function component and realize you need to add some state to it, previously you had to convert it to a class. Now you can use a Hook inside the existing function component. 

**What does calling useState do?** It declares a “state variable”. Our variable is called `count` but we could call it anything else, like `banana`. This is a way to “preserve” some values between the function calls — `useState` is a new way to use the exact same capabilities that this.state provides in a class. Normally, variables “disappear” when the function exits but state variables are preserved by React.

**What do we pass to useState as an argument?** The only argument to the `useState()` Hook is the initial state. Unlike with classes, the state doesn’t have to be an object. We can keep a number or a string if that’s all we need. In our example, we just want a number for how many times the user clicked, so pass 0 as initial state for our variable. (If we wanted to store two different values in state, we would call `useState()` twice.)

**What does useState return?** It returns a pair of values: the current state and a function that updates it. This is why we write `const [count, setCount] = useState()`. This is similar to `this.state.count` and `this.setState` in a class, except you get them in a pair.


### Updating State

In a class, we need to call this.setState() to update the count state:
```js
  <button onClick={() => this.setState({ count: this.state.count + 1 })}>
    Click me
  </button>
```

In a function, we already have setCount and count as variables so we don’t need this:

```js
  <button onClick={() => setCount(count + 1)}>
    Click me
  </button>
```

# References

### [Introducing Hooks](https://reactjs.org/docs/hooks-intro.html#motivation)

### [hooks api](https://reactjs.org/docs/hooks-overview.html)

### [the state hook](https://reactjs.org/docs/hooks-state.html)

### [hooks api reference](https://reactjs.org/docs/hooks-reference.html)

## [Back To Home Page](../../README.md)
