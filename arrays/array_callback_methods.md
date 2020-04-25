# 🔥Array Callback Methods

> Arrays come with many built in methods that accept callback functions.

### forEach()

> Accepts a callback function and calls that function once per element in the array.

> Optionally we can pass second argument, which will return index of given element in an array.

```js
const nums = [9, 8, 7, 6, 5, 4, 3, 2, 1];

nums.forEach(function(n) {
  console.log(n);
});

nums.forEach(function(n) {
  if (n % 2 === 0) {
    console.log(`${n} is a even number.`);
  }
});
```

```js
const movies = [
  {
    title: "Jalsa",
    authors: ["trivikram", "sai burra"],
    rating: 4.25
  },
  {
    title: "Simhadri",
    authors: ["Vijayendra prasad", "Rajamouli"],
    rating: 4.05
  },
  {
    title: "Simha",
    authors: ["Boyapati", "Koratala"],
    rating: 4.75
  },
  {
    title: "Mirchi",
    authors: ["Koratala", "Akula"],
    rating: 4.25
  }
];

movies.forEach(function(movie) {
  console.log(`${movie.title} : ${movie.rating}`);
});

movies.forEach(function(movie, index) {
  console.log(`${index} : ${movie.title} -> ${movie.rating}`);
});

```

### map()

> Creates a new array with the results of calling a callback on every element in the array.
> Original values in an array are unchanged.

```js
const languages = ["php", "javascript", "java", "swift", "go", "java"];
let result = languages.map(function(lang) {
  return lang.toUpperCase();
});
console.log(result);

const nums = [2, 5, 9, 6, 7, 11];
let doubles = nums.map(function(num) {
  return num * 2;
});
console.log(doubles);
```

```js
const nums = [2, 5, 9, 6, 7, 11];
let numDetails = nums.map(function(num) {
  return {
    value: num,
    isEven: num % 2 === 0
  };
});
console.log(numDetails);
```

```js
const words = ["asap", "byod", "rsvp", "diy"];

const abbrevs = words.map(function(word) {
  return word
    .toUpperCase()
    .split("")
    .join(".");
});

console.log(abbrevs);//[ 'A.S.A.P', 'B.Y.O.D', 'R.S.V.P', 'D.I.Y' ]
```

### find()

> Returns the value of the first element in the array that satisfies the provided testing function.

 ```js
 const movies = [
  "The Fantastic Mr. Fox",
  "Mr. and  Mrs. Smith",
  "Mrs. Doubtfire",
  "Mr. Deeds"
];

let movie = movies.find(movie => movie.includes("Mrs."));
let movie2 = movies.find(movie => movie.indexOf("Mrs.") === 0);
movie;//'Mr. and  Mrs. Smith'
movie2;//'Mrs. Doubtfire'
 ```

 ```js
 const movies = [
  {
    title: "Jalsa",
    authors: ["trivikram", "sai burra"],
    rating: 4.25
  },
  {
    title: "Simhadri",
    authors: ["Vijayendra prasad", "Rajamouli"],
    rating: 4.05
  },
  {
    title: "Simha",
    authors: ["Boyapati", "Koratala"],
    rating: 4.75
  },
  {
    title: "Mirchi",
    authors: ["Koratala", "Akula"],
    rating: 4.25
  }
];

let highRating = movies.find(movie => movie.rating > 4);

highRating;//{ title: 'Jalsa', authors: [ 'trivikram', 'sai burra' ], rating: 4.25 }
 ```

 ### filter()

 > Creates a new array with all elements that pass the test implemented by the provided function.

 ```js
 const nums = [9, 8, 7, 6, 5, 4, 3, 2, 1];

const odds = nums.filter(num => num % 2 === 1);

const smallNums = nums.filter(num => num < 5);

odds;//[ 9, 7, 5, 3, 1 ]
smallNums;//[ 4, 3, 2, 1 ]
 ```

 ```js
  const movies = [
  {
    title: "Jalsa",
    authors: ["trivikram", "sai burra"],
    rating: 4.25
  },
  {
    title: "Simhadri",
    authors: ["Vijayendra prasad", "Rajamouli"],
    rating: 4.05
  },
  {
    title: "Simha",
    authors: ["Boyapati", "Koratala"],
    rating: 4.75
  },
  {
    title: "Mirchi",
    authors: ["Koratala", "Akula"],
    rating: 4.25
  }
];

let highRating = movies.filter(movie => movie.rating > 4);

highRating;
 ```

### every()

> Tests whether all elements in the array pass condition in provided function. It returns a boolean value.

```js
const words = ["dog", "dig", "log", "bag", "wag"];

words.every(word => {
  return word.length === 3;
}); //true

words.every(word => {
  let lastLetter = word[word.length - 1];
  return lastLetter === "g";
}); //true
```

### some()

> Similar to every, but returns true if any of the array elements pass condition in test fucntion.

```js
const words = ["dog", "dig", "dlog", "bags", "waggings"];

words.some(word => {
  return word.length === 3;
}); //true

words.some(word => {
  let lastLetter = word[word.length - 1];
  return lastLetter === "g";
}); //true
```

### sort()

?> arr.sorrt(compareFunc(a, b));

> If compareFunc(a, b) returns less than 0 then sort **a** before **b**.

> If compareFunc(a, b) returns 0 then leave **a** and **b** unchanged with respect to each other.

> If compareFunc(a, b) returns greater than 0 then sort **b** before **a**.
```js
const prices = [400.5, 3000, 99.99, 35.99, 12.0, 9500];

let ascendOrder = prices.sort((a, b) => a - b);//[ 12, 35.99, 99.99, 400.5, 3000, 9500 ]

let descendOrder = prices.sort((a, b) => b - a);//[ 9500, 3000, 400.5, 99.99, 35.99, 12 ]
```

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

movies.sort((a, b) => {
  return a.rating - b.rating;
});

```

### reduce()

> Executes a reducer function on each element in the array, resulting in a single value.

```js
const scores = [3, 5, 7, 9, 11];

scores.reduce((accumulator, currentValue) => {
  return accumulator + currentValue;
});
```

<img src="./assets/images/reduce.png" alt="reduce" width="700" height="400"/>

```js
const scores = [3, 5, 7, 9, 11];

scores.reduce((total, currValue) => {
  return total * currValue;
});//10395
```

🥇Advanced syntax of **reduce** function

```js
scores.reduce((accumulator, currentValue) => {
  return accumulator + currentValue;
}, initialValue);
```

```js
const votes = [
  "y",
  "y",
  "n",
  "y",
  "n",
  "n",
  "y",
  "n",
  "n",
  "y",
  "y",
  "y",
  "n",
  "n",
  "y"
];

const results = votes.reduce((tally, val) => {
  if (tally[val]) {
    tally[val]++;
  } else {
    tally[val] = 1;
  }
  return tally;
}, {});

results;//{ y: 8, n: 7 }
```