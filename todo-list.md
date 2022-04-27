```
npm install redux react-redux

```

* create folder Redux
* Having store.js
* createStore from redux
* create reducer.js and have rootReducer
* Add redux devtool extensions in store to debugs on Chrome
* useSelector to access global state

## What I learned from REDUX course
- To apply Redux in React application, there are followings steps:
1. Create store

```
import { createStore } from "redux";
import rootReducer from "./reducer";
import { composeWithDevTools } from "redux-devtools-extension";

const composeEnhancers = composeWithDevTools();

const store = createStore(rootReducer, composeEnhancers);

export default store;

```
* using composeEnhancers to add redux-devtools-extension as middleware on Chrome in React App
* The store needs three parameters including rootReducer, initialValue, enhancers

2. The Store will need Reducer to update global state so that Reducer will need two parameters including initalState and action
```
const initValue = {
  todoList: [
    { id: 1, name: "Learn JavaScript", completed: false, priority: "High" },
    { id: 2, name: "Learn Redux", completed: false, priority: "Medium" },
    { id: 3, name: "Learn Java", completed: false, priority: "Low" },
  ],
};

const rootReducer = (state = initValue, action) => {
  console.log(state, action);
  switch (action.type) {
    case "todoList/addTodo":
      return {
        ...state,
        todoList: [...state.todoList, action.payload],
      };

    default:
      return state;
  }
};

export default rootReducer;

```
3. action should be a object or function returning a object which have two properties type and payload
```
const addTodo = (data) => {
  return {
    type: "todoList/addTodo",
    payload: data,
  };
};

export default addTodo;

```
4. We need enventhandler to dispatch a action to store. Therefore, we use useDispatch hook to send action to store in Redux
```
import { useDispatch, useSelector } from "react-redux";
const dispatch = useDispatch();
const handleAddButton = () => {
  dispatch(
    addTodo({
      id: uuidv4(),
      name: todoName,
      completed: false,
      priority: priority,
    })
  );
};
```
5. To Access global state in Store, we use hook useSelector which take a function return a state.
