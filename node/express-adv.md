# 🔥Express.js - Advanced Topics

### ✳Middleware

?> **Middleware functions** are functions that have access to the request object (**req**), the response object (**res**), and the next middleware function in the application’s request-response cycle. The next middleware function is commonly denoted by a variable named **next**.

```js
app.use(express.json());
```

### ✳Creating Custom Middleware

```js
app.use(function (req, res, next) {
	console.log('Logging...');
	next();
});

app.use(function (req, res, next) {
	console.log('Authenticating...');
	next();
});
```

```js
function log(req, res, next) {
	console.log('Logging...');
	next();
}

function auth(req, res, next) {
	console.log('Authenticating...');
	next();
}

app.use(log);
app.use(auth);
```

### ✳Built-in Middleware

```js
// It parses incoming requests with JSON payloads
app.use(express.json());

// It parses incoming requests with urlencoded payloads
app.use(express.urlencoded({ extended: true }));

// It serves static files
app.use(express.static('public'));
```

### ✳3rd Party Middleware

> [🌐 Reference](https://expressjs.com/en/resources/middleware.html)

```js
//Help secure Express apps with various HTTP headers
const helmet = require('helmet');
app.use(helmet());

//HTTP request logger middleware
var morgan = require('morgan');
app.use(morgan('tiny'));
```

### ✳How to switch between Environments

```js
// We should set NODE_ENV environment variable from terminal.
//process.env.NODE_ENV === app.get('env')
// default value of app.get('env') is development
// we can set Environment variable in Linux using export NODE_ENV=production

if (app.get('env') === 'development') {
	app.use(morgan('tiny'));
	console.log('Morgan is enabled...');
}
```

### ✳How to maintain configuration in the App?

> [🌐 config npm package](https://www.npmjs.com/package/config)

?> **Node-config** organizes hierarchical configurations for your app deployments. It lets you define a set of default parameters, and extend them for different deployment environments (development, qa, staging, production, etc.).

?> Configurations are stored in configuration files within your application, and can be overridden and extended by environment variables, command line parameters, or external sources.

### ✳How to debug Node Applications

> [🌐 debug npm package](https://www.npmjs.com/package/debug)

?> **debug** exposes a function; simply pass this function the name of your module, and it will return a decorated version of **console.error** for you to pass debug statements to. This will allow you to toggle the debug output for different parts of your module as well as the module as a whole.

```js
const startup_debugger = require('debug')('app:startup');
const db_debugger = require('debug')('app:db');

if (app.get('env') === 'development') {
	app.use(morgan('tiny'));
	startup_debugger('Morgan is enabled...');
}
//DB Work
db_debugger('Connected to Database...');
```

**Set Environment Variable**

```bash
//If we have to see app:startup logs
export DEBUG=app:startup

//If we have to see app:db logs
export DEBUG=app:db

//If we have to see app:db and app:startup logs
export DEBUG=app:db,app:startup

//If we have to see all logs
export DEBUG=*

//If you don't want to see any logs
export DEBUG=

//Set DEBUG and run the application
DEBUG=app:db nodemon app.js
```

### ✳Templating Engines

?> There are many templating engines for Node.js apps.

- [Pug](https://pugjs.org/)
- [Mustache](https://mustache.github.io/)
- [EJS](https://ejs.co/)

```js
//Asking Express to use pug as templating engine
app.set('view engine', 'pug');
app.set('views', './views');

app.get('/', (req, res) => {
	res.render('app', { title: 'My Node App', message: 'Hello World!!' });
});
```

```pug
//views/app.pug file
html
    head
        title= title
    body
        h1= message
```

### ✳Database Integration

?> Adding the capability to **connect databases** to Express apps is just a matter of loading an appropriate Node.js driver for the database in your app.

> [🌐 Database integration](https://expressjs.com/en/guide/database-integration.html)

### ⚡Structuring the Project

> [🌐 After structuring the project - Github Repo](https://github.com/gopibabus/LearnNode)
