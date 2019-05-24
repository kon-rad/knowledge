

# JavaScript

#### 'use strict'
- stops default assignment of window object to this, this will be undefined
- undefined variables will throw error
- not allowed to delete variables, functions, or arguments to functions
- stricter 'eval' - not allowed to define variables

#### pass by value or by reference?
- primitive types: value
    - when passed to function, modified inside, the copy is modified
- objects: by reference
    - when passed to function, changed, you change what it points to
#### NaN
- if a !== a is true, then a must be NaN, because only NaN is not equal to itself

#### Function Closures
- Closure is a special set of references to variables that a function needs in order to execute
    - exist in scope outside of the functions scope
    - refer to variables outside of its scope
    - they exist after the outer function executed
```
const foo = [];
for (let i = 0; i<10; i++) {
    ((y) => {
        foo[y] = () => y;
    })(i);
}
console.log(foo[0]());
console.log(foo[1]());
console.log(foo[2]());
```

#### The 'this' Keyword
- it's defined by the calling context
```
const foo = {
    checkThis: function() {
        console.log(this);
    }
};
foo.checkThis(); // will return same object as foo

const func = foo.checkThis;
func(); // will return global object (unless use strict is set, then it will be undefined)
```

#### call, apply and bind functions
- `call` and `apply` stabalizes the `this` value for a function
- `bind` sets the value of `this` for a function
```
function a(b, c, d) {
    console.log(this, b, c, d);
}
a.call(1, 2, 3, 4); // will return 1 2 3 4
a.apply(1, [2, 3, 4]); // will return 1 2 3 4

const a = function() {
    console.log(this);
}.bind(1);
a(); // will return 1
```

### What is the prototype chain?
- js will look on curent object for a property
    - if not found it will look down the prototype chain
- you can assign an object as a `__proto__` of another object (ES6)
- also can use Object.create(ExistingObj)
- you can check with isPrototypeOf method
- classical: like architectual diagram and actual house
- prototypal: no architectual diagrams, only houses built based on actual houses
- can simulate 'private' properties by using closures (return first_name + ' ' + last_name;
        this returns value passed in constructor);


### Event capturing and Event bubbling
- when you click on a button:
        1. there is a event capturing phase which goes from the window (root) element to the button
        2. event bubbling phase, goes from button to the window element
- 3rd parameter in addEventListener() determines which phase: true = capturing, false = bubbling, default = false

### what is the difference between stopPropagation() and preventDefault() ? 
- stopPropagation prevents event from capturing down and bubbling up
- preventDefault allows event to continue, but it doesnt perform it's usual operations (e.g. checkbox won't get checked)


