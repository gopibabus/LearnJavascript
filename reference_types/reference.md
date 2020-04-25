# 🔥 Value Type vs Reference Type

<img src="./assets/images/reference.jpg" alt="value type vs reference type">

## 🕵🏼Value Type

A data type is a value type if it holds a data value within its own memory space. It means variables of these data types directly contain their values.

```js
let name = 'ammu';

let otherName = name;

name;//ammu

otherName;//ammu

otherName = 'gopi';

name;//ammu

otherName;//gopi
```

> 🧶Example: Every Primitive type in Javascript.

## 🕵🏼Reference Type

Unlike value types, a reference type doesn't store its value directly. Instead, it stores the address where the value is being stored. In other words, a reference type contains a pointer to another memory location that holds the data.

```js
let nums = [1000, 206, 4, 8900, 2];

let otherNums = nums;

nums;//[1000, 206, 4, 8900, 2]

otherNums;//[1000, 206, 4, 8900, 2]

nums.push(895);

nums;//[1000, 206, 4, 8900, 2, 895]

otherNums;//[1000, 206, 4, 8900, 2, 895]
```

> 🧶Example: Arrays and Objects in Javascript.

## 🤷🏼‍♂️const with arrays

 You can’t re-assign the value of the variable again.

 ```js
 const name = 'hari';

 name = 'gopi'; //❌Error
 ```

!> Beware when you’re dealing with arrays and objects while using const keyword

when you’re declaring a new **array** using const keyword, you can change the value of any element in the array but, you can’t change the value of the entire array as it is because **const** points to variable reference.

For **objects** you can change the value of any property in the object but, you can’t change the value of the whole object and also you can add more keys in object.

```js
const grades = ['A', 'B', 'C', 'D'];

grades = ['X', 'Y', 'Z'];//❌Error

grades.push('E'); //✅Works fine

grades.pop();//✅Works fine
```