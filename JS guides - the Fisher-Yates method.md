## JS guides: the Fisher-Yates method

**On repl.it: https://repl.it/@Art67/Fisher-Yates-method-of-shuffling-an-array**
### What is the Fisher-Yates algorithm?
The Fisher-Yates algorithm shuffles arrays of numbers randomly. Compared to other similar algorithms, the Fisher-Yates approach is superior, as it has been proved to produce truly random, unbiased results. 

### Sources
* https://en.wikipedia.org/wiki/Fisher%E2%80%93Yates_shuffle#Comparison_with_other_shuffling_algorithms
* https://www.kirupa.com/html5/shuffling_array_js.htm

```
function shuffleColours (array) {
		var i = 0;
		var j = 0;
		var tempNum  = null;

		for (i = array.length -1; i > 0; i -= 1) {
			j = Math.floor(Math.random() * (i + 1))
			tempNum = array[i]
			array[j] = tempNum
		}
	}

shuffleColours(12, 55, 99, 43, 78);
```
