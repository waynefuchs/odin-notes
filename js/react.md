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