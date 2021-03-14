# Functions

## Easy

1. Given a and b, your function should return the value of a<sup>b</sup>  
**Example:**  
**Input:** `power(2,3)` ––> **Output:** `8`
```javascript
// const power = (num, expo) => Math.pow(num,expo);
const power = (num, expo) => {
  if(expo === 1) 
    return num;
  else 
    return num * power(num,expo-1);
}
console.log(power(2,3));
```
2. Given length of a regular hexagon, your function should return area of the hexagon.  
**Example:**  
**Input:** `areaOfHexagon(10)` ––> **Output:** `259.80`
```javascript
const areaOfHexagon = (side) => (3 * Math.sqrt(3) * side * side )/2;
// Math.round(num * 100) / 100
console.log(areaOfHexagon(10));
```
3. Given a sentence, your functions should return the number of words in the sentence.  
**Example:**  
**Input:** `noOfWords(We are neoGrammers)` ––> **Output:** `3`
```javascript
const noOfWords = (str) => str.split(" ").length;
console.log(noOfWords("We are neoGrammers"));
```
4. Given n numbers, your function should return the minimum of them all. The number of parameters won't be accepted from user.  
**Example:**  
**Input:** `findMin(3,5)` ––> **Output:** `3`  
**Input:** `findMin(3,5,9,1)` ––> **Output:** `1`  
*(Hint: Lookup rest parameters in JavaScript)*
```javascript
const findMin = (...rest) => Math.min(...rest)
console.log(findMin(3,5,9,1)); //1
```
5. Given n numbers, your function should return the maximum of them all. The number of parameters won't be accepted from user.  
**Example:**  
**Input:** `findMax(3,5)` ––> **Output:** `5`  
**Input:** `findMax(3,5,9,1)` ––> **Output:** `9`  
*(Hint: Lookup rest parameters in JavaScript)*
```javascript
const findMax = (...rest) => Math.max(...rest)
console.log(findMax(3,5,9,1)); //9
```
6. Given three angles of a triange, your function should return if it is a scalen, isosceles, equilateral triangle or not a triangle at all.
**Example:**  
**Input:** `typeOfTriangle(30, 60, 90)` ––> **Output:** `Scalen Triangle`
```javascript
const typeOfTriangle = (a,b,c) => {
    return (a === b && b === c) && 'Equilateral Triangle' ||
  (a === b || a === c || b === c) && 'Isosceles Triangle' ||
  'Scalene Triangle';
}
// (a <= 0 || b <= 0 || c <= 0) && "error" || (a+b <= c || a+c <=b || b+c <=a) && "wrong" ||
console.log(typeOfTriangle(30, 60, 90));
```

## Medium

1. Given an array, your function should return the length of the array.  
**Example:**  
**Input:** `arrayLength([1,5,3,7,8])` ––> **Output:** `5`
```javascript
const arrayLength = (arr) => {
//   return arr.length;
  return arr.reduce((length, instance)=> length+1,0)
}
console.log(arrayLength([1,5,3,7,8]));
```
2. Given an array and an item, your function should return the index at which the item is present.  
**Example:**  
**Input:** `indexOf([1,6,3,5,8,9], 3)` ––> **Output:** `2`
```javascript
const indexOf = (arr, item) => arr.indexOf(item);
console.log(indexOf([1,6,3,5,8,9], 3));
```
3. Given an array and two numbers, your function should replace all entries of first number in an array with the second number.  
**Example:**  
**Input:** `replace([1,5,3,5,6,8], 5, 10)` ––> **Output:** `[1,10,3,10,6,8]`
```javascript
const replace = (arr, item, replacement) => arr.map(instance => instance === item ? replacement : instance)
console.log(replace([1,5,3,5,6,8], 5, 10));
```
4. Given two arrays, your function should return single merged array.  
**Example:**  
**Input:** `mergeArray([1,3,5], [2,4,6])` ––> **Output:** `[1,3,5,2,4,6]`
```javascript
const mergeArray = (arr1, arr2) => [...arr1, ...arr2];
console.log(mergeArray([1,3,5], [2,4,6]));
```
5. Given a string and an index, your function should return the character present at that index in the string.  
**Example:**  
**Input:** `charAt("neoGcamp", 4)` ––> **Output:** `c`
```javascript
const charAt = (str, index) => str[index];
console.log(charAt("neoGcamp", 4));
```
6. Given two dates, your function should return which one comes before the other.  
**Example:**  
**Input:** `minDate('02/05/2021', '24/01/2021')` ––> **Output:** `24/01/2021`
```javascript
const minDate = (date1, date2) => {
  let d1 = new Date(date1.split("/").join("-"));
  let d2 = new Date(date2.split("/").join("-"));
  return d1 < d2 ? date1 : date2;
}
console.log(minDate('02/05/2021', '24/01/2021'));
```

## Advanced

1. Write a function which generates a secret code from a given string, by shifting characters of alphabet by N places.
**Example:**  
**Input:** `encodeString("neogcamp", 2)` ––> **Output:** `pgqiecor`  
Explanation: 2 represents shifting alphabets by 2 places. a –> c, b –> d, c –> e and so on.
```javascript
const encodeString = (str, n) => {
  let output = "";
  for( const c of str) {
    const charCode = c.charCodeAt(0);
    if(
    	(charCode < 65 || charCode > 122) ||
      (charCode > 90 && charCode < 97)) {
      output += c;
    }
    else {
      let newCharCode = charCode + Math.ceil(n%26);
      if(charCode >= 97 && newCharCode > 122) {
        newCharCode = newCharCode - 26;
      }
     	if(charCode <=90 && newCharCode > 90) {
        newCharCode = newCharCode - 26;
      }
      output += String.fromCharCode(newCharCode);
    }         
  }
  return output;
}
encodeString("neogcamp",2) //"pgqiecor"
```
2. Given a sentence, return a sentence with first letter of all words as capital.  
**Example:**  
**Input:** `toSentenceCase('we are neoGrammers')` ––> **Output:** `We Are NeoGrammers`
```javascript
const toSentenceCase = (str) => {
  let words = str.split(" ");
  let output = "";
  for(word of words) {
    output += word[0].toUpperCase() + word.slice(1) + " ";
  }
  return output;
}
console.log(toSentenceCase("we are neoGrammers")) //We Are NeoGrammers 
```
3. Given an array of numbers, your function should return an array in the ascending order.  
**Example:**  
**Input:** `sortArray([100,83,32,9,45,61])` ––> **Output:** `[9,32,45,61,83,100]`
```javascript
const sortArray = (arr) => {
  return arr.sort(function(a, b){return a - b});
}
console.log(sortArray([100,83,32,9,45,61])); //[ 9, 32, 45, 61, 83, 100 ]
```
4. Given a sentence, your function should reverse the order of characters in each word, keeping same sequence of words.  
**Example:**  
**Input:** `reverseCharactersOfWord('we are neoGrammers')` –––> **Output:** `ew era sremmarGoen`
```javascript
const reverseCharactersOfWord = (str) => {
  let words = str.split(" ");
  let output = "";
  for (word of words) {
    output += word.split("").reverse().join("") + " ";
  }
  return output;
}
console.log(reverseCharactersOfWord("we are neoGrammers"));//ew era sremmarGoen 
```
