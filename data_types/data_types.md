# 🔥 Data Types

## ✨ Primitive Type: numbers ✨

Javascript has one **number** type.<br>
👉 Positive numbers!<br>
👉 Negative numbers!<br>
👉 Whole numbers (integers)!<br>
👉 Decimal numbers!<br>

```js
/* ➕ Addition*/
50 + 5; //55

/* ➖ Subtraction*/
50 - 5; //50

/* ✖️ Multiplication*/
50 * 5; //250

/* ➗ Division*/
50 / 5; //10

/* % Modulo*/
55 % 5; //5

/* 🔠 Expressions*/

10 + 2 * 6; //22
```

## 🔥 NOT A NUMBER (NaN)

> NaN is a numeric value that represents something that is not a number

```js
0 / 0; //NaN

NaN + 5; //NaN
```

## ✨ Primitive Type: Booleans ✨

> 👉 Booleans are simple (True or False), (Yes or No), (1 or 0) values.

```js
let isLoggedIn = true;
let gameOver = false;
const isResultDeclared = true;
```

## 😬 Variables can change Type.

```js
let numOfDonuts = 12;
numOfDonuts = false;
numOfDonuts = 12365489;
```

## ✨ Primitive Type: String ✨

👉 Strings are pieces of text or strings of characters.<br>
👉 We wrap them in quotes.<br>
👉 Whether you use single or double quotes, just make sure you are consistent.<br>
🎯 **typeof** is a built in operator to identify type of value in a variable.<br>
🎯 **length** is a built in property used to find length of given variable.<br>
👉 Strings are indexed. Each character has a corresponding index.<br>
💥 Strings are immutable, we can't change individual characters of a string directly (or) we can't change the original String<br>

```js
let firstName = 'Gopibabu';
let msg = 'I am the author of this file';
let notice = "This is the 'important' information";
let typeOfVariable = typeof notice;
let lengthOfName = 'Srungavarapu'.length;
let songName = 'Sunrise Everyday';
let firstIndex = songName[0]; //S
songName[0] = 'D';
songName[100]; //Undefined
console.log(songName); //Sunrise Everyday
```

## ✨ String Escapes ✨

> 👉 \n : new line <br>
> 👉 \' : single quote <br>
> 👉 \' : double quote <br>
> 👉 \\ : backslash <br>

```js
let message = "He said that he can't watch"; //He said that he can't watch
```

## ✨ Null and Undefined ✨
🎯 NUll : Intentional absence of any value. Can be assigned to variable.
🎯 Undefined : Variables that do not have an assigned value.

```js
let loggedInUser = null; //Value is explicitly nothing
loggedInUser = 'Gopibabu';
loggedInUser[100]; //undefined
```




