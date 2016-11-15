# React best practices

## State management
Application state like with a normal react app can be provided by redux.

![an image](http://i.imgur.com/fULPdXU.png)


## Actions/Reducers
- Responsibiliy of changing state belongs to the reducer.
- Every time an action is called, that action interacts with the reducer. The reducer does state changes on the State or Store model.
- Each `dispatch` call invokes a function, which returns the action object. Redux is responsible for taking this action object and passing it over to the reducer.
- The reducer function takes two parameters, state and action. It role is to make modifications to the state based upon the action.
- The `switch` statement in the reducer will look at the Action.type and set the relevant states.
- The `setIn` method from immutable.js is used to set nested data on the state object. It takes an array of strings (which is what it uses to traverse the tree) and a value for the specified node.
- The new state is now available in the component `props` and since the `props` have changed the component needs to `render`
- 

