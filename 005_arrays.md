# Arrays

## beginner - intermediate

1. Find sum of an array and display the output . Example [10,4,5,2,5,6,9].
```javascript
const sum = arr => arr.reduce((a,b)=> a+b);
console.log(sum([10,4,5,2,5,6,9]));
```
2. Find average of an array and display the output.
```javascript
const avg = arr => arr.reduce((a,b)=>a+b) / arr.length;
console.log(avg([5,10,15]))
```
3. Find maximum and minimum of an array.
```javascript
const maxAndMin = arr => ({max: Math.max(...arr), min: Math.min(...arr)});
console.log(maxAndMin([5,2,9]))
```
4. Find Median and Mode of an array.
    - Median : (N+1/2)th term.
    - Mode : Most repeating term
```javascript
const medianAndMode = arr => {
  if(arr.length === 0)
    return {};
  arr = arr.sort((a,b)=> a-b);
  const median = arr[Math.floor((arr.length + 1) / 2)-1];
	const freq = arr.reduce((obj, n)=> {
    if(!obj[n])
      obj[n] = 1;
    else
      obj[n] += 1;
    return obj;
  }, {});
  const highestFreq = Math.max(...Object.values(freq));
  if(highestFreq === 1) {
    return {
      median,
      mode: "nil"
    }
  }
  const mode = +Object.keys(freq).find(key => freq[key] === highestFreq);
  return {
    median,
    mode
  }
}
console.log(medianAndMode([1,2,3,4,5]))
```
5. Find sum of two arrays.
    - [3,5,2,9,4] = 3+5+2+9+4 = 23
    - [6,2,8,1,3] = 6+2+8+1+3 = 20
    - Final Output : 20+23 = 43
```javascript
const sumOfTwoArrays = (arr1, arr2) => [...arr1, ...arr2].reduce((a,b)=> a+b);
console.log(sumOfTwoArrays([3,5,2,9,4], [6,2,8,1,3]))
```
6. Find number of constants and vowels in a string.
```javascript
const countVowels = str => {
  let consonants = 0, vowels = 0;
  for(char of str.toLowerCase()) {
		if(["a", "e", "i", "o", "u"].includes(char))
      vowels++;
    else
      consonants++;
  }
  return {vowels,consonants}
}
console.log(countVowels("testing"))
```
7. Shift an array by X to right.
    - Example [1,2,3,4,5] after shifting to right [5,1,2,3,4]
```javascript
const cycRotate = (arr, x) => {
  let temp = arr.reverse();
  let result = "";
  for(let i = x % temp.length, j = 0; j < temp.length; j++) {
    result += temp[i];
    i++;
    if(i === temp.length)
      i = 0;
  }
  return result.split("").reverse().map(n => +n)
}
console.log(cycRotate([1,2,3,4,5],1))
```

## Advanced

1. Find the sum of two matrix.
```javascript
const sumOfTwoMatrix = (arr1, arr2) => {
  let sum = [];
  for(let i = 0; i < arr1[0].length; i++) {
    for(let j = 0 ; j < arr1.length; j++) {
      if(j===0)
      	sum[i] = [];
      sum[i][j] = arr1[i][j] + arr2[i][j];
    }
  }
  return sum;
}
console.log(sumOfTwoMatrix([[1,1],[2,2]],[[10,10],[10,10]]))
```
2. Display transpose of matrix. Explaination https://www.varsitytutors.com/linear_algebra-help/the-transpose
```javascript
const transpose = m => m[0].map((x,i) => m.map(x => x[i]));
console.log(transpose([[1,4],[5,8]]))
```
3. Find Identity matrix. Explanation https://www.varsitytutors.com/hotmath/hotmath_help/topics/identity-matrix
```javascript
const identityMatrix = arr => {
  let temp = [];
  for(let i = 0; i < arr[0].length; i++) {
    for(let j = 0; j < arr.length; j++) {
      if(j === 0)
        temp[i] = [];
      if(i===j)
        temp[i][j] = 1;
      else
        temp[i][j] = 0
    }
  }
  return temp;
}
console.log(identityMatrix([[1,4],[5,8]]))
```
