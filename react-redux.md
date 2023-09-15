# React Redux

## Main Concepts

1. **Store**: The store is the central repository for the application's state. It holds the entire state tree of your application. In a React Redux application, you create a single store that manages all the state for your app.

1. **Reducers**: Pure functions that specify how the application's state changes in response to actions. They take the current state and an action as arguments and return a new state. Reducers should be pure and deterministic, meaning they should not have side effects or modify the state directly.

1. **Actions**: Plain JavaScript objects that represent events or intentions to change the state. They have a `type` property that describes the action and an optional `payload` property that carries data associated with the action. Actions are typically dispatched to the store to trigger state changes.
 

### Store

The store is a container that holds the global state of your application, and it's typically used to manage different parts of your application's state.

You can structure your store to hold different slices of state, such as user data, cart data, authentication state, etc. Each slice of state is managed by its corresponding reducer, and all of them are combined into a single store using the configureStore function from Redux Toolkit.

```
import { configureStore } from '@reduxjs/toolkit';
import persistedReducer from './reducers/reducers';
import { persistStore } from 'redux-persist';

const store = configureStore({
  reducer: persistedReducer,
});

const persistor = persistStore(store);

export { store, persistor }; 
```

### Reducers

In Redux, reducers are functions that specify how the state of your application changes in response to dispatched actions. Each reducer is responsible for managing a specific "slice" of the overall application state. These slices are organized within the store using keys.

#### Slices

A slice is a self-contained piece of Redux store configuration that includes the following:

* **reducer**: a function that describes how an application's state changes in response to actions
* **actions**: payloads of information that send data from your application to your Redux store
* **intial state**: the initial values of the state properties managed by that slice

When you create a "slice" using Redux Toolkit's createSlice function, it automatically generates the reducer function, action creators, and the initial state for that slice.

```
import { createSlice } from '@reduxjs/toolkit';
import { CartItem } from '../../models/CartItem';
import { createAction } from '@reduxjs/toolkit';

// Actions
export const addToCart = createAction<CartItem>('ADD_TO_CART');
export const removeFromCart = createAction<string>('REMOVE_FROM_CART');
export const clearCart = createAction('CLEAR_CART');

// Slice
export const cartSlice = createSlice({
    name: 'cart',
    initialState: { cartItems: [] as ReadonlyArray<CartItem> },
    reducers: {},
    extraReducers: (builder) => {
        builder
            .addCase(addToCart, (state, action) => {
                const cartItem = action.payload as CartItem;
                state.cartItems = [...state.cartItems, cartItem];
            })
            .addCase(removeFromCart, (state, action) => {
                const id = action.payload;
                state.cartItems = state.cartItems.filter((item) => item.id !== id);
            })
            .addCase(clearCart, (state, _action) => {
                state.cartItems = [];
            });
    },
});

export default cartSlice.reducer;
export const { addToCart, removeFromCart, clearCart } = cartSlice.actions;
export default cartSlice.reducer;
```

In this example, cartSlice is a slice of your Redux store called 'cart,' and it includes reducers for adding to the cart, removing from the cart, and clearing the cart. The slice automatically generates action creators for these actions.

#### Combined reducers

Combine the app reducers with the persistedReducer so that store can be persisted and rehydrated from localStorage. Note this is using the separate library `redux-persist` to do this.

```
import { combineReducers } from 'redux';
import { persistReducer } from 'redux-persist';

import cartReducer from './cartReducer';
import persistConfig from '../persistConfig';

const rootReducer = combineReducers({
  cart: cartReducer,
});

const persistedReducer = persistReducer(persistConfig, rootReducer);

export default persistedReducer;
```

### Actions

In Redux, actions are plain JavaScript objects that represent events or instructions that describe how the state of an application should change. Actions are the only source of information for the Redux store. They typically have two properties:

1. **type**: A string that describes the type of action being performed. It's a unique identifier for the action and is used by reducers to determine how to update the state.

2. **payload**: Any data or information that is needed to update the state. The payload can contain any data type, such as strings, numbers, objects, or arrays. It provides the necessary information for reducers to make changes to the state.

```
// This is pulled to demonstrate the actions, but the appropriate
// place for these is with the reducer.

export const addToCart = createAction<CartItem>('ADD_TO_CART');
export const removeFromCart = createAction<string>('REMOVE_FROM_CART');
export const clearCart = createAction('CLEAR_CART');
```
	
In this example, addItemToCart is an action creator, which is a function that creates and returns an action object. When dispatched, this action object will be sent to the Redux store, and the store's reducers will use the type and payload properties to determine how to update the state.

Reducers are responsible for handling these actions and specifying how the application's state should change in response to them.

Actions provide a structured and predictable way to communicate changes to the Redux store's state, making it easier to manage and reason about application state changes, especially in complex applications.

#### Dispatching an action

```
import { addToCart } from "../../state/reducers/cartReducer";

…

const ProductDetail = () => {
  const { productId } = useParams();
  const navigate = useNavigate();
  const dispatch = useDispatch();

  const tempProductId: string = productId ? productId : "";
  const cartItem: CartItem = new CartItem(tempProductId, "Vest", 12.23, 1);

  const handleAddToCart = (item: CartItem) => {
    // addToCart is the dispatched action. It is "caught" by the cart
    // slice.
    dispatch(addToCart(item));
    navigate("/cart");
  };

  return (
    <div>
      <h2>Product Detail</h2>
      <div>{product ? `Product ID: ${product.id}` : "Product not found"}</div>
      <button onClick={() => handleAddToCart(cartItem)}>Add to Cart</button>
    </div>
  );
};
```

#### State

The type defining the "shape" of the state.

```
import { CartItem } from "../models/CartItem";


export interface RootState {
    cart: {
        cartItems: ReadonlyArray<CartItem>;
    };
    // TODO implement this
    // user: {
    //   currentUser: User | null;
    // };
}
```

Can select from the state with it:

```
const Cart: FC = () => {
  // Using RootState as type selector type
  const cartItems = useSelector((state: RootState) => state.cart.cartItems);

  return (
    <div>
      <h2>Cart</h2>
      <p>
        <Link to={`/`}>Home</Link>
      </p>

      {cartItems.length === 0 ? (
        <p>Your cart is empty.</p>
      ) : (
        <ul>
          {cartItems.map((item: CartItem) => (
            <li key={item.id}>
              {item.name} - Quantity: {item.quantity} - Price: {item.price}
            </li>
          ))}
        </ul>
      )}
    </div>
  );
};

export default Cart;
```

## Redux Toolkit

Redux Toolkit is designed to simplify and streamline the Redux setup process. It provides a set of utilities and abstractions that help streamline Redux development. Many of the examples in this file use the toolkit for simplification.
