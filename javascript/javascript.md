

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
    checkThis: () => {
        console.log(this);
    }
};
asim.checkThis(); // will return same object as foo

const func = foo.checkThis;
func(); // will return global object (unless use strict is set)
```


