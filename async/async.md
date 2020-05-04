# 🔥Asynchronous Code, Callbacks & Promises

<img src="./assets/images/sync-async.gif" alt="async" width="700"/>

<img src="./assets/images/async.png" alt="async" width="700"/>

## ⚡Call Stack

?> "The mechanisam the JS interpreter uses to keep track of it's place in script that calls multiple functions."

### ✳How it works?

<img src="./assets/images/call_stack.gif" alt="call stack" width="700"/>

- When a script calls a function, the interpreter adds it to the call stack and then starts carrying out the function.
- Any functions that are called by that function are added to the call stack further up, and run where their calls are reached.
- When the current function is finished, the interpreter takes it off the stack and resumes execution where it left off in the last code listing.

```js
const bar = () => console.log('bar');

const baz = () => console.log('baz');

const foo = () => {
	console.log('foo');
	bar();
	baz();
};

foo();
```

?> Call Stack of above mentioned code is shown below🚛

<img src="./assets/images/call_stack_js.png" alt="call stack" width="700"/>

---

<img src="./assets/images/call_stack_2.gif" alt="call stack" width="700"/>

## ⚡JS is Single threaded

?> At any given point in time, that single JS thread is running at most one line of JS code.

## ⚡How Asynchronous code work in JS?

> **Answer**: Web APIs in browser

<img src="./assets/images/web_api.png" alt="web api" width="700"/>

---

<img src="./assets/images/set_timeout.gif" alt="web api work" width="700"/>

!> [Live Demo to see how web apis work](http://latentflip.com/loupe/)

?> Browsers come with **Web APIs** that are able to handle certain tasks in the background (like making requests or **setTimeout**).<br>
The **JS call stack** recognizes these **Web API functions** and passes them off to the browser to take care of, when ever they are encountered in the code.<br>
Once the browser finishes those tasks, they return and are pushed onto the stack as a callback.

?> Examples of Web API's methods: **setTimeout()** and **eventListners**

<img src="./assets/images/set_timeout2.gif" alt="set timeout" width="700"/>

> [Web APIs supported by browsers from 🌐MDN Documentation](https://developer.mozilla.org/en-US/docs/Web/API)

> [Nice article on Web APIs & Event loops](https://dev.to/lydiahallie/javascript-visualized-event-loop-3dif)

## ⚡Callbacks

?> Callback is a reference to executable code, or a piece of executable code, that is passed as an argument to other code.

```js
$('#element').fadeIn('slow', function () {
	// callback function
});
```

> In the following simple callback, we are passing same **moveX** function to the **moveX** function as a callback

### ✳Simple Callback

```js
const button = document.querySelector('button');

const moveX = (element, amount, delay, callback) => {
	setTimeout(() => {
		element.style.transform = `translateX(${amount}px)`;
		if (callback) {
			callback();
		}
	}, delay);
};

moveX(button, 100, 1000, () => {
	moveX(button, 200, 1000, () => {
		moveX(button, 300, 1000, () => {
			moveX(button, 400, 1000, () => {
				moveX(button, 500, 1000);
			});
		});
	});
});
```

### ✳Complex Callback

> The following callback moves an element "amount" number of pixels after a delay. If the element will stay on screen, we move the element and call the onSuccess callback function. If the element will move off screen, we do not move the element and instead call the onFailure callback

```js
const btn = document.querySelector('button');

const moveX = (element, amount, delay, onSuccess, onFailure) => {
	setTimeout(() => {
		const bodyBoundary = document.body.clientWidth;
		const elRight = element.getBoundingClientRect().right;
		const currLeft = element.getBoundingClientRect().left;
		if (elRight + amount > bodyBoundary) {
			onFailure();
		} else {
			element.style.transform = `translateX(${currLeft + amount}px)`;
			onSuccess();
		}
	}, delay);
};

// LOOK AT THIS UGLY MESS!
moveX(
	btn,
	300,
	1000,
	() => {
		//success callback
		moveX(
			btn,
			300,
			1000,
			() => {
				//success callback
				moveX(
					btn,
					300,
					1000,
					() => {
						//success callback
						moveX(
							btn,
							300,
							1000,
							() => {
								//success callback
								moveX(
									btn,
									300,
									1000,
									() => {
										//success callback
										alert('YOU HAVE A WIDE SCREEN!');
									},
									() => {
										//failure callback
										alert('CANNOT MOVE FURTHER!');
									}
								);
							},
							() => {
								//failure callback
								alert('CANNOT MOVE FURTHER!');
							}
						);
					},
					() => {
						//failure callback
						alert('CANNOT MOVE FURTHER!');
					}
				);
			},
			() => {
				//failure callback
				alert('CANNOT MOVE FURTHER!');
			}
		);
	},
	() => {
		//failure callback
		alert('CANNOT MOVE FURTHER!');
	}
);
```

> It is hard to understand code with more nested callbacks. Like above example we have to spend so much time to understand what the code is doing. So it is not ideal to write code with more number of callbacks. This is often referred as **Callback Hell**. In order to address this isssue with callbacks, **promises** are introduced by javascript.

## ⚡Promises

?> A Promise is an object representing the eventual completion or failure of an asynchronous operation.

?> Promise is a pattern for writing async code.

?> A Promise is a returned object to which you attach callbacks, instead of passing callbacks into a function.

<img src="./assets/images/promise.gif" alt="promise" width="700"/>

```js
const willGetYouDog = new Promise((resolve, reject) => {
	const rand = Math.random();
	console.log(rand);
	if (rand < 0.5) {
		resolve('Dog granted😃');
	} else {
		reject('Dog rejected😑');
	}
});
```

### ✳resolve

<img src="./assets/images/promise_resolve.gif" alt="promise" width="700"/>

```js
const getImage = new Promise((resolve, reject) => {
	const rand = Math.random();
	console.log(rand);
	if (rand < 0.5) {
		resolve('Image granted😃');
	} else {
		reject('Image rejected😑');
	}
});

getImage.then(() => {
	console.log('Yes, I got my Image😃');
});
```

### ✳reject

<img src="./assets/images/promise_reject.gif" alt="promise" width="700"/>

```js
const getImage = new Promise((resolve, reject) => {
	const rand = Math.random();
	console.log(rand);
	if (rand < 0.5) {
		resolve('Image granted😃');
	} else {
		reject('Image rejected😑');
	}
});

getImage.then(() => {
	console.log('Yes, I got my Image😃');
});
getImage.catch(() => {
	console.log('No, Image for this time😑');
});
```

### ✳Examples

> Realtime Scenario 1 where we return Promise

```js
function willGetYouDog() {
	return new Promise((resolve, reject) => {
		setTimeout(() => {
			const rand = Math.random();
			console.log(rand);
			if (rand < 0.5) {
				resolve('Dog granted😃');
			} else {
				reject('Dog rejected😑');
			}
		});
	}, 5000);
}

//We can chain Methods
let decision = willGetYouDog();
decision
	.then(() => {
		console.log('Yes, I got my Dog😃');
	})
	.catch(() => {
		console.log('No, Dog😑');
	});
```

> Realtime Scenario 2 where we return Promise

```js
function fakeRequest(url) {
	return new Promise((resolve, reject) => {
		setTimeout(() => {
			const pages = {
				'/users': [
					{ id: 1, username: 'hanky' },
					{ id: 2, username: 'shanky' },
				],
				'/about': 'This is about page',
			};
			const data = pages[url];
			if (data) {
				resolve({ status: 200, data });
			} else {
				reject({ status: 404 });
			}
		});
	}, 5000);
}

fakeRequest('/users')
	.then((res) => {
		console.log('Status Code', res.status);
		console.log('Data', res.data);
	})
	.catch((res) => {
		console.log(res.status);
		console.log('No, request failed');
	});
```

> Realtime Scenario 3 where we chain Promises

```js
const fakeRequest = (url) => {
	return new Promise((resolve, reject) => {
		setTimeout(() => {
			const pages = {
				'/users': [
					{ id: 1, username: 'Bilbo' },
					{ id: 5, username: 'Esmerelda' },
				],
				'/users/1': {
					id: 1,
					username: 'Bilbo',
					upvotes: 360,
					city: 'Lisbon',
					topPostId: 454321,
				},
				'/users/5': {
					id: 5,
					username: 'Esmerelda',
					upvotes: 571,
					city: 'Honolulu',
				},
				'/posts/454321': {
					id: 454321,
					title: 'Ladies & Gentlemen, may I introduce my pet pig, Hamlet',
				},
				'/about': 'This is the about page!',
			};
			const data = pages[url];
			if (data) {
				resolve({ status: 200, data }); //resolve with a value!
			} else {
				reject({ status: 404 }); //reject with a value!
			}
		}, 1000);
	});
};

fakeRequest('/users')
	.then((res) => {
		console.log(res);
		const id = res.data[0].id;
		return fakeRequest(`/users/${id}`);
	})
	.then((res) => {
		console.log(res);
		const postId = res.data.topPostId;
		return fakeRequest(`/posts/${postId}`);
	})
	.then((res) => {
		console.log(res);
	})
	.catch((err) => {
		console.log('OH NO!', err);
	});
```

> Refactoring **moveX** callback hell problem with Promises

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
moveX(btn, 100, 1000)
	.then(() => moveX(btn, 100, 1000))
	.then(() => moveX(btn, 100, 1000))
	.then(() => moveX(btn, 100, 1000))
	.then(() => moveX(btn, 100, 1000))
	.then(() => moveX(btn, 100, 1000))
	.then(() => moveX(btn, 100, 1000))
	.then(() => moveX(btn, 100, 1000))
	.then(() => moveX(btn, 100, 1000))
	.then(() => moveX(btn, 100, 1000))
	.then(() => moveX(btn, 100, 1000))
	.then(() => moveX(btn, 100, 1000))
	.then(() => moveX(btn, 100, 1000))
	.then(() => moveX(btn, 100, 1000))
	.then(() => moveX(btn, 100, 1000))
	.then(() => moveX(btn, 100, 1000))
	.catch(({ bodyBoundary, amount, elRight }) => {
		console.log(`Cannot Move! Body is ${bodyBoundary}px wide`);
		console.log(`Element is at ${elRight}px, ${amount}px is too large!`);
	});
```
