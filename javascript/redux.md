

# Redux


## Essential Rules

### Reducers Must Not Have Side Effects
- should ony depend on their state and action arguments.
- should only return new state based on those arguments
- No: async logic, ajax calls, timeouts, promises, random values, dates, modify variables outside reducer, etc.
- this is so that they behave predictably when called
- especially in time traveling during debugging - would cause app to behave in unexpected ways

### Don't put non-serializable values in store or actions
- e.g. Promises, Symbols, functions or class instances
- exceptions are if the action will be intercepted by a middleware before reaching the reducers, i.e. redux-thunk

## Strongly Recommended

### Use redux-toolkit
- `npm install --save #reduxjs/toolkit`
- provides out of the box functions with suggested best practices
- e.g. setting up store, setsup immer and redux dev tools
- RTK will simplify your logic and ensure that youra app is set up with good defaults

### Use Immer

### Structure Files as Feature Folders or 'Ducks'
- all files for a feature in a same folder
- or ducks pattern, all redux logic for a feature in a single file
- rather then splitting by type of redux code (reducers, actions, etc.)

### Put as Much Logic as Possible in Reducers
- rather than in code that prepares and dispatches action
- ensures more of app is easily testable, and can use time-travel debugging
- except in cases like: generating unique id

### Reducers Should Own the State Shape
- slice reducers should control what values are returned as part of the calculated state
- minimize the use of 'blind spreads/returns' like `return action.payload` or `return {...state, ...action.payload}`
    - They rely on the code taht dispatched the action to correctly format the contents, can lead to bugs if not correct

### Name Sate Slices Based On the Stored Data
- avoid use of word 'reducer'

### Treat Reducers as State Machines
- don't unconditionally update state based on action
- determine new state by current state _and_ action


## Recommended Rules



