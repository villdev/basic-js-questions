# Objects and Oops

## q01

Given an array of objects of student's marks:

-   Print the name and total marks of each student.
-   Print the name of student whose total marks is highest.
-   Print the name of student whose total marks is lowest.
-   Print the average marks of the class in computer subject.
-   Print the grades of all students:  
     Grade A if total marks is higher than or equal to 75%,  
     Grade B if higher than or equal to 60%,  
     Grade C if higher than or equal to 35%,  
     Grade D if lower than 35%.
-   Print the total number of students passed and their names. Pass when total marks is greater than 35%.

```js script
const studentDetails = [
	{
		roll: "1",
		name: "Rohan Singh",
		maths: 86,
		science: 90,
		english: 75,
		computer: 85
	},
	{
		roll: "2",
		name: "Ritvik Patel",
		maths: 27,
		science: 30,
		english: 35,
		computer: 30
	},
	{
		roll: "3",
		name: "Neha Maurya",
		maths: 75,
		science: 69,
		english: 40,
		computer: 75
	},
	{
		roll: "4",
		name: "Mohit Verma",
		maths: 21,
		science: 31,
		english: 45,
		computer: 40
	},
	{
		roll: "5",
		name: "Karan Trivedi",
		maths: 70,
		science: 80,
		english: 35,
		computer: 60
	}
];
```
```javascript
//Print the name and total marks of each student.
const printNameAndTotalMarks = (studentDetails) => {
  studentDetails.forEach(({name, english, science, computer, maths}) => {console.log(`Name: ${name}\t Total Marks: ${english+science+computer+maths}`)})
}

//Print the name of student whose total marks is highest.
const printTopper = (studentDetails) => {
  totalMarks = {};
  studentDetails.forEach(({name, english, science, computer, maths}) => {
    totalMarks[name] = english+science+computer+maths;
  });
  const highestMarks = Math.max(...Object.values(totalMarks));
  console.log(`Topper: ${Object.keys(totalMarks).find(key => totalMarks[key] === highestMarks)}`);
}

//Print the name of student whose total marks is lowest.
const printLowest = (studentDetails) => {
  totalMarks = {};
  studentDetails.forEach(({name, english, science, computer, maths}) => {
    totalMarks[name] = english+science+computer+maths;
  });
  const lowestMarks = Math.min(...Object.values(totalMarks));
  console.log(`Lowest: ${Object.keys(totalMarks).find(key => totalMarks[key] === lowestMarks)}`);
}

//Print the average marks of the class in computer subject
const avgOfClassInComp = studentDetails => {
  let total = 0;
  studentDetails.forEach(({computer})=> {total += computer})
 	console.log(`Avg of class in Computer Science: ${total/studentDetails.length}`)
}

//Print the grades of all students
const printGrades = studentDetails => {
  grades = {};
  studentDetails.forEach(({name, english, science, computer, maths}) => {
    let total = (english+science+computer+maths)/4;
    if(total >= 75)
      grades[name] = "Grade A";
    else if(total >= 60)
      grades[name] = "Grade B";
    else if(total >= 35)
      grades[name] = "Grade C";
    else
      grades[name] = "Grade D";
    console.log(`Name: ${name}\t Grade: ${grades[name]}`)
  }); 
}

//Print the total number of students passed and their names.
const printPassedStudents = studentDetails => {
  let passedStudents = [];
  studentDetails.forEach(({name, english, science, computer, maths}) => {
    let total = (english+science+computer+maths)/4;
    if(total > 35){
      passedStudents = [...passedStudents, name];
    }
  });
  console.log(`Total number passed: ${passedStudents.length}`);
  passedStudents.forEach(student => {
    console.log(`Name: ${student}\t Status: Pass`)
  })
}

printNameAndTotalMarks(studentDetails);
printTopper(studentDetails);
printLowest(studentDetails);
avgOfClassInComp(studentDetails);
printGrades(studentDetails);
printPassedStudents(studentDetails);
```

## q02

Salary calculation using OOPS concept.

-   Create a Class using ES6 in JavaScript named Employee and assign necessary  
    data members and methods such as name, id, basic salary, HRA, Allowances; define getSalary method which will return the net salary.
-   Create two Instances of Employee with all necessary details.
-   Call the getSalary method of each instance and return the net salary based on your computation.

```javascript
class Employee {
  constructor(name, id, basicSalary, hra, allowances) {
    this.name = name;
    this.id = id;
    this.basicSalary = basicSalary;
    this.hra = hra;
    this.allowances = allowances;
  }
  getSalary() {
    return this.basicSalary + this.hra + this.allowances;
  }
}
const p1 = new Employee("abc", 1, 100, 100, 100);
const p2 = new Employee("de", 2, 200, 200, 200);
console.log(`Net salary \n${p1.name}: ${p1.getSalary()}\n${p2.name}: ${p2.getSalary()}`)
```

## q03

Bank Account (Object Oriented Programming in JavaScript)

-   Create a class and define data members such as name, bank account number,  
    account balance, account type, ifsc and name it as BankAccount.
-   Create three Instances(three customers) of BankAccount with all necessary details.
-   Print the name of customers and their account balances.
-   Calculate the average account balance from all the instances.

```javascript
class BankAccount {
  constructor(name, accountNumber, balance, type, ifsc) {
    this.name = name;
    this.accountNumber = accountNumber;
    this.balance = balance;
    this.type = type;
    this.ifsc = ifsc;
  }
}
const bankAccounts = [ new BankAccount("abc", 1, 100, "saving",1), new BankAccount("de", 2, 200, "saving",2), new BankAccount("f", 3, 300, "saving",3)];
let total = 0;
bankAccounts.forEach(({name, balance}) => {
  console.log(`Customer Name: ${name}\t Balance: ${balance}`);
  total += balance;
})
console.log(`Avg account balance: ${total / bankAccounts.length}`);
```

## q04

Given an array of objects of items in cart, print:

-   the total No. of items
-   the total cart value
-   the total discounted value(sum of dicounted values on each item) based on the given discount
-   total tax amount (18% tax, calculated on total cart value)

```js script
const cartItems = [
	{
		id: "101",
		name: "Oreo",
		count: 2,
		price: 30.0,
		discount: 0.18
	},
	{
		id: "102",
		name: "Red Bull",
		count: 1,
		price: 99.0,
		discount: 0.15
	},
	{
		id: "103",
		name: "Dairy Milk Silk",
		count: 3,
		price: 175.0,
		discount: 0.05
	},
	{
		id: "104",
		name: "Pulse Candy Pack",
		count: 1,
		price: 135.0,
		discount: 0.2
	}
];
```
```javascript
//the total No. of items
const printTotalItems = cartItems => {
  console.log(`Total items: ${cartItems.length}`);
}

//the total cart value
const printTotalCartValue = cartItems => {
  const totalValue = cartItems.reduce((total, {price, discount}) =>total + (price - (price*discount)), 0 );
  console.log(`Total Value of cart: ${totalValue}`)
}

//the total discounted value
const printTotalDiscountValue = cartItems => {
  const totalDiscountValue = cartItems.reduce((total, {price, discount})=> total + (price*discount),0);
  console.log(`Total Discount applied: ${totalDiscountValue}`)
}

//total tax amount
const printTaxAmount = cartItems => {
  const totalValue = cartItems.reduce((total, {price, discount}) =>total + (price - (price*discount)), 0 );
  const tax = 0.18 * totalValue; 
  console.log(`Total tax: ${tax}`);
}

printTotalItems(cartItems);
printTotalCartValue(cartItems);
printTotalDiscountValue(cartItems);
printTaxAmount(cartItems);
```
