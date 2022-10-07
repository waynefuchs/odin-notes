- [React](#react)
  - [Common Packages](#common-packages)
    - [react-router-dom](#react-router-dom)
    - [uniqid](#uniqid)
  - [Life Cycle](#life-cycle)
    - [Common Use Methods](#common-use-methods)
      - [Mount](#mount)
      - [Update](#update)
      - [Unmount](#unmount)

# React

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
