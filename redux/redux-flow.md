# How to change state with Redux

## Provide the store to the app

```jsx
// src/index.js

import React from 'react'
import ReactDOM from 'react-dom'
import { Provider } from 'react-redux'

import { App } from './App'
import createStore from './createReduxStore'

const store = createStore()

// As of React 18
const root = ReactDOM.createRoot(document.getElementById('root'))
root.render(
  <Provider store={store}>
    <App />
  </Provider>
)
```

## Dispatch action

Technically action creator is dispatched and it returns an action object that describes the desired chages

```jsx 
// Rest of the code

const dispatch = useDispatch()

//  this is action creator
const addItemToCart = () => {
    //  this is the action with type and an object
return {
    type: "ADD_ITEM_TO_CART"
    payload: {
        bookName: "Harry Potter and the Goblet of Fire",
        noOfItem: 1,
        }
    }
}

<button onClick = {() => dispatch(addItemToCart())}>Add to cart</button>

// Rest of the code
```

## Create reducer function

Which takes in 2 params - action and current state and reduces them into new updated instance of state

```jsx
const initialCartState = {    
    noOfItemInCart: 0,          
    cart: []                              
}

// NOTE: 
// It is important to pass an initial state as default to 
// the state parameter to handle the case of calling 
// the reducers for the first time when the 
// state might be undefined

const cartReducer = (state = initialCartState, action) => {
    switch (action.type) {
        case "ADD_ITEM_TO_CART": 
            return {
                ...state,
                noOfItemInCart: state.noOfItemInCart + 1,
                cart : [
                    ...state.cart,
                    action.payload
                ]
            }
        case "DELETE_ITEM_FROM_CART":
            return {
                // Remaining logic
            }
        default: 
            return state  
    }       // Important to handle the default behaviour
}           // either by returning the whole state as it is 
            // or by performing any required logic
```
So in the above example, we first make a copy of the entire state using the spread operator `...state`. Then we increment the `noOfItemInCart` by 1, update the cart array by adding the new object passed in the `action.payload` shown below, and then finally return the updated object.

```jsx
{
    bookName: "Harry Potter and the Goblet of Fire",
    noOfItem: 1,
}
```
## New state is sent to the store

#### Initial store:

```jsx
// this is how the store object structure looks like
{
    noOfItemInCart: 2,
    cart: [
        {
            bookName: "Harry Potter and the Chamber of Secrets",
            noOfItem: 1,
        },
        {
            bookName: "Harry Potter and the Prisoner of Azkaban",
            noOfItem: 1
        }
    ]
}
```

#### Updated store:

```jsx
{
    noOfItemInCart: 3, // Incremented by 1
    cart: [
        {
            bookName: "Harry Potter and the Chamber of Secrets",
            noOfItem: 1,
        },
        {
            bookName: "Harry Potter and the Prisoner of Azkaban",
            noOfItem: 1
        },
        { // Newly added object
            bookName: "Harry Potter and the Goblet of Fire",
            noOfItem: 1,
        }
    ]
}
```