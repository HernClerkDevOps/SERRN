## Introduction to Redux
Redux is a predictable state container for Javascript applications.

### The 3 Principles of Redux


##### Single Source of Truth
- *All* of your application's state is stored in a single **store**. Your application state is any state that is shared between components. Storing independent component state that does not need to be shared across another component, like the value in a textbox, is a no-no. This would cause unnecessary boilerplate and does not have any added benefit.

##### Read-only State

The only way to change the state is to emit an action, an object describing what happened.

An action is a plain object that represents an intention to change the state. Actions are the only way to get data into the store. Any data, whether from UI events, network callbacks, or other sources such as WebSockets needs to eventually be dispatched as actions if you plan on adding them to the store.

Actions must have a type field that indicates the type of action being performed. Types can be defined as constants and imported from another module. It's better to use strings for type than symbols because strings are serializable.

##### Changes are made with pure functions
To specify how the state tree is transformed by actions, you write pure reducers.

Reducers are just pure functions that take the previous state and an action, and return the next state. Remember to return new state objects, instead of mutating the previous state. You can start with a single reducer, and as your app grows, split it off into smaller reducers that manage specific parts of the state tree. Because reducers are just functions, you can control the order in which they are called, pass additional data, or even make reusable reducers for common tasks such as pagination.

### Sample Implementation of React / Redux
---
#### Users.js
React component for users
```
import {bindActionCreators} from 'redux';
import { connect } from "react-redux";
// an async action that gets users
import { getUsers } from './async_actions';
import React, { Component } from 'react';

class DisplayUsers extends Component {
    componentDidMount() {
    	this.getUsers();
    }

    render() {
    	return (
    		{this.props.users.map((u) => (
    			<p>{u.name}</p>
    		))}
    	)
    }

    function mapStateToProps(state) {
      return {
        users: state.users,
      }
    }

    function mapDispatchToProps(dispatch) {
      return bindActionCreators({
        getUsers: getUsers,
      }, dispatch);
}
export default connect(mapStateToProps, mapDispatchToProps)(DisplayUsers);
```
You must call mapDispatchToProps and mapStateToProps with connect() in order to access your data within props: this.props.users
*Note that this.props.users.map will be NULL until the reducer returns the data from the getUsers action.* The reducer will not return anything until the action is called, which would be inside of a function if during the component's life, or in componentDidMount, which is a React lifecycle hook for when the component has finished rendering.

#### async_actions.js
Create an action to fetch users and pass to reducer
```
import * as type from './types'

export function getUsers() {
	return dispatch => {
		//make HTTP request here
		axios.get(`http://server.com/api/users`)
        	.then(function(response) {
           		let users = response.data;
            	      dispatch(getUsersAsync(users));
        });
	}
}

function getUsersAsync(users) {
    return {
        type: type.GET_USERS,
        users
    }
}
```
#### usersReducer.js
Create a reducer for your users action
```
import {GET_USERS} from './../types'
export default function(state=[], action) {
  switch (action.type) {
    case "GET_USERS":
        return action.users
    default:
      return state;
  }
}
```

#### rootReducer.js
Combine all of your actions through the root reducer
```
import { combineReducers } from 'redux';
import DepartmentsReducer from './departmentReducer';
import UsersReducer from './usersReducer';
import ApplicationsReducer from './applicationReducer';
import EmployeeListReducer from './employeeListReducer';
import UserApplicationsReducer from './userApplicationsReducer';
import SupervisorsReducer from './supervisorsReducer';
import AuthReducer from './authReducer';

const rootReducer = combineReducers({
    users: UsersReducer,
    departments: DepartmentsReducer,
    applications: ApplicationsReducer,
    employeeList: EmployeeListReducer,
    userApplications: UserApplicationsReducer,
    supervisors: SupervisorsReducer,
    auth: AuthReducer
});
export default rootReducer;
```
#### store.js
Only have one of these for your entire project
```
import { createStore, applyMiddleware } from 'redux';
import thunk from 'redux-thunk';
import rootReducer from './reducers/rootReducer';
//I highly suggest using redux-logger so you can see your entire state tree in the console

import {createLogger} from 'redux-logger'
var logger = createLogger();

 const store = createStore(
  rootReducer,
  applyMiddleware(thunk, logger)
);
export default store
```
