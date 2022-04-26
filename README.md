# Learning_Redux

## REDUX STRUCTURE
1. STORE having REDUCER AND STATE
2. DISPATCH getting a object of action or a function of action creator
3. ACTION will be a object having type and payload

## REDUX PROCESS
1. User click on UI to update his balance after depositing $10
2. DISPATCH getting that actionCreator from EVENT HANDLER onClick={deposit(10)}
```
const deposit = (data) => {
  return {
    type: 'DEPOSIT',
    payload: data
  }
}
 ```
 3. DISPATCH send a message to REDUCER taking (initialState, action)
 
 ```
 const initalValue = {
  value: 0
 }
 
 const rootReducer = (state = initialValue, action) => {
  switch(action.type){
    case 'DEPOST':
      return {
        ...state,
        value: state.value + action.payload
      }
      
     default:
      return state
  }
  
 }
 ```
 
 4. REDUCER will update the inital state and then when state changes UI changes.
