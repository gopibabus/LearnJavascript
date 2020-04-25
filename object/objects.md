# 🔥Objects

Objects are collections of properties.

Properties are key value pairs.

Rather than accessing data using an index, we use custom keys.

```js
const fitBitData = {
  totalSteps        : 308569,
  totalMiles        : 211.7,
  avgCalorieBurn    : 5755,
  workoutsThisWeek  : '5 of 7',
  avgGoogSleep      : '2:13',
  123               : 'totalDays'
};

fitBitData.totalSteps; //308569
fitBitData.123; //Error
```

!> We can't access keys with numerics using **.** notation. We have alternative syntax to access keys with numbers. That is array index notation.

```js
fitBitData['totalSteps']; //308569
fitBitData[123]; //totalDays
fitBitData['123']; //totalDays
```

?> ☝️ Number 123 is converted into string before accessing an array. We can use this array index notation on all keys which are valid and not valid javascript identifiers.

> So it is better to use array index notation over object **.** notation. Because we have constraints with object **.** notation.

### How to add values to Objects?

```js
const userReviews = {};

userReviews["gopi"] = 4.0;

userReviews.hari = 5.0;

userReviews["hari"] += 2;

userReviews;//{ gopi: 4, hari: 7 }
```

## 👣Arrays & Objects

### 🧤Arrays inside Objects

```js
const student = {
  firstName: "David",
  lastName: "Jones",
  strengths: ["Music", "Art"],
  exams: {
    midTerm: 92,
    final: 88
  }
};

const avg = (student.exams.midTerm + student.exams.final) / 2;

avg;//90
```

### 🧤Objects inside an Array

```js
const shoppingCart = [
  {
    product: "iPhone",
    price: 499,
    quantity: 1
  },
  {
    product: "Samsung Mobile",
    price: 300,
    quantity: 10
  },
  {
    product: "Nokia Mobile",
    price: 200,
    quantity: 20
  }
];

shoppingCart[1]["price"];//300
```

?> We can mix and match **arrays and objects** as per our requirement.

## 🌈Objects are Reference Type

> Like arrays, Objects are reference type.

```js
const studentInfo = {
  name: "Gopi",
  id: "10491A0595",
  college: "QIS"
};

const studentDetails = studentInfo;

studentDetails.grade = "A";

studentInfo.grade;//A
```

## ⚡️Equality

```js
let name = [1, 2, 4, 6];

let otherName = name; //☃️Reference number is copied

let college = [1, 2, 4, 6];

name === college;//false

name === otherName; //true

let grades = {
  maths : 'A',
  social : 'B',
  drawing : 'C'
};

let gradesCopy = {
  maths : 'A',
  social : 'B',
  drawing : 'C'
};

grades === gradesCopy; //False
```

!> **name** and **college** are carrying same set of values but they are not equal. Because **name** and **college** are not actually carrying array of values, instead they are carrying reference number of those arrays.

!> For Example:<br>
Reference Number of name may be 2562358965<br>
Reference number of college may be 85698569325<br>

?> If we have to compare arrays or Objects, we should write our custom logic to compare arrays or objects using custom functions.
