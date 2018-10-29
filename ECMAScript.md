ES6 is short for ECMAScript 6. ECMAScript is a scripting language standard created by Netscape and Sun Microsystems. JavaScript is the most popular implementation of  ECMAScript.

JavaScript follows the core of ECMAScript, but additionally has the DOM API, which the browser provides the DOM. Node.js, built on the V8 Engine, does not have a DOM, but still follows the ECMAScript standard allowing nodejs to use the same data types, operators, objects and functions that Javascript normally does.

ES6 is the 6th edition of ECMAScript and every year there is usually a new standard with updated features. The version number is one number ahead of the year it was developed. Ex: ES6 was developed in 2015. The most current version is ES9 and was finalized in June 2018. Most modern frameworks use ES6 and ES7, with some using ES8.

Google Chrome, Firefox, Opera, and Edge support ES6 (Edge has a few features missing, not shocking)
Chrome, Firefox, and Opera partially support ES7. Most frameworks using ES7 use BabelJS to transpile ES7+ to ES6. Internet Explorer 11 only supports up to ES5.

There are quite a few new additions in ES6 that have changed the way that developers write JavaScript. One of the most interesting features are arrow functions. Arrow functions behave similarly to vanilla functions, but have less code to be written in declaration.
Ex:
ES5 <=
```
function awakenTiredSoul(me) {
	var caffeine = "Cold Brew";
	return me + caffeine;
}
```
ES6+
```
awakenTiredSoul = (me) => {
	var caffeine = "Cold Brew";
	return me + caffeine;
}
```
You may be thinking, "Alright, whatever. I didn’t really mind typing out the word function." I get it. But! ES6 came with a new set of functions, which have allowed developers to focus on writing [functional] JavaScript.

Eric Elliott explains functional programming as: *"Functional programming (often abbreviated FP) is the process of building software by composing pure functions, avoiding shared state, mutable data, and side-effects. Functional programming is declarative rather than imperative, and application state flows through pure functions. Contrast with object oriented programming, where application state is usually shared and colocated with methods in objects… …Functional code tends to be more concise, more predictable, and easier to test than imperative or object oriented code."*

Here are some examples of things you can do in ES6 that are pretty neat:

Return the first item in an array:
```
const array = [1, 2, 3, 4, 5]

const firstItem = ([x]) => x

firstItem(array) //returns 1
```

Return everything except the first item in an array:
```
const lastItem = ([x, ...x]) => x

lastItem(array) // returns 2,3,4,5
```

Do something to every element in an array as a copy of the original array (similar to foreach and ng-repeat, but follows principle of immutability)

Add an extra 2% to the cost of a home
```
const homesForSale = [
	{"id": 1, "price": 132000},
	{"id": 2, "price": 246089},
	{"id": 3, "price": 357420},
	{"id": 4, "price": 89000},
	{"id": 5, "price": 125690},
]

var newPrices = homesForSale.map(h => {
	h.price = h.price + (h.price * 0.2)
})
```

Get homes that are less than $200,000
`var cheapHomes = homesForSale.filter(h => h.price < 200000)`
