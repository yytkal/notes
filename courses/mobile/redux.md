---
card-decks: mobile
---

# Flux
an application architecture for React utilizing a unidirectional data flow
- the *view* react to changes in *stores*
- the only thing can update data in a *store* is *dispatcher*
- the only way to trigger *dispatcher* is *actions*
- *views* trigger *actions*

# Redux
library inspired by flux
www.redjux.js.org
action -> reducer -> update store

## Reducer
takes the previous state and an update and applies the update
- no side effect
- deterministic results exclusively by input

## store
responsible for maintaining state
getter: getState
can only be updated via dispatch()
listeners as callback when state changes

## action
a piece of data contains all information needed for a update
- usually objects with a type key
- https://github.com/redux-utilities/flux-standard-action

# example:simple redux
```js
class Store {
  constructor(reducer, initialState) {
	  this.reducer = reducer
		this.state = initialState
	}

	getState() {return this.state}

	dispatch(update) {
	  this.state = this.reducer(this.state, update)
	}
}

const merge = (prev, next) => Object.assign({}, prev, next)
const DEFAULT_STATE = {user: {}, contacts: []}
const contactReducer  = (state, action) => {
  if (action.type === UPDATE_CONTACT) {
	  return [...state, action.payload]
	}
	return state
}

const userReducer  = (state, action) => {
  if (action.type == UPDATE_USER) {
	    return merge(state, action.payload)
	}
	return state
}
const UPDATE_USER = 'UPDATE_USER'
const UPDATE_CONTACT = 'UPDATE_CONTACT'

const reducer = (state, action) => ({
  user: userReducer(state.user, action),
	contacts: contactReducer(state.contacts, action),
})

const updateUser = update => ({type: UPDATE_USER, payload: update})
const addContact = newContact => ({type: UPDATE_CONTACT, payload: newContact})
const store = new Store(reducer, DEFAULT_STATE)
store.dispatch(updateUser({bar: 'bar'}){bar: 'bar'}})
store.dispatch(addContact({name: 'abc', number: '12345'})
```

# Redux (Actual)
- similar to the homemade SimpleRedux
- npm install redux
```js
// actions.js

export const UPDATE_USER = 'UPDATE_USER'
export const UPDATE_CONTACT = 'UPDATE_CONTACT'

export const updateUser = update => ({type: UPDATE_USER, payload: update})
export const addContact = newContact => ({type: UPDATE_CONTACT, payload: newContact})
```

```js
// reducer.js
import {combineReducers, createStore} from 'redux'
import {UPDATE_USER, UPDATE_CONTACT} from './actions'

const merge = (prev, next) => Object.assign({}, prev, next)
const contactReducer  = (state = [], action) => {
  if (action.type === UPDATE_CONTACT) {
	  return [...state, action.payload]
	}
	return state
}

const userReducer  = (state = {}, action) => {
  if (action.type == UPDATE_USER) {
	    return merge(state, action.payload)
	}
	return state
}

export default const reducer = combineReducers({
  user: UserReducer,
	contacts: contactReducer,
})

```

```js
// store.js
import {createStore} from 'redux'
import reducer from './reducer'

export default const store = createStore(reducer)
```
- store.getState
```js
// read state
import store from './store'
const contacts = store.getState().contacts

// update state
import {addContact, updateUser} from './action'
store.dispatch(updateUser({bar: 'bar'}){bar: 'bar'}})
store.dispatch(addContact({name: 'abc', number: '12345'})
```
## react redux
- npm install react-redux
- provider: pass store to any nested connected components
```js
import {Provider} from 'react-redux'
import store from './store'
...
render() {
  return  (
		<Provider store={store}>
		 	...core logic...
		</Provider>
	)
}
```
- connect, extract subset of application state and pass into screen components
```js
import {connect} from react-redux
import {addContact} from './actions'

const mapStateToProps = state => ({
	contacts: state.contacts,
})
export default connect(mapStateToProps) (ContactListScreen)

export default connect(null, {addContact: addContact})(AddContactScreen)
```

# Async Redux
## Middleware
- provides extension point between dispatching an action and the moments it reach reducer.
- any function with prototype: ((getState, dispatch)) => next => action => void
- npm install redux-thunk
```jsx
import applyMiddleware from 'redux'
const thunk = store => next => action => {
  if (typeof action === 'function') {
    action(store.dispatch)
  } else {
    next(action)
  }
}

const store = createStore(reducer, applyMiddleware(thunk))
```
https://youtu.be/T0elp5K9lLg?t=4544
