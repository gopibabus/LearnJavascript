# 🔥Functions

* Functions allow us to write reusable. modular code.
* We define a "Chunck" of code that we can thene xecute at a later point.
* It is 2 step process
    * Define functions💪🏽
    * Run functions🏃🏽‍♂️

```js
function getName() {
  console.log("My name is Gopi");
}
getName(); //My name is Gopi
```

```js
function rollDie() {
  let roll = Math.floor(Math.random() * 6) + 1;
  console.log(`Rolled: ${roll}`);
}

function throwDies() {
  rollDie();
}
throwDies();
```

?> We can call functions from other functions in out script.

## 🗣Arguments & Parameters

> We can write functions thata accept inputs, called **arguments**.

> The variable that we sending to functions are called **arguments** and variables in functions which are accepting values are called **parameters**.

```js
function greet(name) {
  console.log(`Hi ${name}, Good Morning!!!`);
}

greet("gopi"); //'Hi gopi, Good Morning!!!'
```

```js
function rollDie() {
  let roll = Math.floor(Math.random() * 6) + 1;
  console.log(`Rolled: ${roll}`);
}

function throwDies(number) {
  for (let i = 0; i <= number; i++) {
    rollDie();
  }
}
throwDies(4);
```

### 👥Multiple Arguments

```js
function divide(a, b) {
  console.log(a / b);
}

divide(4, 2); //2
divide(4); //NaN
```

!> If you don't pass arguments, then by default javascript will allocate **undefined** to that parameter in a function.

### 📩Return Statement

* **Return** statement will allow us to capture value and store it in a variable.
* You can return only one value from a function.
* **return** statement ends function execution.

```js
function divide(a, b) {
  return a / b;
  console.log("This code won't work");
}

let result = divide(4, 2);
console.log(result);//2
```

```js
function containsPurple(arr) {
  for (let color of arr) {
    if (color === "purple" || color === "magents") {
      return true;
    }
  }
  return false;
}

let colors = ["blue", "white", "purple", "orange"];

containsPurple(colors);
```

## 👀Examples

### 💪🏽Example: Password Validate

> Should be atleast 8 characters
> Cannot contain spaces
> Cannot contain username

```js
function isValidPassword(password, username) {
  if (
    password.length < 8 ||
    password.indexOf(" ") != -1 ||
    password.indexOf(username) != -1
  ) {
    return false;
  }
  return true;
}

isValidPassword("J$ssw0rd123", "gopibabus");//True
```

### 💪🏽Example: Average of arrays of numbers

```js
function avg(arr) {
  let total = 0;
  let length = arr.length;
  for (let num of arr) {
    total += num;
  }
  return total / length;
}

avg([4, 56, 89, 12]);//40.25
```

### 💪🏽Example: Pangram

> A pangram is a sentence that contains every letter of the alphabet.

```js
function isPangram(sentence) {
  sentence = sentence.toLowerCase();
  var alphabets = "abcdefghijklmnopqrstyvwxyz";

  for (let char of alphabets) {
    if (sentence.indexOf(char) === -1) {
      return false;
    }
  }
  return true;
}

isPangram("the five boxing wizards jump quickly"); //true
isPangram("Hi this is john marty"); //false
```

## ✨Scope

> In simple terms, **scope** is variable visibility in a script.
> The location where a variable is defined dictates where we have access to that variable.

### ✳Function Scope

> Visibility of variable confined within a function

```js
let name = 'gopi';

function helpMe() {
    let name = 'john';
    var idea = 'go for cinema';
    let msg = "I'm on fire!!";
    msg; // I'm on fire
    name; //john
}

msg; //⛔NOT DEFINED
name; //gopi
idea; //⛔NOT DEFINED
```

?> In above snippet, **msg** is scoped to the **helpMe** function

?>**let**, **const** and **var** obey function scope.

### ✳Block Scope

> Visibility of variable confined to a block(if, for, while)

```js
let names = ["gopi", "hari", "anil", "mohan"];
let i = 10;
for (let i = 0; i < names.length; i++) {
  console.log(i, names[i]);
}

console.log(i);//10
```

```js
let names = ["gopi", "hari", "anil", "mohan"];
var i = 10;
for (var i = 0; i < names.length; i++) {
  console.log(i, names[i]);
}

console.log(i);//4
```

?> **let** and **const** obey block scope but **var** does not obey block scope.

### ✳Lexical Scope

> Lexical scope is the scope defined at lexing time.

> 😃Lexical scope applies to the functions that are declared inside a function. The inner function has access to variables from parent function.

> 😜If inner function won't find variable that is called inside it, it will search for variable in parent function, there after parent's parent function and so on.

```js
function outer() {
  let movie = "Gundamma Kadha";

  function inner() {
    let movie = "Simha";

    function extraInner() {
      console.log(movie.toUpperCase());
    }
    extraInner();
  }
  inner();
}

outer();//SIMHA
```

## 🤹🏽‍♀️Function Expressions

> Other syntax used to define functions

```js
const square = function(num) {
  return num * num;
};

square(4);//16
```

## 💪🏽Higher Order Functions

### ✳Functions as Objects

```js
const add = function(a, b) {
  return a + b;
};

const subtract = function(a, b) {
  return a - b;
};

const multiply = function(a, b) {
  return a * b;
};

const divide = function(a, b) {
  return a / b;
};

const operations = [add, subtract, multiply, divide];

for (let func of operations) {
  let result = func(30, 5);
  console.log(result);
}

const operation = {
  opera1: add
};

operation.opera1(30, 5);
```

### ✳Functions as Arguments

```js
function callThreeTimes(f) {
  f();
  f();
  f();
}

function cry() {
  console.log("😢😢😢😢😢");
}

callThreeTimes(cry);

function repeatNTimes(action, num) {
  for (let i = 0; i < num; i++) {
    action();
  }
}

repeatNTimes(cry, 5);

function even() {
  console.log("Even number");
}

function odd() {
  console.log("Odd number");
}

function findType(f1, f2) {
  let num = Math.ceil(Math.random() * 10);
  if (num / 2 === 0) {
    f1();
  } else {
    f2();
  }
}

findType(even, odd);
```

### ✳Returning Functions

> Lexical scope applies to the function which is returned from a function. Returned function will carry variables from parent function.

```js
function multiplyBy(num) {
  return function(x) {
    return x * num;
  };
}

let triple = multiplyBy(3);
triple(2);//6

function makeBetweenFunc(x, y) {
  return function(num) {
    return num >= x && num <= y;
  };
}

const isChild = makeBetweenFunc(50, 100);

isChild(56);//True
```

### ✳Callback Functions

> A callback function is a function passed into another function as an argument, which is then invoked inside the outer function.

?> **setTimeout(function, time)** is a **function** which will execute **function** after **time** specified.

```js
function wish() {
  console.log("hello world!!");
}

setTimeout(wish, 2000);

setTimeout(function() {
  console.log("This is a callback😜");
}, 2000);
```

## 🤷‍♂️Hoisting

> The pattern of reading all variable declarations in a script by Javascript before execution is called **Hoisting**. And this will work with only variables which are declared with **var** not with **const** and **let**.

```js
console.log(name); //undefined

var name = "gopi";

console.log(college); //Reference Error

let college = "QIS";
```

> All **functions** are **hoisted**, we can use functions first and declare later in teh script. But **function expressions** are not hoisted.

```js
msg();//Hello World

function msg() {
  console.log("Hello World");
}
```

```js
msg();//Type Error

var msg = function() {
  console.log("Hello World");
};
```