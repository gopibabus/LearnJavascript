# 🔥Debugging

## ⚡console

### ❇log

?> The Console method **log()** outputs a message to the web console. The message may be a single string (with optional substitution values), or it may be any one or more JavaScript objects.

```js
let x = 1;
let y = 2;
let z = 3;

console.log(x);
console.log('x:', x);
console.log({x, y, z});
```

```js
let user = {
  name: 'Gopi',
  contact: {
    email: 's.gopibabu@gmail.com',
  },
};

console.log(user);//prints only value
console.log({ user });//prints key and value
```

### ❇clear

?> The console.**clear()** method clears the console if the environment allows it.

### ❇variables

```js
console.clear();

console.log('%s is %d years old.', 'Gopi', 28);
```

### ❇Types of messages

?> The console.**info()** method outputs an informational message to the Web Console. In Firefox, a small "i" icon is displayed next to these items in the Web Console's log.

?> The console method **debug()** outputs a message to the web console at the "debug" log level. The message is only displayed to the user if the console is configured to display debug output.

?>console **warn()** Outputs a warning message to the Web Console.

?> console **error()** outputs an error message to the Web Console.

```js
console.log('This is log');
console.info('This is info');
console.debug('This is debug');
console.warn('This is warn');
console.error('This is error');
```

### ❇dir

?> The Console method **dir()** displays an interactive list of the properties of the specified JavaScript object. The output is presented as a hierarchical listing with disclosure triangles that let you see the contents of child objects.

```js
let user = {
  name: 'Gopi',
  contact: {
    email: 's.gopibabu@gmail.com',
  },
};
console.dir(user);
```

### ❇assert

?> The console.**assert()** method writes an error message to the console if the assertion is false. If the assertion is true, nothing happens.

```js
let isItWorking = false;

console.assert(isItWorking, 'This is why!!');
```

### ❇count and countReset

?> The console.**count()** method logs the number of times that this particular call to count() has been called.

?> The console.**countReset()** method resets counter used with console.count().

```js
console.countReset('count');

for (i = 0; i < 10; i++) {
  console.count('count');
}
```

### ❇time, timeEnd, timeLog

?> **time()** starts a timer you can use to track how long an operation takes. You give each timer a unique name, and may have up to 10,000 timers running on a given page. When you call console.**timeEnd()** with the same name, the browser will output the time, in milliseconds, that elapsed since the timer was started.

?> **timeLog()** Logs the current value of a timer that was previously started by calling console.time() to the console.

```js
console.time();

setTimeout(() => {
  console.timeEnd();
}, 5000);

setTimeout(() => {
  console.timeLog();
}, 2000);
```

### ❇group

?> **group()** creates a new inline group in the Web Console log. This indents following console messages by an additional level, until console.**groupEnd()** is called.

```js
console.group('Group1');
console.log('I am in a group1');
console.log('I am also in a group1');
console.groupEnd('Group1');

console.log('I am out of group');
```

### ❇trace

?> The console interface's **trace()** method outputs a stack trace to the Web Console.

```js
function one() {
  two();
}

function two() {
  three();
}
function three() {
  console.trace();
}
one();
```

### ❇table

?> Displays **tabular data as a table**. This function takes one mandatory argument data, which must be an array or an object, and one additional optional parameter columns.

```js
let devices = [
  {
    name: 'iphone',
    brand: 'Apple',
  },
  {
    name: 'galaxy',
    brand: 'Samsung',
  },
];

console.dir(devices);

//If you have to print only name
console.table(devices, ['name']);
```

```js
async function getUsers() {
  let response = await fetch('https://jsonplaceholder.typicode.com/users');
  let data = await response.json();
  console.table(data, ['name', 'email']);
}

getUsers();
```

### add styles to messages

```js
console.log(
  '%c Auth',
  'color: white; background-color: blue',
  'User has logged in'
);
console.log(
  '%c GraphQL',
  'color: white; background-color: green',
  'User data received'
);
console.log(
  '%c Error',
  'color: white; background-color: red',
  'Error getting user data'
);
```

### ❇debugger

?> The **debugger** statement invokes any available debugging functionality, such as setting a breakpoint. If no debugging functionality is available, this statement has no effect.

```js
for (i = 0; i < 5; i++) {
  debugger;//Browser stops at this point and allow us to debug
  console.log(i);
}
```

### ❇References

[🌐 MDN Documentation](https://developer.mozilla.org/en-US/docs/Web/API/Console)

[⏯ Video Reference](https://www.youtube.com/watch?v=_-bHhEGcDiQ)
