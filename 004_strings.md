# Strings

## Beginner to Intermediate

1. Write a program that converts the string into uppercase
```javascript
const upperCaseString = (str) => str.toUpperCase();
console.log(upperCaseString("test"));
```

2. Write a program that reads two strings and append first string to the second. So if first string is Good second string is Morning , the program should print MorningGood
```javascript
const appendFirstToSecond = (str1,str2) => str2 + str1;
console.log(appendFirstToSecond("good", "morning"));
```

3. Program that reads string and count number of characters present in the string
```javascript
const stringLength = str => str.length;
console.log(stringLength("test"));
```

4. Write a program that converts string like "124" to 124
```javascript
const strToNumber = str => +str;
console.log(strToNumber("123"))
```

5. Write a program to delete all vowels from a string. Assume string is not more than 80 characters long
```javascript
const delVowel = str => {
  const temp = [...str];
 	return temp.filter(c=>!["a","e","i","o","u"].includes(c)).join("")
}
console.log(delVowel("hello"))
```

6. Write a program to check whether the string is alphanumeric or not , eg:batman@45 contains digit 45
```javascript
const isAlphanumeric = str => (/\d/.test(str) && /[a-zA-Z]/.test(str));
console.log(isAlphanumeric("batman@45"))
```

7. A program that reads three strings and prints the longest and smallest one
```javascript
const stringLengthCompare = (...rest) => {
  const lengths = rest.map(str => str.length);
  const max = rest[lengths.indexOf(Math.max(...lengths))];
  const min = rest[lengths.indexOf(Math.min(...lengths))];
  console.log(`Maximum length: ${max}\nMinimum length: ${min}`);
}
stringLengthCompare("test", "a", "abcde");
```

8. A program that counts number of vowels and consonants in a String?
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

9. Write a program which receives a string str that calculates the length of a string and return true if the length is greater than 7 without using strlen()
```javascript
const greaterThanSeven = str => str.length > 7;
console.log(greaterThanSeven("temporary"))
```

10. Write a program that takes two strings and copies smaller string into bigger string
```javascript
const concatSmallString = (str1, str2) => str2.length > str1.length ? str2 + str1 : str1 + str2;
console.log(concatSmallString("test", "ABCDE"));
```

11. Given a string, determine if it is a palindrome, considering only alphanumeric characters
```javascript
const isPalindrome = str => {
  let temp = [...str], half = Math.floor(temp.length / 2);
  if(temp.length % 2 === 1) 
    temp = [...temp.slice(0,half), ...temp.slice(half+1)];
  return temp.slice(0, half).reverse().join("") === temp.slice(half).join("") ? true : false;
}
console.log(isPalindrome("abba"));
```

12. For a given input string(str), write a function to print all the possible substrings.Without using substr method
```javascript
const substrings = str => {
  let subStr = new Set();
  for(let i = 1; i <= str.length; i++) {
    for(let j = 0; j <= str.length - i; j++) {
      subStr.add(str.slice(j,j+i));
    }
  }
  return subStr;
}
console.log(substrings("tests"));

```

13. Write a program that removes the time from the given date string "Wed April 15, 7pm". It should return only the date without the time.
```javascript
const remDate = str => str.split(",")[0];
console.log(remDate("Wed April 15, 7pm"))
```

14. Write a program that masks all but last four characters of the string "5565534276455423" to '#'
```javascript
const maskLastFourChar = str => str.slice(0,str.length - 4) + "####";
console.log(maskLastFourChar("abcdef"))
```

15. Given a string "tic tac toe is a fun game" convert the first 6 characters to capital case
```javascript
const convertFirstSixToUppercase = str => {
  let temp = [...str], count = 6;
  temp = temp.map(char => {
    if(count !== 0 && /[a-zA-Z]/.test(char)) {
			count--;
      return char.toUpperCase();
    }
    return char;
  })
  return temp.join("");
}
console.log(convertFirstSixToUppercase("tic tac toe is a fun game"));
```

## Advance

1. Given an input string S and two characters c1 and c2, you need to replace every occurrence of character c1 with character c2 in the given string
```javascript
const replaceChar = (str, c1, c2) => [...str].map(char => char===c1 ? c2 : char).join("");
console.log(replaceChar("tests", "s", "/"));
```

2. Given an input string S that contains multiple words, you need to remove all the spaces present in the input string. There can be multiple spaces present after any word
```javascript
const removeSpace = str => str.split(" ").join("");
console.log(removeSpace("Hello World  !!"))
```

3. Reverse the given string word wise. That is, the last word in given string should come at 1st place, last second word at 2nd place and so on. Individual words should remain as it is. example: Input : Welcome to NeoG Camp → Camp NeoG to Welcome
```javascript
const revSentence = str => str.split(" ").reverse().join(" ");
console.log(revSentence("Welcome to NeoG Camp"))
```

4. A program that counts the value of each character and prints the most repeated character?
```javascript
const maxFreqChar = str => {
  const freq = [...str.split(" ").join("")].reduce((obj, char)=> {
    if(!obj[char]) 
      obj[char] = 1;
    else 
      obj[char] += 1;
    return obj;
  }, {});
  const max = Math.max(...Object.values(freq));
  const key = Object.keys(freq).find(key => freq[key] === max);
  return key;
}
console.log(maxFreqChar("abc abbcde bbuy"))
```

5. Write a program to toggle case of each character of the string "good afternoon" (example: "neogcamp" ⇒ "nEoGcAmP" )
```javascript
const toggleCase = str => {
  let uppercaseFlag = true;
  return [...str].map(char => {
    if(/[a-zA-Z]/.test(char)) {
    	uppercaseFlag = !uppercaseFlag;
    	return uppercaseFlag ? char.toUpperCase() : char.toLowerCase();
    }
    return char;
  }).join("");
}
console.log(toggleCase("good afternoon"))
```

6. Given a string "how was your day?" and a word "how", write a program that removes the occurrence of the specified word from given sentence. ( input: string⇒"programming camp are amazing",word⇒ "programming"; output:" camp are amazing")
```javascript
const remWord = (str, rem) => str.toLowerCase().split(" ").filter(word => word !== rem.toLowerCase() ).join(" ");
console.log(remWord("how was your day?", "how"))
```
