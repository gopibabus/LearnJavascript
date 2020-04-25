# ✨Conditionals✨

Making decisions with code.

## 🚦 IF

```js
let rating = 3;

if (rating === 3) {
    console.log("You are a superstar!!");
}
```

## 🚦 ELSE IF

```js
let rating = 2;

if (rating === 3) {
    console.log("You are a superstar!!");
}
else if (rating === 2) {
    console.log("Meets Expectations!!");
}
```

> 👉 We can add multiple else if statements as per requirement.

## 🚦 ELSE

```js
let rating = 2;

if (rating === 3) {
    console.log("You are a superstar!!");
}
else if (rating === 2) {
    console.log("Meets Expectations!!");
}
else {
    console.log("Invalid Rating");
}
```

?> 🎯 We can nest conditionals inside conditionals

## ⚡️Switch Statement

The **switch** statement is used to perform different actions based on different conditions.
This is an alternative to **if else if else**, when working with multiple conditions.

```js
switch (new Date().getDay()) {
  case 0:
    day = "Sunday";
    break;
  case 1:
    day = "Monday";
    break;
  case 2:
     day = "Tuesday";
    break;
  case 3:
    day = "Wednesday";
    break;
  case 4:
    day = "Thursday";
    break;
  case 5:
    day = "Friday";
    break;
  case 6:
    day = "Saturday";
}
```

## ⚡️Ternary Operator

> condition ? True Value : False Value

?> 🎯 We can use this as alternative to **if else**

```js
let age = 10;

let result = (age > 18) ? "Allowed to drink" : "Not allowed to drink";
```