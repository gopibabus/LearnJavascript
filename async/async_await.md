# 🔥async/await

- **async/await** newest way to write asynchronous code in JavaScript. It is really **syntactic sugar** on top of those promises.
- It is non blocking (just like promises and callbacks).
- async/await was created to simplify the process of working with and writing chained promises.

## ⚡async

- **async** functions always return a **Promise**😃.
- If the function returns a value, the Promise will be resolved with that value.
- If the function throws an error, the Promise will be rejected.

<!-- tabs:start -->

#### **Simple Function**

```js
function greet() {
	return 'Hello!!!';
}

greet(); //Hello!!!
```

#### **async Function**

```js
async function greet(input) {
	if (typeof input !== 'string') {
		throw 'input is not a string';
	}
	return `Happy ${input}`;
}

greet('birthday')
	.then((val) => {
		console.log(val);
	})
	.catch((err) => {
		console.log(err);
	});

greet(123)
	.then((val) => {
		console.log(val);
	})
	.catch((err) => {
		console.log(err);
	});
```

<!-- tabs:end -->

## ⚡await

- **await** function is used to wait for the promise.
- It makes the code wait until the promise returns a result. It only makes the **async** block wait.
- We can only use the **await** keyword inside of function declared with **async**.
- So async and await go hand in hand👏

<!-- tabs:start -->

#### **Without await**

```js
const axios = require('axios').default;

function getPlanets() {
	return axios.get('http://swapi.dev/api/planets/');
}

getPlanets().then((res) => {
	console.log(res.data); //Data
});
```

#### **Using await**

```js
const axios = require('axios').default;

async function getPlanets() {
	const res = await axios.get('http://swapi.dev/api/planets/');
	console.log(res.data);
}

getPlanets();
```

#### **Error Handling using "catch"**

```js
const axios = require('axios').default;

async function getPlanets() {
	const res = await axios.get('http://swapi.dev/api/planets/');
	console.log(res.data);
}

getPlanets().catch((err) => {
	console.log(err);
});
```

#### **Error Handling using "try catch"**

```js
const axios = require('axios').default;

async function getPlanets() {
	try {
		const res = await axios.get('http://swapi.dev/api/planets/');
		console.log(res.data);
	} catch (err) {
		console.log(err);
	}
}

getPlanets();
```

<!-- tabs:end -->

### ✳Multiple awaits

```js
const moveX = (element, amount, delay) => {
	return new Promise((resolve, reject) => {
		setTimeout(() => {
			const bodyBoundary = document.body.clientWidth;
			const elRight = element.getBoundingClientRect().right;
			const currLeft = element.getBoundingClientRect().left;
			if (elRight + amount > bodyBoundary) {
				reject({ bodyBoundary, elRight, amount });
			} else {
				element.style.transform = `translateX(${currLeft + amount}px)`;
				resolve();
			}
		}, delay);
	});
};

const btn = document.querySelector('button');
async function animateRight(el, amt) {
	await moveX(el, amt, 1000);
	await moveX(el, amt, 1000);
	await moveX(el, amt, 1000);
	await moveX(el, amt, 1000);
	await moveX(el, amt, 1000);
	await moveX(el, amt, 1000);
	await moveX(el, amt, 1000);
	await moveX(el, amt, 1000);
	await moveX(el, amt, 1000);
	await moveX(el, amt, 1000);
}
animateRight(btn, 100).catch((err) => {
	console.log('Hit the right edge! Now Moving left!');
	animateRight(btn, -100);
});
```

> [Nice article on async/await](https://dev.to/lydiahallie/javascript-visualized-promises-async-await-5gke)

## ⚡Parallel Vs Sequential Requests

### ✳Sequential Requests

```js
const axios = require('axios').default;

async function getPokemon() {
	const poke1 = await axios.get('https://pokeapi.co/api/v2/pokemon/1/');
	const poke2 = await axios.get('https://pokeapi.co/api/v2/pokemon/2/');
	const poke3 = await axios.get('https://pokeapi.co/api/v2/pokemon/3/');
	console.log(poke1.data);
	console.log(poke2.data);
	console.log(poke3.data);
}

getPokemon();
```

### ✳Parallel Requests

```js
const axios = require('axios').default;

async function getPokemon() {
	const poke1 = axios.get('https://pokeapi.co/api/v2/pokemon/1/');
	const poke2 = axios.get('https://pokeapi.co/api/v2/pokemon/2/');
	const poke3 = axios.get('https://pokeapi.co/api/v2/pokemon/3/');
	const prom1 = await poke1;
	const prom2 = await poke2;
	const prom3 = await poke3;
	console.log(prom1.data);
	console.log(prom2.data);
	console.log(prom3.data);
}

getPokemon();
```

## ⚡Promise.all

```js
const axios = require('axios').default;

async function getPokemon() {
	const poke1 = axios.get('https://pokeapi.co/api/v2/pokemon/1/');
	const poke2 = axios.get('https://pokeapi.co/api/v2/pokemon/2/');
	const poke3 = axios.get('https://pokeapi.co/api/v2/pokemon/3/');
	const results = await Promise.all([poke1, poke2, poke3]);
	console.log(results);
}

getPokemon();
```
