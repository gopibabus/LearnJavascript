# 🔥Array Methods

### push()

> Add an item to end of an array

```js
let topSongs = [
    'Andamaina Prema Rani Cheyi Thagilithe',
    'Anaganaganaga Aravindaga thana peeru',
    'Rum rudiram, rum samaram',
    'Aradugula bullet, dairyam visirina rocket'
];

topSongs.push('I wanna follow follow follow you'); //5
```

?> This **array.push()** method returns new length of an array.
?> We can add multiple items using **push()**

### pop()

> Remove an item from end of an array

```js
let topSongs = [
    'Andamaina Prema Rani Cheyi Thagilithe',
    'Anaganaganaga Aravindaga thana peeru',
    'Rum rudiram, rum samaram',
    'Aradugula bullet, dairyam visirina rocket'
];

topSongs.pop(); //Aradugula bullet, dairyam visirina rocket
```

?> This **array.pop()** method returns the item that is removed from an array.

### unshift()

> Add an item to start of an array

```js
let topSongs = [
    'Andamaina Prema Rani Cheyi Thagilithe',
    'Anaganaganaga Aravindaga thana peeru',
    'Rum rudiram, rum samaram',
    'Aradugula bullet, dairyam visirina rocket'
];

topSongs.unshift('I wanna follow follow follow you'); //5
```

?> This **array.unshift()** method returns new length of an array.
?> We can add multiple items using **unshift()**

### shift()

> Remove an item from start of an array

```js
let topSongs = [
    'Andamaina Prema Rani Cheyi Thagilithe',
    'Anaganaganaga Aravindaga thana peeru',
    'Rum rudiram, rum samaram',
    'Aradugula bullet, dairyam visirina rocket'
];

topSongs.shift(); //Andamaina Prema Rani Cheyi Thagilithe
```

?> This **array.shift()** method returns the item that is removed from an array.

### concat()

> Helps to merge arrays

```js
let fruits = ['apple', 'orange'];

let veggies = ['cucumber', 'tomato'];

let berries = ['strawberry', 'blueberry']

fruits.concat(veggies, berries);
//['apple', 'orange', 'cucumber', 'tomato', 'strawberry', 'blueberry']
```

?> This **array.concat()** method returns the resulting array after merging multiple arrays. 

### includes()

> Searches for an item in an array

```js
let food = ['apple', 'orange', 'pear', 'cucumber', 'tomato', 'ladies finger'];

food.includes('tomato'); //true

if (food.includes('flour')) {
	console.log('I am gluten free, I cannot eat that!!');
}
```

?> This **array.includes()** method returns true if searching item is present in an array else return false.

### indexOf()

> Searches for index of an item in an array

```js
let food = ['apple', 'orange', 'pear', 'cucumber', 'tomato', 'ladies finger'];

food.indexOf('tomato'); //4

if (food.indexOf('flour') !== -1) {
	console.log('I am gluten free, I cannot eat that!!');
}
```

?> This **array.indexOf()** method returns **index** of an item if searching item is present in an array else return **-1**.

## reverse()

> This will reverse the given array and this will mutate the original array

```js
let grades = ['A', 'B', 'C', 'D'];

grades.reverse(); //['D', 'C', 'B', 'A']
```

?> This **array.reverse()** method returns the array which is reversed.

## join()

> Joins all items in an array into a string with a seperator(,)

```js
let grades = ['A', 'B', 'C', 'D'];

grades.join(); //"A,B,C,D"

grades.join('.'); //"A.B.C.D"

grades.join('&'); //"A&BC&D"
```

?> This **array.join()** method returns the string.

## slice(x,y)

> Extracts a section of a array and returns it as a new array, without modifying the original string. x is included & y is excluded from result.<br>

?> slice will help us to copy one array into other array

```js
let animals = ['dog', 'cat', 'rat', 'tiger', 'lion'];

animals.slice(0, 3); //[ 'dog', 'cat', 'rat' ]
animals.slice(3); //[ 'tiger', 'lion' ]
animals.slice(); // ['dog', 'cat', 'rat', 'tiger', 'lion']
animals.slice(-1);// ['lion']
animals.slice(-3, -1); //['rat', 'tiger']

let animals2 = animals.slice();//['dog', 'cat', 'rat', 'tiger', 'lion']
```

?>This **array.slice()** method returns the string.

## splice(x,y,z)

>Used to replace items in an array

> x: starting element in an array<br>
> y: number of items to be removed<br>
> z: items to be inserted after 'x'<br>

```js
let animals = ['dog', 'cat', 'rat', 'tiger', 'lion'];

animals.splice(1,1, 'monkey');// [ 'cat' ]

animals; //['dog', 'monkey', 'rat', 'tiger', 'lion'];
```

?>This **array.splice()** method returns an array with item that is removed from an array.

## sort()

> This will sort items in an array based on string character codes. That's why this method will sort string properly but not  numbers. This will mutate an array.

> we can sort numbers using this function by passing anonymous fucntion and writing custom logic into it.

```php
let animals = ['dog', 'cat', 'rat', 'tiger', 'lion'];

animals.sort(); //[ 'cat', 'dog', 'lion', 'rat', 'tiger' ]

let nums = [1000, 206, 4, 8900, 2];

nums.sort();//[ 1000, 2, 206, 4, 8900 ]

var numbers = [4, 2, 5, 1, 3];

numbers.sort(function(a, b) {
  return a - b;
});// [1, 2, 3, 4, 5]
```
?>This **array.sort()** method returns an sorted array.
