# 😃New Javascript Features

## ⚡Default Params

```js
function multiply(a, b = 1) {
  return a * b;
}
multiply(4); //4
multiply(4, 5); //20
```

```js
const greet = (name, wish = "How are you?") => {
  console.log(`Hi, ${name}. ${wish}`);
};

greet("gopi");//Hi, gopi. How are you?
greet("ammu", "good morning!!");//'Hi, ammu. good morning!!'
```

?> **NOTE**: Default parameters should come at end of the list of parameters.

## ⚡Spread Operator

Spread syntax allows an iterable such as an array to be expanded in places where zero or more arguments or elements(array literals) are expected, or an object expression to be expanded in places where zero or more key-value pairs are expected.

### ✳spread for function calls

> Expands an iterable(array, string, etc.,) into list of arguments.

```js
const nums = [9, 3, 2, 8];

Math.max(nums); //NaN

Math.max(...nums); 
//...nums = 9, 3, 2, 8

Math.min(...nums); //2
```

```js
function giveMeFour(a, b, c, d) {
  console.log("a", a);
  console.log("b", b);
  console.log("c", c);
  console.log("d", d);
}

giveMeFour(1, 2, 3, 4);

let values = [1, 2, 3, 4];
giveMeFour(values); //undefined in all values except "a"
giveMeFour(...values); //print's all values

let str = "GOAT";
giveMeFour(...str); //prints all values
```

### ✳spread in Array Literals

> Creates a new array using an existing array. Spreads the elements from one array into a new array.

> Order matters while using arrays spread inside arrays

```js
const animals = ["goat", "hen", "duck", "cow"];

const vegetables = ["cucumber", "tomato", "onion", "brinjal"];

const nonveg = [...animals, ...vegetables];
nonveg;//['goat','hen','duck','cow','cucumber','tomato','onion','brinjal']
```

> We can use **spread** operator as alternative to **split** function

```js
const star = "Austronomy";

const arrValue = [...star];

arrValue;//[ 'A', 'u', 's', 't', 'r', 'o', 'n', 'o', 'm', 'y' ]
```

> We can copy arrays using spread operator

```js
const animals = ["goat", "hen", "duck", "cow"];

const copyAnimals = [...animals];
copyAnimals;//[ 'goat', 'hen', 'duck', 'cow' ]
```

### ✳spread in Object Literals

> Copies properties from one object into another object literal.

```js
const nbk = {
  name: "balakrishna",
  profession: "actor",
  family: "nandamuri"
};

const simhaCast = {
  ...nbk,
  film: "Simha",
  director: "Boyapati"
};

simhaCast;
/*
{
  name: 'balakrishna',
  profession: 'actor',
  family: 'nandamuri',
  film: 'Simha',
  director: 'Boyapati'
}
*/
```

> If spread operator and object having same key-value pair, then one will come later will override first one.

```js
const nbk = {
  actor: "balakrishna",
  profession: "actor",
  family: "nandamuri"
};

const simhaCast = {
  ...nbk,
  film: "Simha",
  director: "Boyapati",
  actor: "bala"
};

simhaCast;
/*
{
  actor: 'bala',
  profession: 'actor',
  family: 'nandamuri',
  film: 'Simha',
  director: 'Boyapati'
}
*/
```

> We can copy objects with spread operator

```js
const nbk = {
  actor: "balakrishna",
  profession: "actor",
  family: "nandamuri"
};

const bala = {
  ...nbk
};

bala;//{ actor: 'balakrishna', profession: 'actor', family: 'nandamuri' }
```

!> We can spread objects only inside objects, we can't spread objects inside arrays or functions. Viceversa can be true, where you can spread strings and arrays oinside objects. 

## ⚡Rest Operator

?> **rest** looks like **spread**, but it's not. It will group things. 

### ✳Without Rest Operator

> Javascript will create a array like object called Argument object to access data passed to a function. We can't apply any array functions on argument object.

```js
function sum() {
  console.log(arguments);
}

sum(1, 6, 23, 78);//[Arguments] { '0': 1, '1': 6, '2': 23, '3': 78 }

function sum(first, second) {
  console.log(arguments);
}

sum(1, 6, 23, 78);//[Arguments] { '0': 1, '1': 6, '2': 23, '3': 78 }
```

!> We can't access values in arguments object using arrow functions.

```js
const sum = () => {
  console.log(arguments);
};

sum(1, 6, 23, 78);//[Arguments] {}
```

### ✳With Rest Operator

> Collects all remaining arguments into actual array

```js
function sum(...nums) {
  return nums.reduce((total, currVal) => {
    return total + currVal;
  });
}

sum(1, 56, 78, 102);//237
```

> We use **reduce** operator to group unclaimed parameters
> **reduce** parameter should be ladt formal parameter

```js
function fullName(first, second, ...titles) {
  console.log("first", first);
  console.log("second", second);
  console.log("titles", titles);
}

fullName("john", "marty", "Sr.Engineer", "front end developer", "manager");

/*
'first' 'john'
'second' 'marty'
'titles' [ 'Sr.Engineer', 'front end developer', 'manager' ]
*/
```

> works well in arrow functions

```js
const fullName = (first, second, ...titles) => {
  console.log("first", first);
  console.log("second", second);
  console.log("titles", titles);
};

fullName("john", "marty", "Sr.Engineer", "front end developer", "manager");
/*
'first' 'john'
'second' 'marty'
'titles' [ 'Sr.Engineer', 'front end developer', 'manager' ]
*/
```

## ⚡Destructuring

?>A short, clean syntax to 'unpack'
**Values from arrays**,
**Properties from objects**
into distinct variables.

### ✳Destructuring Arrays

```js
const names = ["gopi", "vamsi", "mohan", "ammu", "dattu"];

const [name1, name2, name3] = names;

console.log(name1); //gopi
console.log(name2); //vamsi
console.log(name3); //mohan

const [, , , name4, name5] = names;
console.log(name4); //ammu
console.log(name5); //dattu

const [name, ...others] = names;
console.log(name); //gopi
console.log(others);//[ 'vamsi', 'mohan', 'ammu', 'dattu' ]
```

### ✳Destructuring Objects

> Here variables names should be keys in a given object. So you shoul define variable which is a key in a object.

```js
const winner = {
  firstName: "gopibabu",
  lastName: "Srungavarapu",
  age: 27,
  university: "DSU"
};

const { firstName, lastName, age, college } = winner;

console.log(firstName);//gopibabu
console.log(lastName);//srungavarapu
console.log(age);//27
console.log(college);//undefined
```

> We can create new variables from existing keys of an object

```js
const winner = {
  firstName: "gopibabu",
  lastName: "Srungavarapu",
  age: 27,
  university: "DSU"
};

const {
  firstName: first,
  lastName: last,
  age: older,
  university: collegee
} = winner;

console.log(first); //gopibabu
console.log(last); //srungavarapu
console.log(older); //27
console.log(collegee); //DSU
```

```js
const winner = {
  firstName: "gopibabu",
  lastName: "Srungavarapu",
  age: 27,
  university: "DSU"
};

const { firstName, lastName, ...others } = winner;

console.log(firstName); //gopibabu
console.log(lastName); //srungavarapu
console.log(others); //{ age: 27, university: 'DSU' }
```

### ✳Nested Destructuring

```js
const movies = [
  {
    title: "Jalsa",
    authors: ["trivikram", "sai burra"],
    rating: 3.25
  },
  {
    title: "Simhadri",
    authors: ["Vijayendra prasad", "Rajamouli"],
    rating: 4.05
  },
  {
    title: "Simha",
    authors: ["Boyapati", "Koratala"],
    rating: 3.75
  },
  {
    title: "Mirchi",
    authors: ["Koratala", "Akula"],
    rating: 4.25
  }
];

const [{ title }, { authors }, { rating }, { title: movie }] = movies;

console.log(title);//Jalsa
console.log(authors);//[ 'Vijayendra prasad', 'Rajamouli' ]
console.log(rating);//3.75
console.log(movie);//Mirchi
```

### ✳Param Destructuring

```js
const fullName  = ({first, last}) => {
  return `${first} ${last}`;
}

const details = {
  first : 'gopi',
  last : 'babu'
}

fullName(details);
```

```js
const studentDetails = ([first, last]) => {
  return `${first} ${last}`;
};

const stDetails = ["gopibabu", "srungavarapu"];

studentDetails(stDetails);//'gopibabu srungavarapu'
```