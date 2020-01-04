

# Redux


## Essential Rules

### Reducers Must Not Have Side Effects
• should ony depend on their state and action arguments.
• should only return new state based on those arguments
• No: async logic, ajax calls, timeouts, promises, random values, dates, modify variables outside reducer, etc.
• this is so that they behave predictably when called
• especially in time traveling during debugging - would cause app to behave in unexpected ways

### Don't put non-serializable values in store or actions
• e.g. Promises, Symbols, functions or class instances
• exceptions are if the action will be intercepted by a middleware before reaching the reducers, i.e. redux-thunk




