## JS guides: _var_ vs _const_ and _let_

### On repl.it: https://repl.it/@Art67/let-vs-var-scope-examples
* Run the examples in your code editor or on repl.it to see how they work
* The variables const and let were introduced in ES6. One main difference between `var`, `const` and `let` lies in their scope. 

### Main differences: scope
*	**`var`**: its scope depends on where it is declared. A var declared within a function can be used anywhere within this scope. A var declared outside a function body will be accessible anywhere within the global scope.
* **`let`** and **`const`**: their scope is limited to the block in which they are wrapped by a pair of curly braces. Also, unlike `var`, they cannot be hoisted; meaning, you can only access and use let and const after they have been declared.

###	How does this work? 
In the case of var, declarations are read during the first iteration through code and each var is initialised with the 'undefined' value before the next iteration, when code will be read and executed line by line. In contrast, let and const are initialised when JavaScript reaches the line where each is declared.

### Why is it good to limit a variable's scope? 
Because it prevents reassigning variables accidentally (think how often you see the same names or letters in different examples of code; it's easy to choose a common name you've already used) and forces developers to avoid multipurpose variables with meaningless names such as 'foo' or 'x' (fine in short examples, a bad idea in longer code).

### Key terms
*	**`const`**: unlike var and let, you cannot reassign it. You give it a value, and that's that. Note that this is not the same as immutability. If, e.g., you assign an object to a const, you can add or remove keys or change their values. But you can't assign a different object to the same const.

* **`let`**: you can reassign this type of variable (but not hoist it as you can hoist a var). When you use ES6 you'll find that let is used primarily within loops, where you need to be able to change the value of your variable at every step of the iteration.

* **Scope**: the territory within which you can access a variable or a function. When we talk about 'function level scope', we mean that a variable's scope is the function within which it is declared. You can use the variable within that function, but you'll get an error message if you try to use it outside that function's scope.

* **Block scope**: the block within a pair of curly braces. 

* **Hoisting**: the ability to use a variable (var, not let or const) or function before you actually declare it. So you can e.g. call a function at the top of a scope and then define it and it will still work.
#### How does hoisting work? 
Because JavaScript separates declarations from definitions: first it goes through your code, spots all variable and function declarations and puts aside the computer memory they'll need. It's a bit like making a note of all declarations at the top of the scope. Then it goes through the code again, line by line, and executes it.
*	Note that only declarations are hoisted. So a hoisted variable will have the value of ‘undefined’.
*	Generally, it doesn't hurt to start by declaring your variables and functions and then using them. It's also good practice to group all your declarations at the top of their scope, as it makes code more readable for humans. 
*	If you want to know more on var, const, let and hoisting:
https://www.vojtechruzicka.com/javascript-hoisting-var-let-const-variables/ 

### Resources:
https://www.taniarascia.com/es6-syntax-and-feature-overview/

## Examples
### `var` vs `let`
Note how when you run the almost identical examples, in the first case, we cannot console.log let outside its scope, whereas in the second case, we can console.log the var outside its scope.

* `let`: we can console.log it only within its scope; it's not globally available
```
var oz = 2;
if (oz >= 1) {
  let metricWeight = oz * 28.3495;
  console.log(`This weighs ${metricWeight} grams`);
}
console.log(metricWeight);
```
*  `const`: same as let in this respect - but, remember, unlike let, const cannot be reassigned.
```
var oz = 3;
if (oz >= 1) {
  const metricWeight = oz * 28.3495;
  console.log(`This weighs ${metricWeight} grams`);
}
console.log(metricWeight);
```

* `var`: we can console.log it anywhere outside its scope; its value 'leaks' outside the curly brackets that enclose it.
```
var oz = 4;
if (oz >= 1) {
  var metricWeight = oz * 28.3495;
  console.log(`This weighs ${metricWeight} grams`);
}
console.log(metricWeight);



console.log(metricWeight);
```
