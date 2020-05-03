# 🔥Asynchronous Code, Callbacks & Promises

<img src="./assets/images/async.png" alt="async" width="700" height="400"/>

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

## ⚡JS is Single threaded

?> At any given point in time, that single JS thread is running at most one line of JS code.

## ⚡How Asynchronous code work in JS?

> **Answer**: Web APIs in browser

<img src="./assets/images/web_api.png" alt="web api" width="700"/>

!> [Live Demo to see how web apis work](http://latentflip.com/loupe/)

?> Browsers come with **Web APIs** that are able to handle certain tasks in the background (like making requests or **setTimeout**).<br>
The **JS call stack** recognizes these **Web API functions** and passes them off to the browser to take care of, when ever they are encountered in the code.<br>
Once the browser finishes those tasks, they return and are pushed onto the stack as a callback.

?> Examples of Web API's methods: **setTimeout()** and **eventListners**

> [Web APIs supported by browsers from 🌐MDN Documentation](https://developer.mozilla.org/en-US/docs/Web/API)
