# 🔥Introduction

<img alt="node.js" width="400" height="200" src="/assets/images/node.png" />

?> Node.js is not a framework. It is a **runtime environment** for executing JavaScript Code outside of the browser. Essentially, Node is a C++ program that embeds Chrome’s v8 engine.

?> Node.js is ideal for building highly scalable, data intensive real time apps.

**2 main reasons** to use Node.js to built applications:

1. JavaScript everywhere.
2. Large ecosystem of open source libraries.

<img alt="v8" width="700px" src="/assets/images/v8.png" />

> **Chrome** and **Node.js** contain JavaScript Engine called **v8 Engine**. This JavaScript Engine is responsible for converting JavaScript code into machine readable code. Chrome provide run time environment to JavaScript for client side applications, in the same way Node.js provide run time environment to JavaScript for server side applications.

?> Node applications are **single-threaded**. That means a single thread is used to serve all clients.

?> Node Applications are Asynchronous(non-blocking) by default. That's why Node.js is ideal for I/O intensive applications.

!> You should **avoid using Node for CPU-intensive applications**, such as a video encoding service. Because while executing these operations, other clients have to wait for the single thread to finish its job andbe ready to serve them.

?> In Node, we don’t have browser environment objects such as **window or the document object**. Instead, we have other objects that are not available in browsers, such as **objects for working with the file system, network, operating system**, etc.,

### ✳Sample Program

```js
function sayHello(name) {
	console.log('Hello ' + name);
}
sayHello('Gopi');

//Output
node app.js
> Hello Gopi
```
