# 🔥Building RESTful APIs using Express

<img alt="express" width="500" src="/assets/images/express.png" />

?> **[Expressjs](https://expressjs.com/)** is a minimal and flexible Node.js web application framework that provides a robust set of features for web and mobile applications.

### ✳How to intall Expressjs?

```bash
npm i express
```

### ✳How to build a web server using Expressjs?

```bash
npm i express
```

```js
// app.js
const express = require('express');
const app = express();

app.get('/', (req, res) => {
	res.send('Hello World!!!');
});

app.get('/api/courses', (req, res) => {
	res.send([1, 2, 3, 4]);
});

app.listen(3000, () => console.log('Listening to the port 3000...'));
```

> [🌐 Express API Reference](https://expressjs.com/en/4x/api.html)

### ✳How to set Environment variables and use them?

**On Windows**

```bash
set PORT=5000
```

**On Mac/Linux**

```bash
export PORT=5000
```

**Using Environment Variables inside Node application**

```js
const port = process.env.PORT || 3000;
app.listen(port, () => console.log(`Listening to the port ${port}...`));
```

### ✳How to retrieve parameters & request parameters?

```js
app.get('/api/posts/:year/:month', (req, res) => {
	res.send({ params: req.params, queryParams: req.query });
});
```

```bash
http://localhost:5000/api/posts/2000/june?sortBy=year
//Output
{"params":{"year":"2000","month":"june"},"queryParams":{"sortBy":"year"}}
```

### ✳How to handle GET and POST requests?

```js
app.get('/api/courses/:id', (req, res) => {
	let course = courses.find((c) => c.id === parseInt(req.params.id));
	if (!course) {
		res.status(404).send(`The course with id ${req.params.id} was not found!!`);
	}
	res.send(course);
});

app.post('/api/courses', (req, res) => {
	const course = {
		id: courses.length + 1,
		name: req.body.name,
	};
	courses.push(course);
	res.send(course);
});
```

### ✳How to validate user input using Joi library?

```js
const Joi = require('joi');
app.post('/api/courses', (req, res) => {
	const schema = {
        name: Joi.string().min(3).required();
    };
    const result = Joi.validate(req.body, schema);
	if (result.error) {
        res.status(400).send(result.error);
        return;
    }
}
```

### ✳How to handle PUT request?

```js
app.put('/api/courses/:id', (req, res) => {
	let course = courses.find((c) => c.id === parseInt(req.params.id));
	if (!course) {
		res.status(404).send(`The course with id ${req.params.id} was not found!!`);
		return;
	}

	const schema = {
		name: Joi.string().min(3).required(),
	};
	const result = Joi.validate(req.body, schema);
	if (result.error) {
		res.status(400).send(result.error);
		return;
	}
	course.name = req.body.name;
	res.send(course);
});
```

### ✳How to handle DELETE request?

```js
app.delete('/api/courses/:id', (req, res) => {
	let course = courses.find((c) => c.id === parseInt(req.params.id));
	if (!course) {
		res.status(404).send(`The course with id ${req.params.id} was not found!!`);
		return;
	}

	const index = courses.indexOf(course);
	courses.splice(index, 1);
	res.send(course);
});
```
