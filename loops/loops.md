# 🔥Loops

> Loops are used to execute certain set of commands for **n** number of times.

## 💫FOR Loop

```js
for (let i = 1; i <= 10; i++) {
  console.log("Hello", i);
}

for (let i = 200; i >= 0; i -= 25) {
  console.log("Hello", i);
}
```

### ⚡️FOR Loop with Arrays

```js
 const examScores = [98, 76, 89, 83, 99];

for (let i = 0; i < examScores.length; i++) {
  console.log(`Exam Score of subject ${i + 1} is ${examScores[i]}`);
}

const Students = [
  {
    firstName: "Gopi",
    grade: 86
  },
  {
    firstName: "Ammu",
    grade: 99
  },
  {
    firstName: "dattu",
    grade: 78
  },
  {
    firstName: "Mohan",
    grade: 88
  }
];

for (let i = 0; i < Students.length; i++) {
  console.log(`Exam Score of ${Students[i].firstName} is ${Students[i].grade}`);
}

const word = "NewtorkCity";
for (let i = 0; i < word.length; i++) {
  console.log(`Character ${i} in a given word: ${word[i]}`);
}

```

### ⚡️Nested FOR Loops

```js
 const gameBoard = [
     [4, 32, 8, 4], 
     [64, 8, 32, 2], 
     [8, 32, 16, 4], 
     [8, 8, 4, 2]
     ];

let totalScore = 0;

for (let i = 0; i < gameBoard.length; i++) {
  let row = gameBoard[i];

  for (let j = 0; j < row.length; j++) {
    totalScore += row[j];
  }
}
console.log(totalScore);
```

## 💫INFINITE Loops

> Infinite loop occurs when ending condition never met. This type of loops never ends.

```js
for (let i = 1; i >= 0; i++) {
  console.log("Hello", i);
}
```

!> This type of **infinite** loops make browser unhappy 😡

## 💫WHILE Loop

```js
const target = Math.floor(Math.random() * 10);
let guess = Math.floor(Math.random() * 10);

while (guess !== target) {
  console.log(`Target: ${target} Guess:${guess}`);
  guess = Math.floor(Math.random() * 10);
}

console.log(`Target: ${target} Guess:${guess}`);
console.log("Congrates you Won!!");
```

## 💥Break Keyword

> Used to break a loop

```js
const target = Math.floor(Math.random() * 10);
let guess = Math.floor(Math.random() * 10);

while (true) {
  if (target === guess) {
    break;
  }
  console.log(`Target: ${target} Guess:${guess}`);
  guess = Math.floor(Math.random() * 10);
}

console.log(`Target: ${target} Guess:${guess}`);
console.log("Congrates you Won!!");


let values = [3, 9, 7, 27, 33, 55, 24, 67];
for (let i = 0; i < values.length; i++) {
  if (values[i] % 2 === 0) {
    console.log("Encountered Even number");
    break;
  }
  console.log(`${values[i]} is not a even number`);
}

```

## 💫FOR OF Loop

?> Used to iterate iterables(array, strings, objects)

```js
let tags = ["php", "js", "html", "css", "java", "c#"];

for (let tag of tags) {
  console.log(tag);
}

let string = "scientific";

for (let char of string) {
  console.log(char);
}

let countryInfo = {
  name: "India",
  population: 1400000000,
  anthem: "Janaganamana",
  flag: "tri color"
};

for (let item of Object.keys(countryInfo)) {
  console.log(`Country ${item} : ${countryInfo[item]}`);
}
```

?> Here we are using **Object.keys()** & **Objects.values()** methods to make **Object** Iterable.

## 💫FOR IN Loop

> Loop over keys in a Object and Arrays. This is designed to iterate Objects.

```js
let countryInfo = {
  name: "India",
  population: 1400000000,
  anthem: "Janaganamana",
  flag: "tri color"
};

for (let item in countryInfo) {
  console.log(`Country ${item} : ${countryInfo[item]}`);
}

let countryInfo = ["India", 1400000000, "Janaganamana", "tri color"];

for (let item in countryInfo) {
  console.log(`${item} : ${countryInfo[item]}`);
}
```

!> Better don't use **for..in** with Arrays.