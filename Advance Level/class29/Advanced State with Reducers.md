# Advanced State with Reducers

## Hooks API Reference

- Basic Hooks

    - `useState`
    - `useEffect`
    - `useContext`

- Additional Hooks

    - `useReducer`
    - `useCallback`
    - `useMemo`
    - `useRef`
    - `useImperativeHandle`
    - `useLayoutEffect`
    - `useDebugValue`
    - `useDeferredValue`
    - `useTransition`
    - `useId`

- Library Hooks

    - `useSyncExternalStore`
    - `useInsertionEffect`

# Basic Hooks

## useState
```js
const [state, setState] = useState(initialState);
```

Returns a stateful value, and a function to update it.

During the initial render, the returned state (state) is the same as the value passed as the first argument (initialState).

The `setState` function is used to update the state. It accepts a new state value and enqueues a re-render of the component.

```js
setState(newState);
```
During subsequent re-renders, the first value returned by useState will always be the most recent state after applying updates.

Functional updates

If the new state is computed using the previous state, you can pass a function to setState. The function will receive the previous value, and return an updated value. 

**Lazy initial state**

The `initialState` argument is the state used during the initial render. In subsequent renders, it is disregarded. If the initial state is the result of an expensive computation, you may provide a function instead, which will be executed only on the initial render:

```js
const [state, setState] = useState(() => {
  const initialState = someExpensiveComputation(props);
  return initialState;
});
```
**Bailing out of a state update**

If you update a State Hook to the same value as the current state, React will bail out without rendering the children or firing effects.

**Batching of state updates**

React may group several state updates into a single re-render to improve performance. Normally, this improves performance and shouldn’t affect your application’s behavior.

## useEffect

```js
useEffect(didUpdate);
```

Accepts a function that contains imperative, possibly effectful code.

Mutations, subscriptions, timers, logging, and other side effects are not allowed inside the main body of a function component (referred to as React’s render phase). Doing so will lead to confusing bugs and inconsistencies in the UI.

Instead, use useEffect. The function passed to useEffect will run after the render is committed to the screen. Think of effects as an escape hatch from React’s purely functional world into the imperative world.


**Cleaning up an effect**

Often, effects create resources that need to be cleaned up before the component leaves the screen, such as a subscription or timer ID. To do this, the function passed to useEffect may return a clean-up function. For example, to create a subscription:

```js
useEffect(() => {
  const subscription = props.source.subscribe();
  return () => {
    // Clean up the subscription
    subscription.unsubscribe();
  };
});
```

The clean-up function runs before the component is removed from the UI to prevent memory leaks. Additionally, if a component renders multiple times (as they typically do), the previous effect is cleaned up before executing the next effect. In our example, this means a new subscription is created on every update. To avoid firing an effect on every update, refer to the next section.

**Conditionally firing an effect**

The default behavior for effects is to fire the effect after every completed render. That way an effect is always recreated if one of its dependencies changes.

However, this may be overkill in some cases, like the subscription example from the previous section. We don’t need to create a new subscription on every update, only if the source prop has changed.

To implement this, pass a second argument to useEffect that is the array of values that the effect depends on. Our updated example now looks like this:

```js
useEffect(
  () => {
    const subscription = props.source.subscribe();
    return () => {
      subscription.unsubscribe();
    };
  },
  [props.source],
);
```

## useContext

```js
const value = useContext(MyContext);
```

Accepts a context object (the value returned from `React.createContex`t) and returns the current context value for that context. The current context value is determined by the value prop of the nearest `<MyContext.Provider>` above the calling component in the tree.

When the nearest `<MyContext.Provider>` above the component updates, this Hook will trigger a rerender with the latest context value passed to that MyContext provider. Even if an ancestor uses React.memo or shouldComponentUpdate, a rerender will still happen starting at the component itself using useContext.

Don’t forget that the argument to useContext must be the context object itself:

```js
const themes = {
  light: {
    foreground: "#000000",
    background: "#eeeeee"
  },
  dark: {
    foreground: "#ffffff",
    background: "#222222"
  }
};

const ThemeContext = React.createContext(themes.light);

function App() {
  return (
    <ThemeContext.Provider value={themes.dark}>
      <Toolbar />
    </ThemeContext.Provider>
  );
}

function Toolbar(props) {
  return (
    <div>
      <ThemedButton />
    </div>
  );
}

function ThemedButton() {
  const theme = useContext(ThemeContext);
  return (
    <button style={{ background: theme.background, color: theme.foreground }}>
      I am styled by theme context!
    </button>
  );
}
```

# Additional Hooks

## useReducer

```js 
const [state, dispatch] = useReducer(reducer, initialArg, init);
```
An alternative to useState. Accepts a reducer of type (state, action) => newState, and returns the current state paired with a dispatch method.


**Specifying the initial state**

There are two different ways to initialize useReducer state. You may choose either one depending on the use case. The simplest way is to pass the initial state as a second argument:

```js
  const [state, dispatch] = useReducer(
    reducer,
    {count: initialCount}
  );
  ```

**Lazy initialization**

You can also create the initial state lazily. To do this, you can pass an init function as the third argument. The initial state will be set to init(initialArg).

**Bailing out of a dispatch**

If you return the same value from a Reducer Hook as the current state, React will bail out without rendering the children or firing effects.

## useCallback

```js
const memoizedCallback = useCallback(
  () => {
    doSomething(a, b);
  },
  [a, b],
);
```

Returns a memoized callback.

Pass an inline callback and an array of dependencies. `useCallback` will return a memoized version of the callback that only changes if one of the dependencies has changed. This is useful when passing callbacks to optimized child components that rely on reference equality to prevent unnecessary renders.

`useCallback(fn, deps)` is equivalent to `useMemo(() => fn, deps)`.

## useMemo


```js
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```

Returns a memoized value.

Pass a “create” function and an array of dependencies. `useMemo` will only recompute the memoized value when one of the dependencies has changed. This optimization helps to avoid expensive calculations on every render.

Remember that the function passed to `useMemo` runs during rendering. Don’t do anything there that you wouldn’t normally do while rendering. For example, side effects belong in `useEffect`, not `useMemo`.

If no array is provided, a new value will be computed on every render.

## useRef

```js
const refContainer = useRef(initialValue);
```
`useRef` returns a mutable ref object whose .current property is initialized to the passed argument (initialValue). The returned object will persist for the full lifetime of the component.

A common use case is to access a child imperatively:

```js
function TextInputWithFocusButton() {
  const inputEl = useRef(null);
  const onButtonClick = () => {
    // `current` points to the mounted text input element
    inputEl.current.focus();
  };
  return (
    <>
      <input ref={inputEl} type="text" />
      <button onClick={onButtonClick}>Focus the input</button>
    </>
  );
}
```
Essentially, **useRef** is like a “box” that can hold a mutable value in its `.current` property.

You might be familiar with refs primarily as a way to access the DOM. If you pass a ref object to React with `<div ref={myRef} />`, React will set its `.current` property to the corresponding DOM node whenever that node changes.

However, `useRef()` is useful for more than the ref attribute. It’s handy for keeping any mutable value around similar to how you’d use instance fields in classes.

This works because `useRef()` creates a plain JavaScript object. The only difference between `useRef()` and creating a `{current: ...}` object yourself is that useRef will give you the same ref object on every render.

Keep in mind that `useRef` doesn’t notify you when its content changes. Mutating the `.current` property doesn’t cause a re-render. If you want to run some code when React attaches or detaches a ref to a DOM node, you may want to use a callback ref instead.

## useImperativeHandle

```js
useImperativeHandle(ref, createHandle, [deps])
```
`useImperativeHandle` customizes the instance value that is exposed to parent components when using ref. As always, imperative code using refs should be avoided in most cases. `useImperativeHandle` should be used with forwardRef:

```js
function FancyInput(props, ref) {
  const inputRef = useRef();
  useImperativeHandle(ref, () => ({
    focus: () => {
      inputRef.current.focus();
    }
  }));
  return <input ref={inputRef} ... />;
}
```
FancyInput = forwardRef(FancyInput);
In this example, a parent component that renders `<FancyInput ref={inputRef} />` would be able to call `inputRef.current.focus()`.

## useLayoutEffect

The signature is identical to `useEffect`, but it fires synchronously after all DOM mutations. Use this to read layout from the DOM and synchronously re-render. Updates scheduled inside `useLayoutEffect` will be flushed synchronously, before the browser has a chance to paint.

Prefer the standard `useEffect` when possible to avoid blocking visual updates.

## useDebugValue

```js
useDebugValue(value)
```

`useDebugValue `can be used to display a label for custom hooks in React DevTools.

For example, consider the `useFriendStatus` custom Hook described in “Building Your Own Hooks”:

```js
function useFriendStatus(friendID) {
  const [isOnline, setIsOnline] = useState(null);

  // ...

  // Show a label in DevTools next to this Hook
  // e.g. "FriendStatus: Online"
  useDebugValue(isOnline ? 'Online' : 'Offline');

  return isOnline;
}
```

## useDeferredValue

```js
const deferredValue = useDeferredValue(value);
```

`useDeferredValue` accepts a value and returns a new copy of the value that will defer to more urgent updates. If the current render is the result of an urgent update, like user input, React will return the previous value and then render the new value after the urgent render has completed.

This hook is similar to user-space hooks which use debouncing or throttling to defer updates. The benefits to using `useDeferredValue` is that React will work on the update as soon as other work finishes (instead of waiting for an arbitrary amount of time), and like startTransition, deferred values can suspend without triggering an unexpected fallback for existing content.

## useTransition

```js
const [isPending, startTransition] = useTransition();
```

Returns a stateful value for the pending state of the transition, and a function to start it.

`startTransition` lets you mark updates in the provided callback as transitions:

```js
startTransition(() => {
  setCount(count + 1);
})
```

`isPending` indicates when a transition is active to show a pending state:

```js
function App() {
  const [isPending, startTransition] = useTransition();
  const [count, setCount] = useState(0);
  
  function handleClick() {
    startTransition(() => {
      setCount(c => c + 1);
    })
  }

  return (
    <div>
      {isPending && <Spinner />}
      <button onClick={handleClick}>{count}</button>
    </div>
  );
}
```

## useId


```js
const id = useId();
```

`useId` is a hook for generating unique IDs that are stable across the server and client, while avoiding hydration mismatches.

For a basic example, pass the id directly to the elements that need it:

```js
function Checkbox() {
  const id = useId();
  return (
    <>
      <label htmlFor={id}>Do you like React?</label>
      <input id={id} type="checkbox" name="react"/>
    </>
  );
};
```

# Library Hooks

## useSyncExternalStore

```js
const state = useSyncExternalStore(subscribe, getSnapshot[, getServerSnapshot]);
```

`useSyncExternalStore` is a hook recommended for reading and subscribing from external data sources in a way that’s compatible with concurrent rendering features like selective hydration and time slicing.

This method returns the value of the store and accepts three arguments:

`subscribe`: function to register a callback that is called whenever the store changes.
`getSnapshot`: function that returns the current value of the store.
`getServerSnapshot`: function that returns the snapshot used during server rendering.
The most basic example simply subscribes to the entire store:

```js
const state = useSyncExternalStore(store.subscribe, store.getSnapshot);
```
However, you can also subscribe to a specific field:

```js
const selectedField = useSyncExternalStore(
  store.subscribe,
  () => store.getSnapshot().selectedField,
);
```
When server rendering, you must serialize the store value used on the server, and provide it to useSyncExternalStore. React will use this snapshot during hydration to prevent server mismatches:

```js
const selectedField = useSyncExternalStore(
  store.subscribe,
  () => store.getSnapshot().selectedField,
  () => INITIAL_SERVER_SNAPSHOT.selectedField,
);
```

## useInsertionEffect

```js
useInsertionEffect(didUpdate);
```

The signature is identical to `useEffect`, but it fires synchronously before all DOM mutations. Use this to inject styles into the DOM before reading layout in `useLayoutEffect`. Since this hook is limited in scope, this hook does not have access to refs and cannot schedule updates.



# useReducer

The `useReducer()` hook in React allows you to decouple the component's state management from its rendering logic.

```js
const [state, dispatch] = useReducer(reducer, initialState)
```

Accepts 2 argument:

1. The reducer function
2. The initial state.

## When to use useReducer?

`useReducer` is typically recommended over useState when you have sophisticated state logic involving several sub-values or when the future state is reliant on the prior one. `UseReducer` can help you increase speed for components that trigger deep updates by allowing you to pass dispatch down instead of callbacks.

How does it work? How does the Reducer Hook work?
Reducer Hook is used to save and update states, much like useState Hook. The reducer function is the first parameter, and the initial state is the second.

`useReducer` returns an array holding the current state value as well as a dispatch function to which you may submit a later-running action. There are a few differences between this design and Redux's.

## CODE EXAMPLE:

```js
import React, { useReducer } from "react";

const initialState = { count: 0 };
// The reducer function
function reducer(state, action) {
  switch (action.type) {
    case "increment":
      return { count: state.count + 1 };
    case "decrement":
      return { count: state.count - 1 };
    case "reset":
      return { count: (state.count = 0) };
    default:
      return { count: state.count };
  }
}

export default function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);
  return (
    <>
      Count: {state.count}
      <button onClick={() => dispatch({ type: "reset" })}>Reset</button>
      <button onClick={() => dispatch({ type: "decrement" })}>-</button>
      <button onClick={() => dispatch({ type: "increment" })}>+</button>
    </>
  );
}
```

# References

## [useReducer hook](https://reactjs.org/docs/hooks-reference.html#usereducer)

## [Ultimate Guide to useReducer](https://blog.logrocket.com/react-usereducer-hook-ultimate-guide/)

## [Back To Home Page](../../README.md)
