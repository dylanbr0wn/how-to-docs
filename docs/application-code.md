# React App Code and Structure

## [React](https://reactjs.org)

React is a JavaScript library for building user interfaces and is what is used in the Timesheet and Burn Permit systems. React uses a virtual DOM to control changes to the user interface. The actual templating of the interface is written using JSX, an extension of JavaScipt that includes XML/HTML support.

### Components

React components are custom entities that can be used like any other XML/HTML element. Components allow you to encapsulate like elements and logic. Components can then be reused as needed.

There are numerous ways to define React components, such as through class definitions, or functional components using the function or arrow function syntax. The method most commonly used in the Timesheet and Burn Permit applications is the arrow function method of defining components.

All components have 3 key elements; props, hooks, and JSX.

```jsx
const App => ({ /* props */}) => {
    //hooks logic
    return (
        //JSX
    )
}
export default App
```

### Props

The props of a component are parameters passed down to it from a parent component. These props can then be accessed in the child component, but cannot be directly modified in the child. If a the props of a component changes, the component will re-render itself.

### Hooks

Hooks are functions that enable you to use state and lifecycle functions within functional components. We will lighlty touch on a few different hooks in this doc but I recommend the [React docs](https://reactjs.org/docs/hooks-overview.html) on hooks if you run into issues or you are looking for a hook not listed here.

#### useState

The useState hook is arguably the most common hook. It allows you to create and modify the state of a component. The useState hook returns an array of 2 items, the first is the value of the state, the second is a setter for that piece of state.

The useState hook takes 1 argument, the initial value of the state.

```jsx
const [user, setUser] = useState({ id: null });
const [page, setPage] = useState(0);
```

State can only be altered through the setter functions for each piece of state.

```jsx
setUser({ id: 1 });
```

#### useEffect

The useEffect hook is a lifecycle hook. useEffect is called in the component and will run everytime one of its dependencies changes.

```jsx
useEffect(
  () => {
    //Logic to fire whenever a dependency changes
  },
  [
    /* dependencies */
  ]
);
```

Leaving the dependency array empty will lead to that useEffect hook being called only once upon first render/prop change.

Good practice is to include every dynamic value in the dependency array, this includes state, and functions. If they are not included here, useEffect will not fire when it changes, and its value will remain what it was upon first execution.

Multiple useEffect calls can be made for handling different logic with different lifecycles

#### useMemo

useMemo is a hook used for memoization of values. This can be helpful when you have calculated values that dont need to be re-calculated upon every use, but only when the dependencies change.

```jsx
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```

#### useCallback

useCallback is useMemo but for functions. Without memoization, a function will need to be reevaluated upon every execution. With useCallback you can once again specify a dependency array so that the function is only re-evaluated if those dependencies change.

```jsx
const nextPage = useCallback(
    //Function to memoize
    ,
    [ /* Dependencies */]
);
```

## App Structure

In the root of the repository, we have a `src` and a `public` folder. In `public` we can keep static files such as assets, or the entry HTML file.

In `src` we store all our code that we need to compile through webpack. This includes JSX, CSS, etc. The `src` directory has the following structure:

<p align="center">
<img src="/img/react_direc.png" width="250" alt="React App Directory" />
</p>

### Components

As the name suggests, this is where all the components of the application reside. This can be organised as desired to fit the layout of the application.

### API

The `api` directory holds all code associated with communication with the API. This includes [Axios](https://axios-http.com) configuration, and organised route call functions.

The general format of an API file is as follows:

```js
import API from "./api.js"

const getAddressAutoFill = async () => {
    try{
        const result = API().get(/* api route address */,
        {/* request configuration */}
        )
    }catch(error){
        //handle error
    }
}
```

### Redux

The `redux` directory evidently holds all logic associated with the [Redux](https://redux.js.org) store, actions, and reducers.

Please see the section on Redux for further information on this topic.

### Utils/Services

The utils/services directory holds all code that doesn't fall into one of the aformentioned categories. This includes helper functions/code, pieces of logic that are reused, or static objects.
