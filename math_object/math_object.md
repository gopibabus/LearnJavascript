# ✨ Math Object ✨

> ⚡️ Contains properties and methods for mathematical constants and functions

```js
Math.PI;// 3.171592653586793
Math.round(4.9); //5
Math.abs(-456); //456
Math.pow(2, 5); //32
Math.floor(3.9999); //3
```

> 🎯 Math.random() gives us a random decimal between 0 and 1.

```js
Math.random(); //0.1450243
Math.random(); //0.2586598
```

> 🎯 Random number between 1 and 10.

```js
const step1 = Math.random(); //0.59625356
const step2 = step1 * 10; //5.96253
const step3 = Math.floor(step2); //5
Math.floor(Math.random() * 10); //5
```

## ✨ TYPE OF ✨

```js
typeof 'hello'; //'string'
typeof 2; //'number'
typeof true; //'boolean'
typeof undefined; //'undefined'
typeof null; //'object'😬
typeof NaN; //'number'
```

## ✨ parseInt & parseFloat ✨

> 👉 Use to parse strings into numbers.
> 😬 But watch out for NaN (If string doesn't start with number)

```js
parseInt('24'); //24
parseInt('24.987'); //24
parseInt('28days'); //28

parseFloat('24.987'); //24.987
parseFloat('7'); //7
parseFloat('i ate 3 fish'); //NaN
parseFloat('   99.34'); //99.34
```