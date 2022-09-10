# Redux Toolkit

The **Redux Toolkit** package is intended to be the standard way to write Redux logic. It was originally created to help address three common concerns about Redux:

- "Configuring a Redux store is too complicated"
- "I have to add a lot of packages to get Redux to do anything useful"
- "Redux requires too much boilerplate code"

## Installation

```js
# Redux + Plain JS template
npx create-react-app my-app --template redux

# Redux + TypeScript template
npx create-react-app my-app --template redux-typescript
```

### An Existing App

```js
npm install @reduxjs/toolkit
```

### Redux Toolkit includes these APIs:

- `configureStore()`: wraps `createStore` to provide simplified configuration options and good defaults. It can automatically combine your slice reducers, adds whatever Redux middleware you supply, includes `redux-thunk` by default, and enables use of the Redux DevTools Extension.
- `createReducer()`: that lets you supply a lookup table of action types to case reducer functions, rather than writing switch statements. In addition, it automatically uses the immer library to let you write simpler immutable updates with normal mutative code, like `state.todos[3].completed = true`.
- `createAction()`: generates an action creator function for the given action type string. The function itself has `toString()` defined, so that it can be used in place of the type constant.
- `createSlice()`: accepts an object of reducer functions, a slice name, and an initial state value, and automatically generates a slice reducer with corresponding action creators and action types.
- `createAsyncThunk`: accepts an action type string and a function that returns a promise, and generates a thunk that dispatches `pending/fulfilled/rejected` action types based on that promise
- `createEntityAdapter`: generates a set of reusable reducers and selectors to manage normalized data in the store
The createSelector utility from the Reselect library, re-exported for ease of use.

## RTK Query

**RTK Query** is provided as an optional addon within the @reduxjs/toolkit package. It is purpose-built to solve the use case of data fetching and caching, supplying a compact, but powerful toolset to define an API interface layer for your app. It is intended to simplify common cases for loading data in a web application, eliminating the need to hand-write data fetching & caching logic yourself.

RTK Query is included within the installation of the core Redux Toolkit package. It is available via either of the two entry points below:

```js
import { createApi } from '@reduxjs/toolkit/query'

/*React-specific entry point that automatically generates
hooks corresponding to the defined endpoints*/
import { createApi } from '@reduxjs/toolkit/query/react'
```


### RTK Query includes these APIs:

- `createApi()`: The core of RTK Query's functionality. It allows you to define a set of endpoints describe how to retrieve data from a series of endpoints, including configuration of how to fetch and transform that data. In most cases, you should use this once per app, with "one API slice per base URL" as a rule of thumb.
- `fetchBaseQuery()`: A small wrapper around fetch that aims to simplify requests. Intended as the recommended baseQuery to be used in createApi for the majority of users.
- `<ApiProvider />`: Can be used as a Provider if you **do not already have a Redux store**.
- `setupListeners()`: A utility used to enable refetchOnMount and refetchOnReconnect behaviors.

# MobX


**MobX** is a simple, scalable and battle tested state management solution, also it's standalone library, but most people are using it with React.

MobX makes state management simple again by addressing the root issue: it makes it impossible to produce an inconsistent state. The strategy to achieve that is simple: Make sure that everything that can be derived from the application state, will be derived. Automatically.

Conceptually MobX treats your application like a spreadsheet.

![](https://mobx.js.org/assets/getting-started-assets/overview.png)

# HookState

### Installation and dependencies

```js
npm install --save @hookstate/core
```
### Creating and using global state

```js
import React from 'react';
import { hookstate, useHookstate } from '@hookstate/core';

const globalState = hookstate(0);

setInterval(() => globalState.set(p => p + 1), 3000)

export const ExampleComponent = () => {
    const state = useHookstate(globalState);
    return <>
        <b>Counter value: {state.get()}</b> (watch +1 every 3 seconds) {' '}
        <button onClick={() => state.set(p => p + 1)}>Increment</button>
    </>
}
```


# References

## [Redux Toolkit (RTK)](https://redux-toolkit.js.org/)

## [MobX](https://mobx.js.org/getting-started.html)

## [HookState](https://hookstate.js.org/)

## [Tutorial](https://redux-toolkit.js.org/tutorials/overview)

## [Back To Home Page](../../README.md)


