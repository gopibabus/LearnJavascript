# ✨Operators✨

## ⚡️Comparison Operators
<br>

| Operator 	| Description              	|
|----------	|--------------------------	|
| **>**  	| Greater Than             	|
| **<**    	| Less Than                	|
| **>=**   	| Greater than or Equal to 	|
| **<=**   	| Less than or Equal to    	|
| **==**   	| Equality                 	|
| **!=**   	| Not Equal                	|
| **===**  	| Strict Equality          	|
| **!==**  	| Strict Non Equality      	|

---

```js
10 > 1; //True
0.2 > 0.3; //False
-10 < 0; //True
50.5 < 5; //False
0.5 <= 0.5; //True
99 >= 4; //True
99 >= 99; //True
'a' < 'b'; //True
'A' > 'a'; //False
```

## 🔆 == (Double Equals)

* Checks for equality of value, but not eqality of type.
* It coerces both values to the same type and then compares.

```js
5 == 5; //True
'b' == 'c'; //false
7 == '7'; //True
0 == ''; //True
true == false; //False
0 == false; //True
null == undefined; //True
10 != '10'; //False
```

## 🔆 === (Triple Equals)

* Checks for equality of value and type.

```js
5 === 5; //True
1 === 2; //False
2 === '2'; //False
false === 0; //False
10 !== '10'; //True
```

?> 🎯 **console.log()** prints arguments to the console.

## ⚡️Logical Operators

### 👀 AND (&&)

Both sides must be true in order for the whole thing to be true.

```js
1 <= 4 && 'a' === 'a'; //True

9 > 10 && 9 >= 9 //False

'abc'.length === 3 && 1 + 1 === 4; //False
```

```js
let password = 'password#123';

if (password.length >= 6 && password.indexOf(' ') === -1) {
    console.log("Valid Password");
}
else {
    console.log("Invalid Password");
}
```

### 👀 OR (||)

If oneside is true, the whole thing is true

```js
1 !== 1 || 10 === 10; //True

10 / 2 === 5 || null; //True

0 || undefined; //False
```

```js
let age = 76;

if (age < 6 || age >= 65) {
    console.log("You get in for free!!");
}
else {
    console.log("That will be 10 please");
}
```

### 👀 NOT(||)

?> **!**expression returns true if the expression is false.

```js
!null //True

!(0 === 0) //False

!(3 <= 4) //False
```

## ⚡️Operator Precedence

> NOT (!) has higher precedence than && and ||<br>
> && has higher precedence than ||<br>
> You can alter this precedence using ( )

## ⚡️Truthy and Falsy Values

* All values have an inherent truthy or falsy value.
* **Falsy Values**
    * false
    * 0
    * "" (empty string)
    * null
    * undefined
    * NaN
* Everything else is **truthy**.
