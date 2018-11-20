
# ES6 - Sets

Sets are collections of values that are unique within that set, i.e. they cannot occur twice. 
If you duplicate a value in a set and console.log the result, you will get an error.
Note that Sets can include 'undefined' and NaN, although, conventionally, NaN !== NaN. However, in a Set NaN will be treated as equal to itself.

### Source: MDN docs
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set

### Example
Run it on repl.it: https://repl.it/@Art67/ES6-Sets
 
```
let exampleSet = new Set();
exampleSet.add(12);
exampleSet.has(12);  
//Returns true. Comment out line 3 to run line 5.
exampleSet.has(11); 
// Returns false


let secondSet = new Set();
secondSet.add(NaN);
secondSet.add(9, 7);

secondSet.has(NaN);
// Returns true. Comment out line 13 to run line 9.
secondSet.has(9, 7);
```
