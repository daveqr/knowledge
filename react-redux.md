# React Redux

## Main Concepts

1. **Store**: The store is the central place that holds the entire application state. It is created using Redux and serves as a single source of truth for your application's data.

2. **Reducer**: A reducer is a pure function that takes the current state and an action as arguments and returns a new state based on the action. Reducers are responsible for specifying how the state changes in response to actions. You can have multiple reducers, each managing a specific part (or slice) of the overall state.

3. **Slice**: A slice is a concept introduced by Redux Toolkit, which is a library built on top of Redux. Slices are a way to group together related reducer logic, initial state, and action creators under a single key in the Redux store.

4. **Action**:

### Store

The store is a container that holds the global state of your application, and it's typically used to manage different parts of your application's state.

You can structure your store to hold different slices of state, such as user data, cart data, authentication state, etc. Each slice of state is managed by its corresponding reducer, and all of them are combined into a single store using the configureStore function from Redux Toolkit.

### Reducers

In Redux, reducers are functions that specify how the state of your application changes in response to dispatched actions. Each reducer is responsible for managing a specific "slice" of the overall application state. These slices are organized within the store using keys.

### Slices

A slice is a self-contained piece of Redux store configuration that includes the following:

* **reducer**: a function that describes how an application's state changes in response to actions
* **actions**: payloads of information that send data from your application to your Redux store
* **intial state**: the initial values of the state properties managed by that slice

When you create a "slice" using Redux Toolkit's createSlice function, it automatically generates the reducer function, action creators, and the initial state for that slice.

```
import { createSlice } from '@reduxjs/toolkit';
	
const cartSlice = createSlice({
  name: 'cart', // The name of the slice
  initialState: [], // Initial state for the cart slice
  reducers: {
    addToCart: (state, action) => {
      // Logic to add an item to the cart
    },
    removeFromCart: (state, action) => {
      // Logic to remove an item from the cart
    },
    clearCart: (state) => {
      // Logic to clear the cart
    },
  },
});
```

export const { addToCart, removeFromCart, clearCart } = cartSlice.actions;
export default cartSlice.reducer;

In this example, cartSlice is a slice of your Redux store called 'cart,' and it includes reducers for adding to the cart, removing from the cart, and clearing the cart. The slice automatically generates action creators for these actions.

### Actions

In Redux, actions are plain JavaScript objects that represent events or instructions that describe how the state of an application should change. Actions are the only source of information for the Redux store. They typically have two properties:

1. **type**: A string that describes the type of action being performed. It's a unique identifier for the action and is used by reducers to determine how to update the state.

2. **payload**: Any data or information that is needed to update the state. The payload can contain any data type, such as strings, numbers, objects, or arrays. It provides the necessary information for reducers to make changes to the state.

```
const addItemToCart = (item) => {
  return {
    type: 'ADD_ITEM_TO_CART',
    payload: item,
  };
};
```
	
In this example, addItemToCart is an action creator, which is a function that creates and returns an action object. When dispatched, this action object will be sent to the Redux store, and the store's reducers will use the type and payload properties to determine how to update the state.

Reducers are responsible for handling these actions and specifying how the application's state should change in response to them. Here's an example of a reducer that handles the `ADD_ITEM_TO_CART` action:

```
const cartReducer = (state = initialState, action) => {
  switch (action.type) {
    case 'ADD_ITEM_TO_CART':
      return {
        ...state,
        cartItems: [...state.cartItems, action.payload],
      };
    // ... other cases for different actions
    default:
      return state;
  }
};
```

In this reducer, when the 'ADD_ITEM_TO_CART' action is dispatched, it adds the item from the action's payload to the cartItems array in the state, resulting in a new state object.

Actions provide a structured and predictable way to communicate changes to the Redux store's state, making it easier to manage and reason about application state changes, especially in complex applications.

## Redux Toolkit

Redux Toolkit is designed to simplify and streamline the Redux setup process. It provides:

* simpler config
* better defaults
* improved performance
* reduced boilerplate
* type safety