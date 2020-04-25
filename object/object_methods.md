# 🔥Object Methods

### ✳Shorthand Object Properties

```js
const getStats = arr => {
  const max = Math.max(...arr);
  const min = Math.min(...arr);
//Old way of returning object
  return {
    max: max,
    min: min
  };
};

const reviews = [4.5, 3.2, 2.5, 4.75, 5.0, 4.2];

getStats(reviews);//{ max: 5, min: 2.5 }

👇👇👇👇👇👇👇

const getStats = arr => {
  const max = Math.max(...arr);
  const min = Math.min(...arr);
  //Shorthand syntax of object
  return {
    max,
    min
  };
};

const reviews = [4.5, 3.2, 2.5, 4.75, 5.0, 4.2];

getStats(reviews);//{ max: 5, min: 2.5 }
```

### ✳Computed Properties

> We can use a varaible as a key name in an object literal property!!

```js
const user = 'Jools';

const userRoles = {
  [user] : 'Admin',
  [1+6+9] : 'total'
}
userRoles;//{ '16': 'total', Jools: 'Admin' }

const addProp = (obj, key, value) => {
  return {
    ...obj,
    [key]:value
  }
}

addProp(userRoles, 'name', "gopi");//{ '16': 'total', Jools: 'Admin', name: 'gopi' }
```

### ✳Methods in Objects

> We can add functions as properties on Objects. We call them methods 😉

?> This is how, we group common set of functionlity in to one object.

```js
const math = {
  multiply: function(x, y) {
    return x * y;
  },
  divide: function(x, y) {
    return x / y;
  },
  square: function(x) {
    return x * x;
  }
};

math.multiply(4, 2);//8
```

### ✳Methods Shorthand

> There is no need to mention key value pairs for **methods** inside objects.

```js
const math = {
  intialValue: 34,
  multiply(x, y) {
    return x * y;
  },
  divide(x, y) {
    return x / y;
  },
  square(x) {
    return x * x;
  }
};

math.multiply(4, 2);//8
```

### 😎this keyword

> **this** is the object and it refers to current execution scope.

> The value of **this** depends on the invocation context of the function it is used in.

```js
function sayHi(){
  console.log("Hi");//Hi
  console.log(this);//Window object
}

sayHi();
```

```js
const person = {
  first : 'gopi',
  last : 'srungavarapu',
  nickName: 'raju',
  fullName(){
    console.log(this);//person object
    return `${this.first} ${this.last}`
  },
  details() {
    const {first, last, nickName} = this;
     return `${this.nickName} ${this.last}`
  }
}

person.fullName();//'gopi srungavarapu'
person.details();//'raju srungavarapu'

const personDetails = person.details;
personDetails();//Error (window object context)
```

!> **arrow functions** uses window object scope by default not where it is defined. That's why we don't use arrow functions to define methods inside objects.

```js
const person = {
  first : 'gopi',
  last : 'srungavarapu',
  nickName: 'raju',
  printBio: () => {
    console.log(this);//Window Object
    console.log(this.first);//undefined
  }
}

person.printBio();
```

```js
const annoyer = {
  phrases: [
    "this is gopi",
    "she is ammu",
    "fiend is mohan",
    "father is nag",
    "sister in santhi",
    "cousin in lavanya",
    "village is bodawada"
  ],
  pickPhrase() {
    const { phrases } = this;

    const idx = Math.floor(Math.random() * phrases.length);
    return phrases[idx];
  },
  start() {
    this.timerId = setInterval(function(){
      console.log(this.pickPhrase())
    }, 3000)
  },
  startAnnoyer() {
    this.timerId = setInterval(() => {
      console.log(this.pickPhrase())
    }, 3000)
  },
  stopAnnoyer() {
    clearInterval(this.timerId);
  }
};

annoyer.start();
//setTimeInterval is not defined, 
//setTimeInterval is called by window and window context is applied

annoyer.startAnnoyer();//print random phrases
annoyer.stopAnnoyer();//stop printing phrases
```