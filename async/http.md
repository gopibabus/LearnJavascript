# 🔥Making HTTP Requests

## ⚡AJAX

- AJAX stands for **Asynchronous JavaScript And XML**.
- AJAX’s most appealing characteristic is its **“asynchronous”** nature, which means it can **communicate with the server**, **exchange data**, and **update the page** without having to refresh the page.

- The two major features of AJAX allow you to do the following:
  - Make requests to the server without reloading the page
  - Receive and work with data from the server

## ⚡XML & JSON

### ✳XML

- XML is a software- and hardware-independent tool for storing and transporting data.
- XML stands for **eXtensible Markup Language**. It is a markup language much like HTML. The XML language has no predefined tags like HTML.
- XML was designed to store and transport data and XML is Extensible.
- XML is just information wrapped in tags.

```xml
<note>
  <date>2015-09-01</date>
  <hour>08:30</hour>
  <to>Tove</to>
  <from>Jani</from>
  <body>Don't forget me this weekend!</body>
</note>
```

> [🌐 Check Valid XML](https://onlinexmltools.com/validate-xml)

### ✳JSON

- JSON stands for **JavaScript Object Notation**.
- JSON is a lightweight format for storing and transporting data.
- JSON is often used when data is sent from a server to a web page.
- JSON is "self-describing" and easy to understand.
- The JSON format is syntactically identical to the code for creating JavaScript objects.
- Because of this similarity, a JavaScript program can easily convert JSON data into native JavaScript objects.
- JSON data is written as name/value pairs, just like JavaScript object properties.
- JSON names require **double quotes**. JavaScript names do not.

!> The JSON syntax is derived from **JavaScript object notation syntax**, but the JSON format is text only. Code for reading and generating JSON data can be written in **any programming language**.

```json
{
	"employees": [
		{ "firstName": "John", "lastName": "Doe" },
		{ "firstName": "Anna", "lastName": "Smith" },
		{ "firstName": "Peter", "lastName": "Jones" }
	]
}
```

> [🌐 Check Valid JSON](https://jsonformatter.curiousconcept.com/)

## ⚡XMLHttpRequest(XHR)

> This is the old school way of making HTTP requests. You can find some good documentation on [🌐 MDN](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/Using_XMLHttpRequest)

!> Does not support Promises, so lot of callbacks😑

### ✳Simple XHR

```js
const firstReq = new XMLHttpRequest();
firstReq.addEventListener('load', function () {
	console.log('It worked');
	const data = JSON.parse(this.responseText);
	for (let planet of data.results) {
		console.log(planet.name);
	}
});
firstReq.addEventListener('error', function () {
	console.log('It Failed');
});
firstReq.open('GET', 'https://swapi.dev/api/planets/');
firstReq.send();
console.log('Request Send');
```

### ✳Chaining Requests with XHR

```js
const firstReq = new XMLHttpRequest();
firstReq.addEventListener('load', function () {
	console.log('It worked');
	const data = JSON.parse(this.responseText);
	const filmURl = data.results[0].films[0];
	const filmReq = new XMLHttpRequest();
	filmReq.addEventListener('load', function () {
		console.log('Second Req worked');
		const filmData = JSON.parse(this.responseText);
		console.log(filmData);
	});
	filmReq.addEventListener('error', function () {
		console.log('Second Req Failed');
	});
	filmReq.open('GET', filmURl);
	filmReq.send();
	console.log('Second Request Send');
});
firstReq.addEventListener('error', function () {
	console.log('It Failed');
});
firstReq.open('GET', 'https://swapi.dev/api/planets/');
firstReq.send();
console.log('Request Send');
```

## ⚡Fetch API

- **XMLHttpRequest** involved some really messy code, it didn't give us ability to work with promises, so we used **jQuery.ajax()**.
- Javascript address this issue by introducing **Fetch API** a new standard to make server request jam-packed with **promises**.
- In a very simple manner all you really do is call fetch with the URL you want.
- By default the Fetch API uses the **GET** method.

!> Not supported in **Internet Explorer** 🤔

?> [🌐 Nice Article on Fetch API](https://scotch.io/tutorials/how-to-use-the-javascript-fetch-api-to-get-data)

### ✳Simple Fetch

```js
fetch('https://swapi.dev/api/planets/')
	.then((response) => {
		if (!response.ok) {
			throw new Error(`Status Code ErrorL ${response.status}`);
		}
		response.json().then((data) => {
			for (let planet of data.results) {
				console.log(planet.name);
			}
		});
	})
	.catch((err) => {
		console.log(err);
	});
```

### ✳Chaining Requests with Fetch

<!-- tabs:start -->

#### ** BEFORE REFACTOR **

```js
fetch('https://swapi.dev/api/planets/')
	.then((response) => {
		if (!response.ok) {
			throw new Error(`Status Code ErrorL ${response.status}`);
		}
		return response.json();
	})
	.then((data) => {
		const filmURL = data.results[0].films[0];
		return fetch(filmURL);
	})
	.then((response) => {
		if (!response.ok) {
			throw new Error(`Status Code ErrorL ${response.status}`);
		}
		return response.json();
	})
	.then((data) => {
		console.log(data.title);
	})
	.catch((err) => {
		console.log(err);
	});
```

#### ** AFTER REFACTOR **

```js
const checkStatusAndParse = (response) => {
	if (!response.ok) throw new Error(`Status Code Error: ${response.status}`);

	return response.json();
};

const printPlanets = (data) => {
	console.log('Loaded 10 more planets...');
	for (let planet of data.results) {
		console.log(planet.name);
	}
	return Promise.resolve(data.next);
};

const fetchNextPlanets = (url = 'https://swapi.co/api/planets/') => {
	return fetch(url);
};

fetchNextPlanets()
	.then(checkStatusAndParse)
	.then(printPlanets)
	.then(fetchNextPlanets)
	.then(checkStatusAndParse)
	.then(printPlanets)
	.then(fetchNextPlanets)
	.then(checkStatusAndParse)
	.then(printPlanets)
	.catch((err) => {
		console.log('SOMETHING WENT WRONG WITH FETCH!');
		console.log(err);
	});
```

<!-- tabs:end -->

## ⚡Axios

- [**Axios**](https://www.npmjs.com/package/axios) is a very popular **JavaScript library** you can use to perform HTTP requests, that works in both **Browser** and **Node.js** platforms.

- Using Axios has quite a few **advantages** over the native Fetch API:
  - supports older browsers (Fetch needs a polyfill)
  - has a way to abort a request
  - has a way to set a response timeout
  - has built-in CSRF protection
  - supports upload progress
  - performs automatic JSON data transformation
  - works in Node.js

> 💡 We should install "axios" library using npm or yarn

### ✳Simple Axios Request

```js
const axios = require('axios').default;

axios
	.get('https://swapi.dev/api/planets/')
	.then((res) => {
		console.log(res.data);
	})
	.catch((err) => {
		console.log(err);
	});
```

### ✳Chaining Requests with Axios

<!-- tabs:start -->

#### **BEFORE REFACTOR**

```js
const axios = require('axios').default;

axios
	.get('https://swapi.dev/api/planets/')
	.then(({ data }) => {
		for (let planet of data.results) {
			console.log(planet.name);
		}
		return axios.get(data.next);
	})
	.then(({ data }) => {
		for (let planet of data.results) {
			console.log(planet.name);
		}
	})
	.catch((err) => {
		console.log(err);
	});
```

#### **AFTER REFACTOR**

```js
const axios = require('axios').default;

const fetchNextPlanets = (url = 'https://swapi.co/api/planets/') => {
	console.log(url);
	return axios.get(url);
};
const printPlanets = ({ data }) => {
	console.log(data);
	for (let planet of data.results) {
		console.log(planet.name);
	}
	return Promise.resolve(data.next);
};

fetchNextPlanets()
	.then(printPlanets)
	.then(fetchNextPlanets)
	.then(printPlanets)
	.then(fetchNextPlanets)
	.then(printPlanets)
	.catch((err) => {
		console.log('ERROR!!', err);
	});
```

<!-- tabs:end -->
