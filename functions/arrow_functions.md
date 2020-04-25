# 🔥Arrow Functions

?> Syntactically compact alternative to a regular function expression.

!> Internet explorer doesn't support Arrow functions.

### ⚓Type 1

```js
const greet = () => {
  console.log("Hello World!!!");
};
greet();
```

```js
const square = (x) => {
  return x * x;
};
square(9);//81
```

```js
const multiply = (x, y) => {
  return x * y;
};
multiply(9, 5);//45
```

### ⚓Type 2 (Implicit return)

> This will apply when function is executing only one statement.

```js
const double = x => {
  return x * 2;
};
double(5);//25

👇🏽👇🏽👇🏽👇🏽👇🏽

const double = x => (
    x * 2
);
double(5);//22

👇🏽👇🏽👇🏽👇🏽👇🏽

/**
 * This will apply for only cases where we can fit entire logic 
 * in a single line
*/
const double = x => x * 2;
double(5);
```

```js
const nums = [2, 5, 6, 9, 12, 45, 32];

const doubles1 = nums.map(function(n) {
  return n * 2;
});

const doubles2 = nums.map(n => {
  return n * 2;
});

const doubles3 = nums.map(n => n * 2);

doubles1;//[ 4, 10, 12, 18, 24, 90, 64 ]
doubles2;//[ 4, 10, 12, 18, 24, 90, 64 ]
doubles3;//[ 4, 10, 12, 18, 24, 90, 64 ]
```

```js
const nums = [2, 5, 6, 9, 12, 45, 32];

const parity = nums.map(n => (n % 2 === 0 ? "even" : "odd"));
parity;//[ 'even', 'odd', 'even', 'odd', 'even', 'odd', 'even' ]
```