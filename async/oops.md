# 🔥Prototypes & Classes

## ⚡Prototypes

<img src="./assets/images/prototype_hierarchy.png" alt="prototype hierarchy" width="700"/>

?> 🧠**Prototypes** are the mechanism by which JavaScript objects inherit features from one another.

- All JavaScript objects inherit properties and methods from a **prototype**.
- All JavaScript objects inherit properties and methods from a prototype:

  - **Date** objects inherit from **Date.prototype**
  - **Array** objects inherit from **Array.prototype**
  - **String** objects inherit from **String.prototype**
  - **Person** objects inherit from **Person.prototype**

- Date objects, Array objects, and Person objects inherit from **Object.prototype**.

?> 🎯 The **Object.prototype** is on the top of the prototype inheritance chain.

### ✳Custom Methods on Existing Prototypes

```js
let name = 'gopibabu';
name.toUpperCase(); //GOPIBABU
String.prototype.customFunction = () => {
	console.log('This is my custom function on String');
};
name.customFunction(); //This is my custom function on String

let animals = ['pigs', 'goats', 'sheep'];
animals.push('cows'); //['pigs', 'goats', 'sheep', 'cows']
animals;
Array.prototype.customArrayFunction = () => {
	console.log('This is my custom function on Array');
};
animals.customArrayFunction(); //This is my custom function on Array
```

```js
let name = 'gopibabu';
String.prototype; // Actual Object [Template]
name.__prototype__; //Reference of String.prototype
```

## ⚡Factory Functions

- A **factory function** is any function which is not a class or constructor that returns a new object. In JavaScript, any function can return an object. When it does so without the new keyword, it’s a factory function.
- With help of Factory functions we can easily produce object instances without diving into the complexities of classes and the new keyword.

```js
function makeColor(r, g, b) {
	const color = {};
	color.r = r;
	color.g = g;
	color.b = b;

	color.rgb = function () {
		const { r, g, b } = this;
		return `rgb(${r}, ${g}, ${b})`;
	};

	color.hex = function () {
		const { r, g, b } = this;
		return '#' + ((1 << 24) + (r << 16) + (g << 8) + b).toString(16).slice(1);
	};

	return color;
}

const color1 = new makeColor(23, 255, 56);
color1.rgb(); //'rgb(23, 255, 56)'
color1.hex(); //'#17ff38'

const color2 = new makeColor(25, 155, 96);
color2.rgb(); //'rgb(25, 155, 96)'
color2.hex(); //'#199b60'

color1.hex === color2.hex; //False
```

## ⚡Constructor Functions

?> **Constructors** force callers to use the **new** keyword. Factories don’t. That’s it, but that has some relevant side-effects.

- Benefits of using Constructor Functions
  - Instantiates a new instance object and binds this to it within the constructor.
  - Binds **instance.\_\_proto\_\_** to **Constructor.prototype**.
  - Implicitly returns this, which refers to instance.

---

<img src="./assets/images/new_keyword.png" alt="constructor" width="700" style="border: black solid 2px"/>

```js
function makeColor(r, g, b) {
	this.r = r;
	this.g = g;
	this.b = b;
}

makeColor.prototype.rgb = function () {
	const { r, g, b } = this;
	return `rgb(${r}, ${g}, ${b})`;
};

makeColor.prototype.hex = function () {
	const { r, g, b } = this;
	return '#' + ((1 << 24) + (r << 16) + (g << 8) + b).toString(16).slice(1);
};

const color1 = new makeColor(23, 255, 56);
color1.rgb(); //'rgb(23, 255, 56)'
color1.hex(); //'#17ff38'

const color2 = new makeColor(25, 155, 96);
color2.rgb(); //'rgb(25, 155, 96)'
color2.hex(); //'#199b60'

color1.hex === color2.hex; //True
```

## ⚡JS Classes

?> **class** declaration introduced in ES2015 simply works as syntactic sugar over the existing prototype-based inheritance.

!> 💡 Should Capitalize class name

```js
class MakeColor {
	constructor(r, g, b) {
		this.r = r;
		this.g = g;
		this.b = b;
	}
	message(name) {
		console.log(`This is ${name} method`);
	}
	rgb() {
		this.message('rgb');
		const { r, g, b } = this;
		return `rgb(${r}, ${g}, ${b})`;
	}
	hex() {
		this.message('hex');
		const { r, g, b } = this;
		return '#' + ((1 << 24) + (r << 16) + (g << 8) + b).toString(16).slice(1);
	}
}

const color1 = new MakeColor(23, 255, 56);
color1.rgb();
color1.hex();

const color2 = new MakeColor(25, 155, 96);
color2.rgb();
color2.hex();

color1.hex === color2.hex; //true
```

### ✳extends,super and sub classes

```js
class Pet {
	constructor(name, age) {
		this.name = name;
		this.age = age;
	}

	eat() {
		return `${this.name} is eating`;
	}
}

class Cat extends Pet {
	meow() {
		return 'Meowww';
	}
}

class Dog extends Pet {
	constructor(name, age, feature) {
		super(name, age);
		this.feature = feature;
	}
	bark() {
		return 'Woooof';
	}
	identity() {
		return `Hi, you got wonderful dog with ${this.feature}`;
	}
}

let cat1 = new Cat('jersey', 4);
console.log(cat1.eat());
console.log(cat1.meow());

let dog1 = new Dog('hound', 6, 'long neck');
console.log(dog1.eat());
console.log(dog1.bark());
console.log(dog1.identity());
```
