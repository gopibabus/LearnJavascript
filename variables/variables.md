# 🔥 Variables

Place where we store a value and give it a name.

## 🔆 Basic Syntax

> 👉 Naming convention is important to store real time values.

```js
let someName = value;

let ageOfStudent = 25;

ageOfStudent + 1;
ageOfStudent = ageOfStudent + 1;
```

## 🔆 Unary Operators

```js
ageOfStudent++;
ageOfStudent--;
ageOfStudent += 1;
ageOfStudent -= 1;
ageOfStudent *= 1
```

## 🔆 const (Form of defining variables).

> 👉 const works just like let except you CANNOT change the value.

```js
const numberOfStudents = 4;
numberOfStudents = 20; //⛔ Error
numberOfStudents = numberOfStudents + 1; //⛔ Error

const pi = 3.14159; //✅
const daysInWeek = 7; //✅
const minHeightOfRide = 60; //✅
```

## 🔆 var (Old way of defining variables).

> 👉 var works just like let except you can access the value from anywhere in the file.😬

```js
var subjectGrade = 'A';
subjectGrade = 'B';
```

## 🔆String Template Literals(Back Tick)
⚡️ Template Literals are strings that are allow embedded expressions, which will be evaluated and then turned into a resulting string.

```js
`I counted ${3 + 4} sheep`; //I counted 7 sheep
let name = 'Gopibabu';
let welcomeMsg = `Welcome ${name}`; //Welcome Gopibabu
```

