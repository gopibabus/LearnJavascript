# 🔥Significance of call, apply & bind methods

<img src="./assets/images/this.gif" alt="this" height="400"/>

?> The **this** keyword in JavaScript behaves differently when compared to other programming languages. In other programming languages **this** refers to **current instance of a class**. Whereas in JavaScript, **this** depends on **how a given function is called**.

```js
const studentInfo = {
  firstName: "John",
  lastName: "Doe",
  printName: function(initial, end) {
    console.log(`${initial} ${this.firstName} ${this.lastName} to the ${end}`);
  }
};

studentInfo.printName('Welcome', 'College');//Welcome John Doe to the College

const printFullName =  studentInfo.printName;
printFullName('Welcome', 'College');//Welcome undefined undefined to the College
```

When we call **studentInfo.printName**, this in **printName** refers to **studentInfo** object. When we call **printFullName**, **this** in **printName** refers to **window(global)** object.

In order to fix this issue with **this** reference. JavaScript introduced 3 methods to pass **this** reference manually.

## ⚡call( ) Method

> The **call( )** method calls a function with a given this value and arguments provided individually.

```js
const studentInfo = {
  firstName: "John",
  lastName: "Doe",
  printName: function(initial, end) {
    console.log(`${initial} ${this.firstName} ${this.lastName} to the ${end}`);
  }
};

studentInfo.printName('Welcome', 'College');//Welcome John Doe to the College

const printFullName =  studentInfo.printName;

const printFullName =  studentInfo.printName;
printFullName.call(studentInfo, 'Welcome', 'College');//Welcome John Doe to the College
```

In the above example we are passing *studentInfo* as this into *printFullName* function using **call** method along with arguments.

[🌐 MDN Documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/call)

## ⚡apply( ) Method

> The **apply( )** method calls a function with a given **this** value, and **arguments provided as an array**.

```js
const studentInfo = {
  firstName: "John",
  lastName: "Doe",
  printName: function(initial, end) {
    console.log(`${initial} ${this.firstName} ${this.lastName} to the ${end}`);
  }
};

studentInfo.printName('Welcome', 'College');//Welcome John Doe to the College

const printFullName =  studentInfo.printName;
printFullName.apply(studentInfo, ['Welcome', 'College']);//Welcome John Doe to the College
```

In the above example we are passing **studentInfo** as this into **printFullName** function using **apply** method along with arguments as an array.

[🌐 MDN Documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/apply)

## ⚡bind( ) Method

> The **bind()** method creates a new function that, when called, has its **this** keyword set to the provided value, with a given sequence of arguments preceding any provided when the new function is called.

```js
const studentInfo = {
  firstName: "John",
  lastName: "Doe",
  printName: function(initial, end) {
    console.log(`${initial} ${this.firstName} ${this.lastName} to the ${end}`);
  }
};

studentInfo.printName('Welcome', 'College');//Welcome John Doe to the College

const printFullName =  studentInfo.printName;
const printName = printFullName.bind(studentInfo);
printName('Welcome', 'College');//Welcome John Doe to the College
```

In the above example we are passing **studentInfo** as this into **printFullName** function using **bind** method.

[🌐 MDN Documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_objects/Function/bind)