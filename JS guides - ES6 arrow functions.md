## JS guides: ES6 arrow functions

**On repl.it: https://repl.it/@Art67/ES6-arrow-functions?language=javascript**

* Arrow functions were introduced in ES6
* Generally, arrow functions are shorter than their ES5 equivalents.
* This allows us to modularise code more efficiently.
* There's less scope for errors (less code = fewer potential errors).
* They haven't replaced 'conventional' functions: arrow functions cannot generally be used as object methods, because they treat the `this` keyword differently from ES5 functions.


* This function is written in the 'traditional' ES5 way:

``` function tripleIt (num) {
return num * 3
}

tripleIt(5); // Returns 15
```

* The same function revamped as an ES6 syntax:
```
let tripleIt = (num) => {
return  num * 3
}
tripleIt(5); // Returns 15
```

* The same example, but without curly braces, parentheses or 'return': all of these can be omitted when the arrow function has a single parameter and returns a value (i.e. is a simple expression).
Note that such succinct functions can be written in one line.

```
let tripleIt = num => num * 3

tripleIt(5) // Returns 15
```

* An example with an object literal:
```
const tripleIt = () => ({num:  3 * 5})

tripleIt(); // Returns 15
```

### Things to remember when using arrow functions
* They are anonymous: this is a disadvantage, because they're harder to trace when you're debugging.
* You need parentheses if the function has two or more arguments.
* You need curly braces if your function encompasses a statement (such as an `if ... else` statement).
* When you do use curly braces, you also need to include the `return`.
* They cannot be used with the `new` keyword, i.e. arrow functions cannot be used as constructors.
* They are not bound to the `this` keyword. This property makes them unsuitable in at least two cases:
1. as object methods.
2. as event handlers.

### Arrow functions and `this`
With arrow functions, `this` inherits its value from its parent scope. 
When you use event listeners in event-handler functions, `this` is bound to the element that the event listener targets (e.g. a button). If you use an arrow function, however, `this` will be bound to the arrow function's scope, which may be the entire window. To avoid such errors, you still need to use conventional functions with event listeners.

More on `this` and arrow functions:
* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions#No_separate_this
* https://medium.freecodecamp.org/when-and-why-you-should-use-es6-arrow-functions-and-when-you-shouldnt-3d851d7f0b26
* https://flaviocopes.com/javascript-arrow-functions/

