# 🔥DOM Manipulation

> **D**ocument **O**bject **M**odel

- The **DOM** is a Javascript representation of a webpage.
- It's your JS **window** into the contents of a webpage.
- It's just bunch of objects that you can interact with via JS.

<img src="./assets/images/dom-1.png" alt="DOM" width="700" height="400"/>

---

<img src="./assets/images/dom-2.png" alt="DOM" width="700" height="400"/>

?> 🎯 The **document** object is our entry point into the world of the **DOM**. It contains representation of all the content on a page, plus tons of useful methods and properties.

## ⚡Selecting

### ✳getElementById

> Select element in DOM with it's id.

<!-- tabs:start -->

#### ** HTML **

```html
<div class="section">
	<p id="post1">
		Lorem ipsum dolor sit amet consectetur adipisicing elit. Aliquid laboriosam,
		incidunt velit totam dolorem aliquam, id culpa asperiores vel quod tempore
		officia nobis unde hic. Eaque quia libero explicabo voluptatem!
	</p>
	<img
		id="post1-image"
		src="https://source.unsplash.com/user/erondu/daily"
		alt="random"
		width="500px"
	/>
</div>
```

#### ** Javascript **

```js
let post1 = document.getElementById('post1');
console.dir(post1); //HTMLParagraphElement of post1

let image1 = document.getElementById('post1-image');
console.dir(image1); // HTMLImageElement of image1
```

<!-- tabs:end -->

### ✳getElementByTagName

> Select element in DOM with it's tag name.

<!-- tabs:start -->

#### ** HTML **

```html
<div class="section">
	<p id="post1">
		Lorem ipsum dolor sit amet consectetur adipisicing elit. Aliquid laboriosam,
		incidunt velit totam dolorem aliquam, id culpa asperiores vel quod tempore
		officia nobis unde hic. Eaque quia libero explicabo voluptatem!
	</p>
	<img
		id="post1-image"
		src="https://source.unsplash.com/user/erondu/daily"
		alt="random"
		width="500px"
	/>
</div>
<div class="section">
	<p id="post2">
		Lorem ipsum dolor sit amet consectetur adipisicing elit. Aliquid laboriosam,
		incidunt velit totam dolorem aliquam, id culpa asperiores vel quod tempore
		officia nobis unde hic. Eaque quia libero explicabo voluptatem!
	</p>
	<img
		id="post2-image"
		src="https://source.unsplash.com/user/erondu/daily"
		alt="random"
		width="500px"
	/>
</div>
```

#### ** Javascript **

```js
let paragraphs = document.getElementByTagName('p');
console.dir(post1); //HTMLCollection of paragraph objects

let images = document.getElementByTagName('img');
console.dir(image1); // HTMLCollection of image objects
```

<!-- tabs:end -->

> **HTMLCollection** is displays like an array, but it is not an array. We can access contents inside collection using indices and can get length but we can't any apply array methods on the collection.

> We can iterate **HTMLCollections** using **for loop**.

### ✳getElementByClassName

> Select element in DOM with it's class name.

<!-- tabs:start -->

#### ** HTML **

```html
<div class="section">
	<p class="post">
		Lorem ipsum dolor sit amet consectetur adipisicing elit. Aliquid laboriosam,
		incidunt velit totam dolorem aliquam, id culpa asperiores vel quod tempore
		officia nobis unde hic. Eaque quia libero explicabo voluptatem!
	</p>
	<img
		class="post-image"
		src="https://source.unsplash.com/user/erondu/daily"
		alt="random"
		width="500px"
	/>
</div>
<div class="section">
	<p class="post">
		Lorem ipsum dolor sit amet consectetur adipisicing elit. Aliquid laboriosam,
		incidunt velit totam dolorem aliquam, id culpa asperiores vel quod tempore
		officia nobis unde hic. Eaque quia libero explicabo voluptatem!
	</p>
	<img
		class="post-image"
		src="https://source.unsplash.com/user/erondu/daily"
		alt="random"
		width="500px"
	/>
</div>
```

#### ** Javascript **

```js
let paragraphs = document.getElementByClassName('p');
console.dir(post1); //HTMLCollection of paragraph objects

let images = document.getElementByClassName('img');
console.dir(image1); // HTMLCollection of image objects
```

<!-- tabs:end -->

### ✳querySelector

> A newer, all-in-one method to select a single Element.

```js
//Finds first h1 element
document.querySelector('h1');

//Finds first element with id of red
document.querySelector('#red');

//Finds first element with class of big
document.querySelector('.big');
```

<!-- tabs:start -->

#### ** HTML **

```html
<div class="section">
	<p class="post">
		Lorem ipsum dolor sit amet consectetur adipisicing elit. Aliquid laboriosam,
		incidunt velit totam dolorem aliquam, id culpa asperiores vel quod tempore
		officia nobis unde hic. Eaque quia libero explicabo voluptatem!
	</p>
	<img
		id="post-image1"
		src="https://source.unsplash.com/user/erondu/daily"
		alt="random"
		width="500px"
	/>
</div>
<div class="section">
	<p class="post">
		Lorem ipsum dolor sit amet consectetur adipisicing elit. Aliquid laboriosam,
		incidunt velit totam dolorem aliquam, id culpa asperiores vel quod tempore
		officia nobis unde hic. Eaque quia libero explicabo voluptatem!
	</p>
	<img
		id="post-image2"
		src="https://source.unsplash.com/user/erondu/daily"
		alt="random"
		width="500px"
	/>
	<input type="email" name="email" id="email" />
</div>
```

#### ** Javascript **

```js
let paragraph = document.querySelector('p');
console.dir(paragraph); //HTMLParagraphElement

let paragraph = document.querySelector('p.post');
console.dir(paragraph); //HTMLParagraphElement

let image = document.querySelector('#post-image1');
console.dir(image); // HTMLImageElement

let email = document.querySelector('input[type="email"]');
console.dir(email); // HTMLInputElement
```

<!-- tabs:end -->

### ✳querySelectorAll

> A newer, all-in-one method that return a collection of matching elements.

```js
//Finds all h1 elements
document.querySelectorAll('h1');

//Finds element with id of red
document.querySelectorAll('#red');

//Finds all elements with class of big
document.querySelectorAll('.big');
```

<!-- tabs:start -->

#### ** HTML **

```html
<div class="section">
	<p class="post">
		Lorem ipsum dolor sit amet consectetur adipisicing elit. Aliquid laboriosam,
		incidunt velit totam dolorem aliquam, id culpa asperiores vel quod tempore
		officia nobis unde hic. Eaque quia libero explicabo voluptatem!
	</p>
	<img
		id="post-image1"
		src="https://source.unsplash.com/user/erondu/daily"
		alt="random"
		width="500px"
	/>
</div>
<div class="section">
	<p class="post">
		Lorem ipsum dolor sit amet consectetur adipisicing elit. Aliquid laboriosam,
		incidunt velit totam dolorem aliquam, id culpa asperiores vel quod tempore
		officia nobis unde hic. Eaque quia libero explicabo voluptatem!
	</p>
	<img
		id="post-image2"
		src="https://source.unsplash.com/user/erondu/daily"
		alt="random"
		width="500px"
	/>
	<input type="email" name="email" id="email" />
</div>
```

#### ** Javascript **

```js
let paragraphs = document.querySelectorAll('p');
console.dir(paragraphs); //NodeList

let posts = document.querySelectorAll('p.post');
console.dir(posts); //NodeList

let image = document.querySelectorAll('#post-image1');
console.dir(image); // NodeList

let email = document.querySelectorAll('input[type="email"]');
console.dir(email); // NodeList
```

<!-- tabs:end -->

> **NodeList** is displays like an array, but it is not an array. It is similar to **HTMLCollection**. We can access contents inside collection using indices, can get length and can apply forEach but cannot apply other array methods on the **NodeList**.

## ⚡Methods & Properties

<img src="./assets/images/dom-methods.png" alt="DOM" width="700" height="400"/>

### ✳innerText

> The **innerText** property of the HTMLElement represents the "rendered" text content of a node and its descendants.

<!-- tabs:start -->

#### ** HTML **

```html
<div class="section">
	<p class="post">
		Lorem ipsum dolor sit amet consectetur adipisicing elit. Aliquid laboriosam,
		incidunt velit totam dolorem aliquam, id culpa asperiores vel quod tempore
		officia nobis unde hic. Eaque quia libero explicabo voluptatem!
	</p>
	<script>
		console.log('message');
	</script>
	<ul>
		<li>one</li>
		<li>two</li>
		<li style="visibility: hidden;">three</li>
	</ul>
</div>
```

#### ** Javascript **

```js
let el = document.querySelector('div').innerText;
console.log(el);
```

#### ** Output **

```txt
Lorem ipsum dolor sit amet consectetur adipisicing elit. Aliquid laboriosam, incidunt velit totam dolorem aliquam,
id culpa asperiores vel quod tempore officia nobis unde hic. Eaque quia libero explicabo voluptatem!

one
two
```

<!-- tabs:end -->

### ✳textContent

> The **textContent** property of the Node interface represents the text content of the node and its descendants.

1. **textContent** gets the content of all elements, including **script and style** elements. In contrast, innerText only shows “human-readable” elements.
2. **textContent** returns every element in the node. In contrast, **innerText** is aware of styling and won’t return the text of “hidden” elements.

<!-- tabs:start -->

#### ** HTML **

```html
<div class="section">
	<p class="post">
		Lorem ipsum dolor sit amet consectetur adipisicing elit. Aliquid laboriosam,
		incidunt velit totam dolorem aliquam, id culpa asperiores vel quod tempore
		officia nobis unde hic. Eaque quia libero explicabo voluptatem!
	</p>
	<script>
		console.log('message');
	</script>
	<ul>
		<li>one</li>
		<li>two</li>
		<li style="visibility: hidden;">three</li>
	</ul>
</div>
```

#### ** Javascript **

```js
let el = document.querySelector('div').textContent;
console.log(el);
```

#### ** Output **

```txt
				Lorem ipsum dolor sit amet consectetur adipisicing elit. Aliquid
				laboriosam, incidunt velit totam dolorem aliquam, id culpa asperiores
				vel quod tempore officia nobis unde hic. Eaque quia libero explicabo
				voluptatem!

			console.log('message');

			one
			two
			three
```

<!-- tabs:end -->

### ✳innerHTML

> The Element property **innerHTML** gets or sets the HTML markup contained within the element.
> We can replace HTML content inside an element using **innerHTML**

<!-- tabs:start -->

#### ** HTML **

```html
<div class="section">
	<h1>Hello World</h1>
	<ul id="main_list">
		<li>one</li>
		<li>two</li>
		<li style="visibility: hidden;">three</li>
	</ul>
</div>
```

#### ** Javascript **

```js
let el = document.querySelector('#main_list').innerHTML;
console.log(el);
let heading = document.querySelector('h1');
heading += ' gopi';
```

#### ** Output **

```txt
<li>one</li>
<li>two</li>
<li style="visibility: hidden;">three</li>
```

<!-- tabs:end -->

### ✳HTML Element Attributes & Methods

?>**value:** Updates and retrieves input field value.

?>**checked:** Make checkbox field checked or unchecked.

?>**placeholder:** Updates and retrieves placeholder text in input field.

?>**href:** Updates and retrieves href value in anchor fields.

?>**src:** Updates and retrieves src value in image fields.

?>**getAttribute():** Retrieves attribute value in a HTML element.

?>**setAttribute():** Updated attribute value in a HTML element.

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
	<input type="range" name="status" id="status" min="10" max="1000" step="10" />
	<input type="checkbox" name="prime" id="prime" /> Prime
	<input type="submit" value="Submit" />
</form>
```

#### ** Javascript **

```js
document.querySelector('#username').value = 'johnmarty';
document.querySelector('#username').placeholder = 'Enter username please...';
document.querySelector('#status').value;
document.querySelector('input[type="checkbox"]').checked = true;
document.querySelector('#form_destination').href = 'https://cats.com';
document.querySelector('#form_image').src = 'https://cats.com/image1.jpg';

let rangeValue = document.querySelector('input[type="range"]');
rangeValue.getAttribute('min');
rangeValue.setAttribute('max', 5000);
rangeValue.setAttribute('step', 100);
rangeValue.setAttribute('tye', 'radio');
```

<!-- tabs:end -->

### ✳Finding Parent, Children & Siblings Elements

<!-- tabs:start -->

#### ** HTML **

```html
<div class="section">
	<p class="post">
		Lorem ipsum dolor sit amet consectetur adipisicing elit. Aliquid laboriosam,
		incidunt velit totam dolorem aliquam, id culpa asperiores vel quod tempore
		officia nobis unde hic. Eaque quia libero explicabo voluptatem!
	</p>
	<script>
		console.log('message');
	</script>
	<ul id="main_list">
		<li>one</li>
		<li>two</li>
		<li style="visibility: hidden;">three</li>
	</ul>
</div>
```

#### ** Javascript **

```js
document.querySelector('li').parentElement;
document.querySelector('li').parentElement.parentElement;
document.querySelector('ul').children; //HTMLCollection of li
document.querySelector('ul').children[0];

let firstLi = document.querySelector('ul').children[0];
firstLi.nextElementSibling;
let secondLi = firstLi.nextElementSibling;
secLI.previousElementSibling;
```

#### ** Output **

```js
<ul id='main_list'>
	<li>one</li>
	<li>two</li>
	<li style='visibility: hidden;'>three</li>
</ul>

<div class="section">...</div>

HTMLCollection

<li>one</li>

<li>two</li>
<li>one</li>
```

<!-- tabs:end -->

### ✳Changing Multiple Elements

<!-- tabs:start -->

#### ** HTML **

```html
<div class="section">
	<p class="post">
		Lorem ipsum dolor sit amet consectetur adipisicing elit. Aliquid laboriosam,
		incidunt velit totam dolorem aliquam, id culpa asperiores vel quod tempore
		officia nobis unde hic. Eaque quia libero explicabo voluptatem!
	</p>
	<script>
		console.log('message');
	</script>
	<ul id="main_list">
		<li>one</li>
		<li>two</li>
		<li style="visibility: hidden;">three</li>
	</ul>
</div>
```

#### ** Javascript **

```js
const allLis = document.querySelectorAll('li');

for (let i = 0; i < allLis.length; i++) {
	console.log(allLis[i].innerText);
	allLis[i].innerText = 'We are the champions';
}
```

#### ** Output **

```js
one
two
three
We are the champions
We are the champions
We are the champions
```

<!-- tabs:end -->

### ✳Altering Styles

> We can assign styles on HTML elements using **style** property.
> If we are applying style susing javascript, It is inline styles and it will take precedence over styles in stylesheet.

!> We cannot access styles on HTML Elements, if they are defined in style sheets

?> We can access styles on HTML Elements only when we define styles inline.

?> In javascript style properties are in camelCase<br>
**Example**: background-color = backgroundColor

> The **Window.getComputedStyle()** method returns an object containing the values of all CSS properties of an element including styles from external stylesheets.

<!-- tabs:start -->

#### ** HTML **

```html
<div class="section">
	<h1>Hello World</h1>
	<p class="post">
		Lorem ipsum dolor sit amet consectetur adipisicing elit. Aliquid laboriosam,
		incidunt velit totam dolorem aliquam, id culpa asperiores vel quod tempore
		officia nobis unde hic. Eaque quia libero explicabo voluptatem!
	</p>
	<script>
		console.log('message');
	</script>
	<ul id="main_list">
		<li>one</li>
		<li>two</li>
		<li style="visibility: hidden;">three</li>
	</ul>
</div>
```

#### ** Javascript **

```js
const h1 = document.querySelector('h1');
h1.style.color = 'red';
h1.style.backgroundColor = 'yellow';
h1.style.fontSize = '40px';

let para = document.querySelector('p');
let compStyles = getComputedStyle(para);
compStyles.color;
compStyles.fontSize;
```

#### ** Output **

```txt
DOM with modified css properties.
```

<!-- tabs:end -->

### ✳Manipulating Classes

<!-- tabs:start -->

#### ** HTML **

```html
<div class="section">
	<h1>Hello World</h1>
	<p class="post">
		Lorem ipsum dolor sit amet consectetur adipisicing elit. Aliquid laboriosam,
		incidunt velit totam dolorem aliquam, id culpa asperiores vel quod tempore
		officia nobis unde hic. Eaque quia libero explicabo voluptatem!
	</p>
	<script>
		console.log('message');
	</script>
	<ul id="main_list">
		<li class="list_item">one</li>
		<li class="list_item">two</li>
		<li class="list_item">three</li>
	</ul>
</div>
```

#### ** Javascript **

```js
const todo = document.querySelector('#main_list .list_item');
todo.classList.add('done'); //Add Class to list of classes
todo.classList.remove('done'); //Remove Class to list of classes
todo.classList.toggle('done'); //Toggle Class
```

#### ** Output **

```txt
DOM with modified classes on elements.
```

<!-- tabs:end -->

### ✳Creating Elements

<!-- tabs:start -->

#### ** HTML **

```html
<div class="section">
	<h1>Hello World</h1>
	<section>
		<p class="post">
			Lorem ipsum dolor sit amet consectetur adipisicing elit. Aliquid
			laboriosam, incidunt velit totam dolorem aliquam, id culpa asperiores vel
			quod tempore officia nobis unde hic. Eaque quia libero explicabo
			voluptatem!
		</p>
	</section>
	<script>
		console.log('message');
	</script>
	<ul id="main_list">
		<li class="list_item">one</li>
		<li class="list_item">two</li>
		<li class="list_item">three</li>
	</ul>
</div>
```

#### ** Javascript **

```js
const newh2 = document.createElement('h2');
newh2.innerText('This is part of DOM manipulation');
newh2.classList.add('highlight');

let section = document.querySelector('section');
section.appendChild(newh2); //Append end of section element

const newImg = document.createElement('img');
newImg.src = 'https://images.gopibabu.live/image1.jpg';
newImg.style.width = '500px';
document.body.appendChild(newImg);
```

#### ** Output **

```txt
DOM with newely created elements.
```

<!-- tabs:end -->

### ✳Append, Prepend & InsertBefore

<!-- tabs:start -->

#### ** HTML **

```html
<div class="section">
	<h1>Hello World</h1>
	<section>
		<p class="post">
			Lorem ipsum dolor sit amet consectetur adipisicing elit. Aliquid
			laboriosam, incidunt velit totam dolorem aliquam, id culpa asperiores vel
			quod tempore officia nobis unde hic. Eaque quia libero explicabo
			voluptatem!
		</p>
	</section>
	<script>
		console.log('message');
	</script>
	<ul id="main_list">
		<li class="list_item">one</li>
		<li class="list_item">two</li>
		<li class="list_item">three</li>
	</ul>
</div>
```

#### ** Javascript **

```js
const parentUL = document.querySelector('ul');
const firstLi = document.querySelector('li');
const newLi = document.createElement('li');
newLi.innerText = 'Cricket';

parentUL.appendChild(newLi); //Add end of the list

parentUL.insertBefore(newLi, firstLi);

parentUL.insertAdjacentElement('beforebegin', newLi);
parentUL.insertAdjacentElement('afterbegin', newLi);
parentUL.insertAdjacentElement('beforeend', newLi);
parentUL.insertAdjacentElement('afterend', newLi);

const paraEl = document.querySelector('p');
let spanEl = document.createElement('span');
spanEl.innerText = 'This is span element';
const newImg = document.createElement('img');
newImg.src = 'https://images.gopibabu.live/image1.jpg';
newImg.style.width = '500px';

//We can add multiple elements using append and prepend methods
paraEl.append(newImg, spanEl);
paraEl.prepend(spanEl, newImg);
```

#### ** Output **

```txt
DOM with newely created elements.

<!-- Placement od element for insertAdjacentElement method -->
<!-- beforebegin -->
<ul>
  <!-- afterbegin -->
  <li></li>
  <!-- beforeend -->
</ul>
<!-- afterend -->
```

<!-- tabs:end -->

### ✳removeChild & remove

<!-- tabs:start -->

#### ** HTML **

```html
<div class="section">
	<h1>Hello World</h1>
	<section>
		<p class="post">
			Lorem ipsum dolor sit amet consectetur adipisicing elit. Aliquid
			laboriosam, incidunt velit totam dolorem aliquam, id culpa asperiores vel
			quod tempore officia nobis unde hic. Eaque quia libero explicabo
			voluptatem!
		</p>
	</section>
	<script>
		console.log('message');
	</script>
	<ul id="main_list">
		<li class="list_item">one</li>
		<li class="list_item">two</li>
		<li class="list_item">three</li>
	</ul>
</div>
```

#### ** Javascript **

```js
let ul = document.querySelector('#main_list');
let allLis = ul.querySelectorAll('#main_list li');
let firstLi = allLis[0];
let secondLi = allLis[1];

ul.removeChild(firstLi);
firstLi.remove();
secondLi.remove();
```

#### ** Output **

```txt
DOM with updated elements.
```

<!-- tabs:end -->
