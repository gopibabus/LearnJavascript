# 🔥Arrays

Arrays are ordered collection of values.

## 🧙‍♂️Examples: 

* List of comments on IG post.

* Collection of levels in a game.

* Songs in a playlist.

## 💪Syntax of an Array

### How to make an empty array?

```js
let students = [];
```

### How to make an array of strings?

```js
let colors = ['red', 'orange', 'yellow'];
```

### How to make an array of numbers?

```js
let lottoNums = [19, 22, 56, 58, 87];
```

### How to make a mixed array?

```js
let stuff = [true, 67, 'cat', null];
```

### What is the legacy way of making an Array?

!> This is no longer necessary.(creating an array using objects).

```js
let marks = new Array(56, 76, 87, 45);
```

### How to access values in an Array?

```js
let colors = ['red', 'orange', 'yellow', 'green'];

colors.length //4

colors[0] //red
colors[1] //orange
colors[2] //yellow
colors[3] //green
colors[5] //undefined
```

### How to modify an Array?

> Unlike Strings, Arrays are Mutable. We can changes values inside an array.

```js
let colors = ['red', 'orange', 'yellow', 'green'];

colors[0] = 'blue';
colors[1] = 'violet';
colors[2] = 'purple';
colors[3] = 'brown';
color[colors.length] = 'pink';
```

## 💪 Nested Arrays

> We can nest array inside other array.

```js
var numberBoard = [
  [34, 67, 89],
  [23, 67, 90],
  [
    256, 
    72, 
    [18, 92, 28]
  ]
];

numberBoard[0];//[ 34, 67, 89 ]

numberBoard[1][2];//90

numberBoard[2][2][1];//92
```

!> There is no **associative arrays** concept in Javascript. Though we can achieve the functionality of associative arrays using Objects.