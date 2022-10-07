- [React](#react)
  - [Hooks](#hooks)
    - [useEffect](#useeffect)
    - [useState](#usestate)
    - [useContext / useReducer](#usecontext--usereducer)
    - [Custom Hooks](#custom-hooks)
  - [Common Packages](#common-packages)
    - [react-router-dom](#react-router-dom)
    - [uniqid](#uniqid)
  - [Life Cycle](#life-cycle)
    - [Common Use Methods](#common-use-methods)
      - [Mount](#mount)
      - [Update](#update)
      - [Unmount](#unmount)

# React

## Hooks

[Official Hook Introduction Documentation](https://reactjs.org/docs/hooks-intro.html)

* Hooks are only available from React function components, and not in extensions of React classes.

* Call hooks only from the top level. (Not inside conditionals, loops, or nested functions.)

* Introduced in React 16.8


### useEffect

Combine `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount`.

``` js
useEffect(() => {
    // componentDidMount
    // componentDidUpdate
    console.log("Component mounted or updated");
    return () => {
        // componentWillUnmount
        console.log("Component is unmounting")
    }
})
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
        <Route path="/profile" element={<Profile />} />
      </Routes>
    </BrowserRouter>
  );
};

export default RouteSwitch;
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
