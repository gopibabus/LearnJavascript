# ✨ String Methods ✨

🎯 String Methods are case sensitive.<br>
💥 Syntax: string.method();<br>
### Concatenate 2 strings

> string1 + string2.<br>

```js
let town = 'Illinois';
let city = 'Evanston';
town + city; //IllinoisEvanston
```

### toUpperCase()
>Convert String to upper case string.<br>

```js
let name = 'Gopibabu Srungavarapu';
name.toUpperCase(); //GOPIBABU SRUNGAVARAPU
```

### toLowerCase()
> Convert String to lower case string.<br>

```js
let name = 'Gopibabu Srungavarapu';
name = name.toLowerCase(); //gopibabu srungavarapu
```

### trim()
> Remove leading and trailing spaces in a string. Used to chain methods.<br>

```js
let wishes = '   Happy Birthday   ';
wishes.trim(); //Happy Birthday
wishes.trim().toUpperCase(); //HAPPY BIRTHDAY
```

---

### indexOf()
> Return index of given string in a String.<br>

```js
let tvShow = 'catDog';
tvShow.indexOf('cat'); //0
tvShow.indexOf('Dog'); //3
tvShow.indexOf('z'); //-1 (not found)
```
### slice(x,y)
> Extracts a section of a string and returns it as a new string, without modifying the original string. x is included & y is excluded from result.<br>

```js
let str = 'supercoolsachinhitscenturyinhydground';
str.slice(0, 5); //super
str.slice(5); //coolsachinhitscenturyinhydground
```
### replace(x, y)
> Replace first occurrence of x with y in a string.<br>

```js
let sportMsg = 'Cricket is entertaining';
sportMsg.replace('Cricket', 'Hockey'); //Hockey is entertaining
let msg = 'ha ha ha';
msg.replace('haa', 'hoo'); //ha ha ha
let commentary = 'Ball is in the air and Ball caught by a fielder';
commentary.replace('Ball', 'Bat'); //Bat is in the air and Ball caught by a fielder
```