## JS basics: the `reduce` method

**ON REPL.IT: https://repl.it/@Art67/JS-basics-reduce**

### The basics
The **.reduce** method is essentially a loop in disguise: it iterates through an array and performs the function to which it is attached in each cycle.
The key arguments of `.reduce` are what is often denoted as the **'accumulator'** (also commonly labelled 'acc', 'total') and the 'current' value (also commonly labelled 'currentVal', 'total' etc.).
The optional arguments are the *index* and the original *array*.
When `.reduce` performs the loop for the first time, the 'accumulator' takes the value of the first element of the array from the left, and 'current' takes the value of the second element from the left.
In each cycle, 'current' shifts to the next element and takes its value, till the end of the array. The 'accumulator' is also updated with the new result, so if, e.g., in each cycle we add the next element of the array to the previously updated 'accumulator', the latter's value will increase accordingly.
When the loop stops, the calculations performed in each step are reduced to a total.


* A simple example: this will sum up all items in the array.

```
const nums = [2, 3.45, 99, 12.05, 0.558];

const sum = nums.reduce((total, indivNum) => total + indivNum);

console.log(sum);
```

* We can also use .reduce to flatten an arrays of nested arrays. To do so, the 'accumulator' needs to be set to an empty array that will receive all the elements of the flattened array.
The first example uses numbers.

```
const randomNums = [[3, 55, 9], [0.2, 28, 11], [100.5, 3, 0]];

const flatNums = randomNums.reduce((accR, currentR) => {
  return accR.concat(currentR);
}, [] );

console.log(flatNums);
```

* An example with strings. NB Remember to enclose each string element in quotes!

```
const flowers = [['iris', 'daisy', 'rose'], ['violet', 'snapdragon', 'bluebell'], ['camelia', 'poppy', 'jasmin']];

const flatFlowers = flowers.reduce((accF, currentF) => {
  return accF.concat(currentF);
}, [] );

console.log(flatFlowers);
```


* An example with .push. This will return a new array.

```
let arr = [1, 2.67, 1, 2, 3.09, 3.09, 5, 4, 5, 3, 4.00999, 4, 4, 4];
let result = arr.sort().reduce((accumulator, current) => {
    const length = accumulator.length
    if (length === 0 || accumulator[length - 1] !== current) {
        accumulator.push(current);
    }
    return accumulator;
}, []);
console.log(result);
```

* An example with .sort and .push. Will also return a new array.
```
let arr1 = [1, 12, 1, 2, 35, 35, 35, 35, 5, 4, 5, 3,  4, 4, 4];
let result1 = arr1.sort().reduce((acc, currentVal) => {
    const length = acc.length
    if (length === 0 || acc[length - 1] !== currentVal) {
        acc.push(currentVal);
    }
    return acc;
}, []);
console.log(result1);
```
* An example with all four arguments that .reduce takes: add the 'current' value to the 'accumulator' and return the final accumulator plus the array's length.
```
const arrX = [0.9, 2, 11, 3.75];

const arrY = arrX.reduce((totalX, amountX, index, array) => {
  totalX += amountX;
  if (index === array.length-1){
    return totalX + array.length;
  } 
  else {
    return totalX;
  }
});

console.log(arrY);
```

* A more complex example of using .reduce:
Reduce an array of numbers into another array that will contain half the value of each original element (e.g. the original 5 will become 2.5).

To do so, we need to set the accumulator to an empty array and to push the result of each iteration of .reduce into that array. 

Note the syntax: to set a specific initial value for the accumulator (i.e. the value it takes when .reduce performs the first cycle through the array), place a comma followed by the desired initial value after the closing curly brace but within the closing parenthesis.

```
const numz = [6, 0.35, 11, 12.48, 202];

const halves = numz.reduce((acc1, current1) =>{ acc1.push(current1 / 2); 
      return acc1;
}, []);   
console.log(halves);
```

* The .reduce method can be adapted to perform much like .filter and .map do in conjunction, i.e. when chained or used together.
E.g. we can use .reduce to filter out the even numbers from the original array and push only the even ones into our empty array.

```
const mixedNumz = [0, 2, 5.05, 9, 12, 59, 226];

const keepOdd = mixedNumz.reduce((acc2, current2) => {
  if (current2 % 2 !== 0){
    acc2.push(current2);
  }
  return acc2;
}, []);

console.log(keepOdd);
```
