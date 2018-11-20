# JavaScript ES6: Destructuring

### What is 'destructuring'?
* In JavaScript, when we 'destructure' an array, we  can treat its items as distinct variables. Similarly, when we destructure an object, we treat its properties as distinct variables.
* Destructuring won't destroy the original array or object.

#### Example 1
let's destructure an **array** with three items into variables.

```
const cake = ['chocolate', 'fudgy', 'Disaster! All gone!'];

// Destructure the array into variables
const [flavour, texture, remaining] = cake;

// You can now grab each item as a variable of the destructured array.
console.log(flavour);
console.log(texture);
console.log(remaining);
```
:star: Run it here: https://repl.it/@Art67/InsistentButteryNetwork

#### Example 2
* If you only want to grab one item out of several in an array, you can do so with commas. In this example, you replace the first item with a comma and grab just the second one. Note that all items following the item you've output are implicitly omitted.
```
const [, irresistible] = ['chocolate', 'brownies', 'muffins','carrot cake', 'gingernuts', 'shortbread'];

console.log(irresistible);
```

:star: Run it here: https://repl.it/@Art67/ES6-destructuring-one-cake-out-of-many-in-an-array?language=javascript


#### Example 3
You can also separate an item from the rest with the `...rest` operator and still access an item from that bunch.

```
const [choc, ...rest] = ['chocolate', 'brownies', 'muffins','carrot cake', 'gingernuts', 'shortbread'];

console.log(rest[0]);

// Count your blessings
console.log(rest.length);
```

:star: Run it here: https://repl.it/@Art67/ES6-destructuring-the-rest-of-those-cakes?language=javascript


#### Example 4
Let's destructure an **object**:

```
const coffee = {
roast: 'dark',
aroma: 'intense',
origin: 'Java'
};

const {roast, aroma, origin} = coffee;

console.log(aroma);
```

Object-destructuring works much the same way as array-destructuring, as you can see.
:star:  Run it here: https://repl.it/@Art67/ES6-destructuring-objects


#### Example 5
We can destructure nested objects and grab multiple properties in one go:

```
const cocktails = {
  white: {
      vodka: {
        coffee: 'White Russian',
        lime: 'Caipiroska',
        cranberry: 'Cosmopolitan' 
        },
      gin: 'Singapore Sling',
      rum: 'Mojito'             
         },
  dark: {
       rum: 'Cuba Libre'
       }
   };


const {rum} = cocktails.white;
console.log(rum);

const {coffee, lime} = cocktails.white.vodka;
console.log(coffee, lime);
```
:star:  Run it here:  https://repl.it/@Art67/ES6-destructuring-nested-objects?language=javascript

### Sources:
* https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment
* https://wesbos.com/destructuring-objects/
* https://javascript.info/destructuring-assignment
