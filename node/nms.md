# 🔥Node Module System

<img alt="NMS" width="700" src="/assets/images/nms.png" />

### ✳Global Object

?> In browsers, **window** is the global object.

```js
console.log() === window.console.log();
```

?> But in Node.js **global** is the global object.

```js
console.log() === global.console.log();

setTimeout() === global.setTimeout();
clearTimeout() === global.clearTimeout();

setInterval() === global.setInterval();
clearInterval() === global.clearInterval();
```

!> If you have to use same global object in Node.js and in browsers, we should use **globalThis**.

```js
//In Browser
window.console.log() === globalThis.console.log();

//In Node.js
global.console.log() === globalThis.console.log();
```

### ✳Modules

?> In Node, **every file is a module**. Variables and functions defined in that file are scoped to that module. They are not available outside of the module.

### ✳Creating a Module

```js
//(logger.js)
var url = 'https://mylogger.io/log';

function log(message) {
	console.log(message);
}

module.exports = log;
```

### ✳Loading a Module

```js
//(app.js)
const log = require('./logger');

log('message'); //message
```

### ✳Module Wrapper Function

<iframe 
    width="560" 
    height="515" 
    src="https://www.youtube.com/embed/WlWdbtJoCLQ?controls=0" 
    frameborder="0" 
    allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" 
    allowfullscreen
    >
</iframe>

> [🌐 Reference](https://www.vskills.in/certification/tutorial/web-development/node-js/the-module-wrapper/)

## ⚡Built-in Modules

> [🌐 Node.js Built in Modules](https://nodejs.org/dist/latest-v12.x/docs/api/)

### ✳Path Module

> [🌐 Reference](https://nodejs.org/dist/latest-v12.x/docs/api/path.html)

```js
const path = require('path');

let pathObj = path.parse(__filename);

console.log(pathObj);
```

### ✳OS Module

[🌐 Reference](https://nodejs.org/dist/latest-v12.x/docs/api/os.html)

```js
const os = require('os');

let totalMemory = os.totalmem();
let freeMemory = os.freemem();

console.log(`Total Memory: ${totalMemory} and Free Memory: ${freeMemory}`);
```

### ✳File System Module

> [🌐 Reference](https://nodejs.org/dist/latest-v12.x/docs/api/fs.html)

```js
const fs = require('fs');

//Synchronous Method
const files = fs.readdirSync('./');
console.log(files);

//Asynchronous Method
fs.readdir('./', function (err, files) {
	if (err) console.log('Error', err);
	else console.log(files);
});
```

!> Always use Asynchronous Methods over Synchronous Methods.

### ✳Events Modules

> [🌐 Reference](https://nodejs.org/dist/latest-v12.x/docs/api/events.html)

**Event without Arguments**

```js
const EventEmitter = require('events');

class MyEmitter extends EventEmitter {}

const myEmitter = new MyEmitter();

//Register a Listner
myEmitter.on('messageEvent', () => {
	console.log('an event occurred!');
});

//Raised an Event
myEmitter.emit('messageEvent');
```

**Event with Arguments**

?> **EventEmitter** is one of the core classes in Node that allows us to raise (emit) and handle events. Several built-in classes in Node derive fromEventEmmiter.

```js
const EventEmitter = require('events');

class MyEmitter extends EventEmitter {}

const myEmitter = new MyEmitter();

//Register a Listner
myEmitter.on('messageEvent', (arg) => {
	console.log('an event occurred!', arg);
});

//Raised an Event
myEmitter.emit('messageEvent', { id: 1, url: 'https://gopibabu.live' });
```

### ✳HTTP Module

> [🌐 Reference](https://nodejs.org/dist/latest-v12.x/docs/api/http.html)

```js
const http = require('http');
const server = http.createServer(function (req, res) {
	if (req.url === '/') {
		res.write('Home Page');
		res.end();
	}

	if (req.url === '/contact') {
		res.write('Contact Page');
		res.end();
	}

	if (req.url === '/api/courses') {
		res.write(JSON.stringify([1, 2, 3]));
		res.end();
	}
});

// server.on('connection', (socket) => {
// 	console.log('New Connection...');
// });
server.listen(3000);
console.log('Server running on port 3000...');
```
