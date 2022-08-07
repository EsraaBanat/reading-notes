# Component Based UI

# React 

**React** is a JavaScript library, and so we’ll assume you have a basic understanding of the JavaScript language.

### What are the building blocks of a React app?

- Elements.
- Components.

### What is the difference between an element and a React component?

| Element                                                                    | Component                                                                                                                            |
|----------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
| An element is always gets returned by a component.                         | A component can be functional or a class that optionally takes input and returns an element.                                         |
| The element does not have any methods.                                     | Each component has its life cycle methods.                                                                                           |
| A React element is an object representation of a DOM node.                 | A component encapsulates a DOM tree.                                                                                                 |
| Elements are immutable i,e once created cannot be changed.                 | The state in a component is mutable.                                                                                                 |
| An element can be created using React.createElement( ) with type property. | A component can be declared in different ways like it can be an element class with render() method or can be defined as a function.  |
| We cannot use React Hooks with elements as elements are immutable.         | React hooks can be used with only functional components                                                                              |
| Elements are light, stateless and hence it is faster.                      | It is comparatively slower than elements.                                                                                            |


### What are some advantages of React’s component based architecture?

In the case of component based architecture (CBA), responsibility is split on a component-by-component basis. This means that the design, logic, and helper methods exist all within the same level of the architecture (generally the view). As aforementioned, everything that pertains to a particular component is defined within that component’s class.


# JSX

### What is JSX and why do we use it?

**JSX** stands for JavaScript XML.

**JSX** allows us to write HTML in React.

**JSX** makes it easier to write and add HTML in React.

**JSX** allows us to write HTML elements in JavaScript and place them in the DOM without any createElement()  and/or appendChild() methods.

**JSX** converts HTML tags into react elements.

### Describe the process of embedding JavaScript expressions in JSX.

JSX will only accept expressions between curly braces. The curly braces tell our transpiler to process what is between the curly braces as normal JavaScript. Note we cannot write full statements as we might expect, only bits of JavaScript that return a value. Here are a few common types of expressions you may use:

1. Variable and object values
2. Function calls and references
3. Expressions and operators
4. Loops and iteration

### Eample :

```
const name = 'Josh Perez';
const element = <h1>Hello, {name}</h1>;
```
# Rendering Elements

Elements are the smallest building blocks of React apps.

An element describes what you want to see on the screen.

Unlike browser DOM elements, React elements are plain objects, and are cheap to create. React DOM takes care of updating the DOM to match the React elements.

Let’s say there is a `<div>` somewhere in your HTML file:

```
<div id="root"></div>
```
We call this a “root” DOM node because everything inside it will be managed by React DOM.

Applications built with just React usually have a single root DOM node. If you are integrating React into an existing app, you may have as many isolated root DOM nodes as you like.

To render a React element, first pass the DOM element to `ReactDOM.createRoot()`, then pass the React element to `root.render()`:

```
const root = ReactDOM.createRoot(
  document.getElementById('root')
);
const element = <h1>Hello, world</h1>;
root.render(element);
```
It displays “Hello, world” on the page.

## Updating the Rendered Element

React elements are immutable. Once you create an element, you can’t change its children or attributes. An element is like a single frame in a movie: it represents the UI at a certain point in time.

With our knowledge so far, the only way to update the UI is to create a new element, and pass it to `root.render()`.

Consider this ticking clock example:

```
const root = ReactDOM.createRoot(
  document.getElementById('root')
);

function tick() {
  const element = (
    <div>
      <h1>Hello, world!</h1>
      <h2>It is {new Date().toLocaleTimeString()}.</h2>
    </div>
  );
  root.render(element);
}

setInterval(tick, 1000);
```

It calls `root.render() `every second from a `setInterval()` callback.

### React Only Updates What’s Necessary

React DOM compares the element and its children to the previous one, and only applies the DOM updates necessary to bring the DOM to the desired state.

You can verify by inspecting the last example with the browser tools:


# References

### [React hello world](https://reactjs.org/docs/hello-world.html)

### [Intoduction to JSX](https://reactjs.org/docs/introducing-jsx.html)

### [Rendering Elements](https://reactjs.org/docs/rendering-elements.html)

### [SASS Cheatsheet](https://devhints.io/sass)

### [React Cheatsheet](https://devhints.io/react)

### [Another React Cheatsheet](https://reactcheatsheet.com/)

## [Back To Home Page](../../README.md)