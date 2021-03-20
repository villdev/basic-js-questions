# Numbers

1. Write a program to input 2 numbers and display the sum of the numbers to the console.

    ```
    Input Number 1: 20
    Input Number 2: 40
    Sum : 60
    ```
```javascript
const sum = (...rest) => {console.log(rest.reduce((a,b)=>a+b))};
sum(20,40)
```

2. Write a JavaScript program to calculate the simple interest given P,R,T with the given formula.
   Formula:
   `SI = (P * T * R) / 100`
   Where:
   P = principal amount
   T = time
   R = rate
   SI = simple interest

    ```
    Input: P=100, R=6%, T=2
    Output: 12
    ```
```javascript
const si = (p,r,t) => (p * r * t)/100;
console.log(si(100,6,2))
```

3. Write a program to calculate the kinetic energy of a body with mass 'm' and volume 'v'.

    Formula : `0.5 * m * v * v`
```javascript
const kineticEnergy = (m,v) => 0.5 * m * v * v;
console.log(kineticEnergy(10,2))
```

4. Write a program to convert Fahrenheit to Celsius. For Celsius to Fahrenheit conversion use:
   `T = 9*T/5 + 32`
   'T' is the temperature on the Celsius scale.

    ```
    Input: 56
    Output: 13.33333
    ```
```javascript
const fahrenToCelsius = (t) => ((t-32)*5)/9; //wrong formula in example
console.log(fahrenToCelsius(56))
```

5. Calculate the area, perimeter of a s1.re of side 'a'. Also, calculate the surface area and the volume of a cube of side 'a'.

    Formula :

    `Area: a*a`

    `Perimeter: 4*a`

    `Surface Area: 6*a*a`

    `Volume: a*a*a`
```javascript
const square = (a) => { console.log(`Area: ${a*a} \nPerimeter: ${4*a} \nSurface Area: ${6*a*a} \nVolume: ${a*a*a}`) };
console.log(square(5))
```

6. Given the Cost Price(CP) and Selling Price(SP) of a product. Write a Program to Calculate the Profit or Loss.

    ```
    Input: CP = 1500, SP = 2000
    Output: 500 Profit

    Input: CP = 3125, SP = 1125
    Output: 2000 Loss
    ```
```javascript
const profitOrLoss = (cp, sp) => cp < sp ? `${sp-cp} Profit` : (cp > sp ? `${cp-sp} Loss` : "No profit or loss");
console.log(profitOrLoss(1500,2000))
```

7. Write a program to calculate sum of N natural digits, as input by the users?

    ```
    Enter a positive integer: 100
    Sum = 5050
    ```
```javascript
const sumOfNumbers = (n) => n * (n + 1) / 2;
console.log(sumOfNumbers(100))
```

8. Write a Program to Print N Odd Number in Descending Order.

    ```
    Input : 4
    Output : 1
    3
    5
    7
    ```
```javascript
const printOddNoDesc = (n) => {
  for(let i = 1, j = 0; j < n; i+= 2, j++)
    console.log(i); 
}
printOddNoDesc(4)
```

9. Write a JavaScript program to compute the sum of all digits that occur in a given string.

    ```
    Input: 1234
    Output: 1+2+3+4 = 10
    ```
```javascript
const sumOfAllDigits = (n) => {
  let sum = 0;
  while(n > 0) {
    sum += n % 10;
    n = Math.floor(n/10);
  }
  return sum;
}
console.log(sumOfAllDigits(1234))
```

10. Write a JavaScript program that reverses a number.

    Example:

    ```
    Input:  32243;
    Output:  34223
    ```
```javascript
const revNo = (n) => {
  let rev = "";
  while(n>0) {
    rev += n % 10;
    n = Math.floor(n/10);
  }
  return +rev;
}
console.log(revNo(32243))
```

11. Write a Program to cyclically Rotate a Number by X positions in the left direction, as provided by the user.

    Example-

    ```
    Enter a Number : 1234
    Enter the Number of Rotations : 2
    Output : 3412
    ```
```javascript
const cycRotate = (num, n) => {
  let temp = [...num.toString()];
  let result = "";
  for(let i = n % temp.length, j = 0; j < temp.length; j++) {
    result += temp[i];
    i++;
    if(i === temp.length)
      i = 0;
  }
  return +result
}
console.log(cycRotate(1234,2))
```

12. Write a Program to convert Decimal to Binary.

    ```
    Enter the number to convert: 5
    Binary of Given Number is=101
    ```

    Follow up Question : Write a Program to Convert Octal to Decimal.

    ```
    Enter an octal number: 116
    Octal of Given Number = 78 in decimal
    ```
```javascript
const decimalToBinary = (dec) => {
  let bin = [];
  while(dec > 0) {
    bin = [dec % 2, ...bin];
    dec = Math.floor(dec / 2);
  }
  return bin.join("");
}
console.log(decimalToBinary(5))

const octalToDecimal = (oct) => {
  let dec = 0, i = 0;
  while(oct > 0) {
    dec += (oct % 10) * Math.pow(8,i);
    oct = Math.floor(oct / 10);
    i++;
  }
  return dec;
}
console.log(octalToDecimal(116))
```
