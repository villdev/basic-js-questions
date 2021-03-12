# Operators, Branching, Loops

## Easy

1. Write a program to add 5 numbers. The value of numbers are num1=5, num2=13, num3=7, num4=21 and num5=48.
```javascript
const add = (...rest) => (rest.reduce((total, instance)=> total + instance, 0));
console.log(add(5, 13, 7, 21, 48)); //output - 94
```

2. Write a program to take a number input from user and determine whether the number is odd or even.
```javascript
const oddOrEven = (num) => num%2 === 0 ? "even": "odd";
console.log(oddOrEven(9)); //odd
```

3. Write a program to find the maximum and minimum out of two given numbers. The numbers are num1=129 and num2=251.
```javascript
const compareNumbers = (num1, num2) => num1 > num2 ? `max: ${num1} & min: ${num2}` : num2 > num1 ? `max: ${num2} & min: ${num1}` : `${num1} & ${num2} are equal`;
console.log(compareNumbers(129,251)); //max: 251 & min: 129
```

4. Write a program to find the maximum out of three given numbers. The numbers are num1=8, num2=23 and num3=17.
```javascript
const findMax = (...rest) => rest.reduce((accumulator, instance) => instance > accumulator ? instance : accumulator );
console.log(findMax(8,23,17)); //23
```

5. Write a program to find the minimum out of three given numbers. The numbers are num1=35, num2=29 and num3=46.
```javascript
const findMin = (...rest) => rest.reduce((accumulator, instance) => instance < accumulator ? instance : accumulator );
console.log(findMin(35,29,46)); //29
```

6. Write program to take a month as an input from the user and find out whether the month has 31 days or not.
```javascript
const has31Days = (monthNum) => [1,3,5,7,8,10,12].includes(monthNum) ? "Has 31 days": "Does not have 31 days";
console.log(has31Days(9)); // Does not have 31 days //string can be checked in the same way
```

## Intermediate

1. Fizzbuzz - Write a program to return an array from 1 to 100. But for every multiple of 3, replace the number with "Fizz", for every multiple of 5, replace the number with "Buzz" and for every multiples of 3 & 5, replace with "FizzBuzz".

Your output should look something like this `1, 2, Fizz, 4, Buzz, Fizz, 7, 8, Fizz, Buzz, 11, Fizz, 13, 14, FizzBuzz, 16, 17 ..... `
```javascript
const FizzBuzz = () => {
  let arr = [];
  for(i=1; i < 101; i++) {
    let temp = i%3 === 0 ? (i%5 === 0 ? "FizzBuzz" : "Fizz" ): (i%5 === 0 ? "Buzz": i );
    arr = [...arr, temp]; //arr[arr.length] = temp;
  }
  return arr;
}
console.log(FizzBuzz()); // [1,2,Fizz,4,...]
```

2. Print the following star pattern :-

    \* \
    \* \* \
    \* \* \* \
    \* \* \* \* \
    \* \* \* \* \*
```javascript
const printStarPattern = (row) => {
  let temp = "";
  for(let i = 0; i < row; i++) {
    for(let j = i; j>= 0 ; j--)
      temp += "*";
    temp += "\n";
  }
  console.log(temp);
}
printStarPattern(5); 
```

3. Write a program to take a number input from user and print multiplication table 12 times for that number.
```javascript
const printMultTable = (num) => {
  for(let i = 1; i < 13; i++) 
    console.log(`${num} x ${i} = ${num*i}`)
}
printMultTable(5);// 5 x 1 = 5 // 5 x 2 = 10 // ...
```

4. Write a program to return a Fibonacci series : 0,1,1,2,3,5,8,13,21....
```javascript
const createFiboSeries = (num) => {
  let fiboArr = [0, 1];
  for( i = 2; i < num; i++)
    fiboArr = [...fiboArr, fiboArr[i-2] + fiboArr[i-1]]; 
  return num === 1 ? [0] : (num > 1 ? fiboArr : ["error"] );
}
console.log(createFiboSeries(9)); // [0,1,1,2,3,5,8,13,21]
```

5. Write a program to take an input from a user and find its Factorial.
   `Example: Factorial of 5 is 120`
```javascript
const findFactorial = (num) => {
  let signFlag = 1;
  if(num < 0) {
     signFlag = -1;
     num *= signFlag;
  }
  if(num === 0)
    return 1;
  let facto =  num * findFactorial(num-1);
  return signFlag*facto;
}
console.log("Factorial of 5 is: ", findFactorial(5)); // Factorial of 5 is: 120
```
6. Write a Program to take a number input from user and find if the number is Prime or not.
```javascript
const isPrime = (num) => {
  for( i = 2; i < num / 2; i++) {
      if( num%i === 0)
         return false;
  }
  return num <= 0 ? false : true;
}
console.log(isPrime(7)); // true
```

7. Write a program to take a day as an input and determine whether it is a weekday or weekend.
   `Example: Tuesday is weekday.`
```javascript
const checkDay = (day) => ["saturday","sunday"].includes(day.toLowerCase()) ? `${day} is weekend.`: `${day} is weekday.`;
console.log(checkDay("Tuesday")); // Tuesday is weekday.
```
