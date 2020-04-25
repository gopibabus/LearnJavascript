# 🔥Events

<img src="./assets/images/events.jpg" alt="events" width="700" height="400"/>

## 🤹🏽‍♀️Two ways of adding Events

### ⛔ Wrong way

!> Not the best way to add events on HTML Elements.

```html
<div class="section">
	<button onclick="alert('This is button');">Click Me 1</button>
	<button onclick="activatePopup();">Click Me 2</button>
	<button onmouseover="activatePopup();">Click Me 3</button>
</div>
```

<!-- tabs:start -->

#### ** HTML **

```html
<div class="section">
	<button id="click_me_1">Click Me 1</button>
	<button id="click_me_2">Click Me 2</button>
	<button id="click_me_3">Click Me 3</button>
</div>
```

#### ** Javascript **

```js
let btn = document.querySelector('#click_me_1');

btn.onclick = alert('This is Click me 1');

btn.onclick = function () {
	console.log('You clicked me!!');
};
btn.ondblclick = function () {
	console.log('You clicked me twice!!');
};
```

#### ** Output **

```js
Updated DOM output
```

<!-- tabs:end -->

### 😃 Right way

?> We should use **addEventListener**. we should specify the event type and a callback to run.

> We can add same event on a element multiple times using **addEventListener**

<!-- tabs:start -->

#### ** HTML **

```html
<div class="section">
	<button id="click_me_1">Click Me 1</button>
	<button id="click_me_2">Click Me 2</button>
	<button id="click_me_3">Click Me 3</button>
</div>
```

#### ** Javascript **

```js
let btn = document.querySelector('#click_me_1');

btn.addEventListener('click', function () {
	console.log('button clicked!!!');
});
btn.addEventListener('click', function () {
	alert('button clicked!!!');
});

btn.addEventListener('mouseover', function () {
	btn.innerText('Stop touching me!!!');
});

window.addEventListener('scroll', function () {
	console.log('Stop scrolling!!!');
});
```

#### ** Output **

```js
Updated DOM output
```

<!-- tabs:end -->

> 🏗The impossible button demo

```js
const btn = document.querySelector('button');

btn.addEventListener('mouseover', function () {
	const height = Math.floor(Math.random() * window.innerHeight);
	const width = Math.floor(Math.random() * window.innerWidth);
	btn.style.left = `${width}px`;
	btn.style.right = `${height}px`;
});

btn.addEventListener('mouseover', function () {
	btn.innerText = 'You got me!!!';
	document.body.style.backgroundColor = 'green';
});
```

## ⚡Events on Multiple Elements

```js
const colors = [
	'red',
	'orange',
	'yellow',
	'green',
	'blue',
	'purple',
	'indigo',
	'violet',
];

const changeColor = function () {
	const h1 = document.querySelector('h1');
	h1.style.color = this.style.backgroundColor;
};

const container = document.querySelector('#boxes');

for (let color of colors) {
	const box = document.createElement('div');
	box.style.backgroundColor = color;
	box.classList.add('box');
	container.appendChild(box);
	box.addEventListener('click', changeColor);
}
```

## ⚡Event Object

```js
document.body.addEventListener('keypress', function (evt) {
	//Event object of the ket that we pressed
	console.log(evt);
});
```

## ⚡Key Events

- keydown
- keypress
- keyup

!> **keypress** feature is no longer recommended. This event has been deprecated.

<!-- tabs:start -->

#### ** HTML **

```html
<form action="#" method="post" id="main_form">
	<a href="#" id="form_destination">
		<img src="#" alt="form" id="form_image" />
	</a>
	<input
		type="text"
		name="username"
		id="username"
		placeholder="Enter username"
	/>
	<input
		type="password"
		name="password"
		id="password"
		placeholder="Enter password"
	/>
	<input type="range" name="status" id="status" min="10" max="100" />
	<input type="checkbox" name="prime" id="prime" /> Prime
	<input type="submit" value="Submit" />
</form>
```

#### ** Javascript **

```js
const input = document.querySelector('#username');

input.addEventListener('keydown', function (evt) {
	console.log('Key Down');
});
input.addEventListener('keyup', function (evt) {
	console.log('Key Up');
});
input.addEventListener('keypress', function (evt) {
	console.log('Key Press');
});
```

<!-- tabs:end -->

## ⚡Form Events & PreventDefault

?> The **preventDefault() method** cancels the default action that belongs to the event.

<!-- tabs:start -->

#### ** HTML **

```html
<form action="#" method="post" id="main_form">
	<input
		type="text"
		name="username"
		id="username"
		placeholder="Enter username"
	/>
	<input
		type="password"
		name="password"
		id="password"
		placeholder="Enter password"
	/>
	<input type="range" name="status" id="status" min="10" max="100" />
	<input type="checkbox" name="prime" id="prime" /> Prime
	<select name="job" id="job">
		<li value="software engineer">Software Engineer</li>
		<li value="frontend developer">Frontend Developer</li>
		<li value="database admin">Database Admin</li>
	</select>
	<input type="submit" value="Submit" />
</form>
```

#### ** Javascript **

```js
const form = document.querySelector('#main_form');
const username = document.querySelector('#username');
const password = document.querySelector('#password');
const prime = document.querySelector('#prime');
const job = document.querySelector('#job');

form.addEventListener('submit', function (e) {
	e.preventDefault();
	console.log('username', username.value);
	console.log('password', password.value);
	console.log('prime', prime.checked);
	console.log('job', job.value);
});
```

<!-- tabs:end -->

## ⚡Input & Change Events

<!-- tabs:start -->

#### ** HTML **

```html
<form action="#" method="post" id="main_form">
	<input
		type="text"
		name="username"
		id="username"
		placeholder="Enter username"
	/>
	<input
		type="password"
		name="password"
		id="password"
		placeholder="Enter password"
	/>
	<input type="range" name="status" id="status" min="10" max="100" />
	<input type="checkbox" name="prime" id="prime" /> Prime
	<select name="job" id="job">
		<li value="software engineer">Software Engineer</li>
		<li value="frontend developer">Frontend Developer</li>
		<li value="database admin">Database Admin</li>
	</select>
	<input type="submit" value="Submit" />
</form>
```

#### ** Javascript **

```js
const form = document.querySelector('#main_form');
const username = document.querySelector('#username');
const password = document.querySelector('#password');
const prime = document.querySelector('#prime');
const job = document.querySelector('#job');

const formData = {};

username.addEventListener('input', function (e) {
	formData['username'] = e.target.value;
});

prime.addEventListener('input', function (e) {
	formData['prime'] = e.target.value;
});

//Collecting data in 1 shor 😉
for (let input of [username, prime, job]) {
	input.addEventListener('input', ({ target }) => {
		const { name, type, value, checked } = target;
		formData[name] = type === 'checkbox' ? checked : value;
	});
}
```

<!-- tabs:end -->

## ⚡Categories of events

?> Most common categories of events that are avaiable and suported by all major browsers.

<a href="https://developer.mozilla.org/en-US/docs/Web/Events#Most_common_categories" target="_blank">
	<img src="./assets/images/mdn-events.png" alt="events" width="700" height="550"/>
</a>
