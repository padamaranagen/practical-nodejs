## Chapter 1 : Setting up Node.js and other Essentials

### Node.js Basics and Syntax

Node.js was built on top of the Google Chrome V8 engine and its ECMAScript, which means most of the Node.js 
syntax is similar to front-end JavaScript (another implementation of ECMAScript), including objects, functions,
and methods.

* Loose typing
* Buffer—Node.js super data type
* Object literal notation
* Functions
* Arrays
* Prototypal nature
* Conventions

#### Loose Typing

Automatic typecasting works well most of the time. It’s a great feature that saves a lot of time and mental energy!
There are only a few types of primitives:
* String
* Number (both integer and real)
* Boolean
* Undefined
* Null
* RegExp

```
'a' === new String('a') //false
but
'a' === new String('a').toString() //true
or
'a' == new String('a') //true
```
By the way, == performs automatic typecasting whereas === does not.

#### Buffer—Node.js Super Data Type

Node.js tries to use buffers any time it can, such as when reading from file systems and when receiving packets
over the network.

#### Object Literal Notation

Object notation is super readable and compact:

```
var obj = {
color: "green",
type: "suv",
owner: {
...
}
}
```
Remember, functions are objects:

```
var obj = function () {
this.color: "green",
this.type: "suv",
this.owner: {
...
}
}
```
#### Functions

In Node.js (as well as in JavaScript), functions are first-class citizens, and we treat them as variables, because they are
objects! Yes, functions can even have properties/attributes

	##### Define/Create a Function
	
	The three most common ways to define/create a function are to use a named expression, an anonymous expression
	assigned to a variable, or both.

	* named expression

	```
	function f () {
		console.log('Hi,Nagendra');
		return true;
	}
	```

	* anonymous expression
	
	```
	var f = function f () {
		console.log('Hi');
		return true;
	}
	```
	* functions are just objects that can be invoked/initialized

	```
	var f = function () 
	{
		console.log('Welcome');
	}
	f.welcome = 1;
	f(); //outputs Welcome
	console.log(f.welcome); //outputs 1
	```

	```
	Note: The return keyword is optional. When it is omitted, the function returns undefined on invocation.
	```

#### Arrays
#### Prototypal nature
#### Conventions





