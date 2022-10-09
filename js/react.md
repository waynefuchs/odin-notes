- [React](#react)
  - [Hooks](#hooks)
    - [useEffect](#useeffect)
    - [useState](#usestate)
    - [useContext / useReducer](#usecontext--usereducer)
    - [Custom Hooks](#custom-hooks)
  - [Common Packages](#common-packages)
    - [react-router-dom](#react-router-dom)
      - [<Outlet context={...} />](#outlet-context-)
      - [navigate(location)](#navigatelocation)
      - [const obj = useParams()](#const-obj--useparams)
      - [useSearchParams({...})](#usesearchparams)
      - [useNavigate()](#usenavigate)
    - [uniqid](#uniqid)
  - [Life Cycle](#life-cycle)
    - [Common Use Methods](#common-use-methods)
      - [Mount](#mount)
      - [Update](#update)
      - [Unmount](#unmount)
  - [Testing (Jest)](#testing-jest)

# React

WebDevSimplified's [Learn React Router v6 in 45 Minutes](https://www.youtube.com/watch?v=Ul3y1LXxzdU)

## Hooks

[Official Hook Introduction Documentation](https://reactjs.org/docs/hooks-intro.html)

- Hooks are only available from React function components, and not in extensions of React classes.

- Call hooks only from the top level. (Not inside conditionals, loops, or nested functions.)

- Introduced in React 16.8

### useEffect

Combine `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount`.

```js
useEffect(() => {
  // componentDidMount
  // componentDidUpdate
  console.log("Component mounted or updated");
  return () => {
    // componentWillUnmount
    console.log("Component is unmounting");
  };
});
```

### useState

`[value, setValue] = useState(initialValue);`

### useContext / useReducer

"Less common" hooks that I haven't looked into.

### Custom Hooks

Naming Convention: The keyword `use`, such as `useSomething()` where `useSomething()` calls other hooks causes it to be a custom hook, and the React linter uses that to find hook related bugs.

## Common Packages

| Package                  | What the package does    |
| ------------------------ | ------------------------ |
| `npm i react-router-dom` | React Client-side Router |
| `npm i uniqid`           | Unique id's for lists    |

### react-router-dom

Official react-router-dom [documentation](https://reactrouter.com/en/v6.3.0/getting-started/overview)

```js
// react-router-dom Example
import { BrowserRouter, Routes, Route } from "react-router-dom";
import App from "./App";
import Profile from "./Profile";

const RouteSwitch = () => {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<App />} />
        <Route path="/profile" element={<Profile />}>
          <Route index element={<ProfileHome />} />
          <Route path=":id" element={<ShowProfile />} />
          <Route path="*" element={<FourOhFour />} />
        </Route>
      </Routes>
    </BrowserRouter>
  );
};

export default RouteSwitch;
```

#### <Outlet context={...} />

A way to route nested content from sub-routes.

#### navigate(location)

A way to force navigation.

```js
navigate("/"); // navigate to page root
navigate(-1); // simulate hitting the back button (1 time)
navigate(-2); // simulate hitting the back button (2 times)
navigate(1); // simulate hitting the forward button (1 time)
```

#### const obj = useParams()

Get parameters passed in from react router ":value" fields.


#### useSearchParams({...})

The ability to alter query string data so if someone copies and pastes a link to a friend, the url that is reached will be the same as the one copied. (Store some state in the query string)

#### useNavigate()

```js
import { useNavigate } from "react-router-dom";

const NotFound = () => {
  useEffect(() => {
    setTimeout(() => {
      navigate("/"); // go to home page
    }, 1000);
  }, []);
  return <h1>Not Found</h1>;
};
```

### uniqid

```js
// Uniqid example
import uniqid from "uniqid";
const id = uniqid();
```

## Life Cycle

Mount => Update => Unmount

[React Lifecycle Diagram](https://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/)

### Common Use Methods

#### Mount

constructor()
render()
componentDidMount()

#### Update

render()
componentDidUpdate(prevProps, prevState, snapshot)

#### Unmount

componentWillUnmount()



## Testing (Jest)

`create-react-app` sets up and installs all of the necessary packages and takes care of the `package.json` configuration for testing.

Documentation on test functions available for performing tests:
* [DOM Testing Library Cheat Sheet](https://testing-library.com/docs/dom-testing-library/cheatsheet/)
* [ByTestId Documentation](https://testing-library.com/docs/queries/bytestid/) for when the standard DOM Testing Library doesn't quite cut it.

Documentation on jest-dom, an optional extension to the built-in matchers
* [jest-dom Github](https://github.com/testing-library/jest-dom)

Documentation on how to simulate user input:
* [User Interactions](https://testing-library.com/docs/user-event/intro/)

Remember that snapshots exist.

```js
// Need to place in <Filename>.test.js
import React from "react";

// Get access to useful functions like `render`
import { ... } from "@testing-library/react";

// includes some handy custom matchers (assertive functions) like `toBeInTheDocument` and more. 
// Jest already has a lot of matchers so this package is not compulsory to use.
// See jest-dom github for docs
import "@testing-library/jest-dom";  // optional

// Provides the `userEvent` API that simulates user interactions with the webpage.
// Alternatively, we could import the `fireEvent` API from @testing-library/react.
// Note: `fireEvent` is an inferior counterpart to `userEvent`
//       and userEvent should always be preferred in practice.
import userEvent from "@testing-library/user-event";

// No need to import jest since it will automatically detect test files (*.test.js or *.test.jsx).
import <TestComponent> from "<path-to-test-component>";
```

A Copy-Paste Example From Above:

``` js
import React from 'react';
import { render, screen } from '@testing-library/react';
import App from './App';
```
	
