# React

**Create a TypeScript app**

```
$ npx create-react-app my-app --template typescript
```
## Commands

**Start the app**

```
$ yarn **start**
```

**Run tests**

```
$ yarn test
```

**Build**

```
$ yarn buid
```
## Data types

```
// String
const topic = "React";

// int
const age = 12;

// boolean (would need to cast to String to view)
const isTrue = true;
String(true) // to view in the web page
```

## Conditional

**Ternary**

Use terneary instead of if-else.

```
{
  age > 4 ? <h3>Is True</h3> : <h3>Is False</h3>
}
```

To loop, use the map method.

```
  const likes = ["JSX", "React", "Redux"];`

  // Elements created by the map should have a key defined.
  // This is to allow React to know which elements to change when something changes.
  return (
    <div>
      {likes.map(like => (
        <h3 key={like}>{like}</h3>
      ))}
    </div>
  ); 
```
## Hooks

Standard hooks:

* useState
* useEffect
* useContext
* useRef
* useMemo
* useCallback
* useReducer
* useLayoutEffect 

### useState

[useState](https://react.dev/reference/react/useState) declares and tracks state value within a component. When the state is changed, React re-renders the JSX to reflect the new value.

Returns an array with two values:

* the current state (initialized with the optional inital value)
* a `set` function that lets you update the state and trigger a re-render of the JSX

```
import { useState } from 'react';

function MyComponent() {
  // useState() is initialized to 42. "age" is the state and "setAge"
  // is the update function (named "set" by convention)
  const [age, setAge] = useState(42);

  function handleClick() {
    setAge(23);
  }
```

Can pass in an updater function to update the state variable in running code.

```
function handleClick() {
  // using an updater function
  setAge(a => a + 1); // setAge(42 => 43)
  setAge(a => a + 1); // setAge(43 => 44)
  setAge(a => a + 1); // setAge(44 => 45)

  setAge(a + 1); // doesn't update "age" the way you expect because the code is running. needs an updater function
}
```

#### Initial state

Accepts an optional initial value, which can be any valid javascript value or a function.

```
// 🚩 calls "createInitialTodos()" for every render, but it only
// needs the inital render 
function TodoList() {
  const [todos, setTodos] = useState(createInitialTodos());
  // ...

// ✅ instead, pass a function "createInitialTodos" 
function TodoList() {
  const [todos, setTodos] = useState(createInitialTodos);
  // ...  
```


#### Objects and arrays in state
Can put objects in state, but replace rather than mutate the existing objects

```
// 🚩 Don't mutate an object in state like this:
form.firstName = 'Taylor';

// ✅ Replace state with a new object
setForm({
  ...form,
  firstName: 'Taylor'
});
```

## JSX

* combination of Javascript and HTML
* Javascript eXtended syntax
* components combine presentation and computation, so components have both html and Javascript (or Typescript) together
* JSX gets transpiled to plain Javascript and HTML
* return from the react component
  ```
  function App() {
    return <div>This is thejsx</div>;
  }
  ```

## Components

* plain Javascript function
* the function must return something
* the something it must return is JSX
* the component may have data private to itself, which is called `state`
* the component may have data to share with other components. this is called `props`
## Hosting on Vercel

https://vercel.com/

### Using exteranl URL

```
function App() {
  const backgroundImageUrl = "https://example.com/images/category1.jpg";

  const divStyle = {
    backgroundImage: `url(${backgroundImageUrl})`,
  };

  return (
    <div style={divStyle}>
      Hello World
    </div>
  );
}
```

### Using local image

```
import React from "react";
import background from "./images/category1.jpg";

function App() {
  const divStyle = {
    backgroundImage: `url(${background})`,
  };

  return (
    <div style={divStyle}>
      Hello World
    </div>
  );
}

export default App;
```

### Using require

Using Webpack with a local image:

```
<div
  className="full-background"
  style={{
    backgroundImage: `url(${require('./images/category1.jpg')})`,
    backgroundSize: "cover"
  }}
>
Hello World
</div>
```

### Using public image

Images in the `public` directory.

```
<div style={{ backgroundImage: "url(/images/category1.jpg)" }}>
  Hello World
</div>
```