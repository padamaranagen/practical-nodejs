## Chapter 1 : Setting up Node.js and other Essentials

## Node.js Basics and Syntax

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

	##### Pass Functions as Parameters

	JavaScript treats functions like any other objects, so we can pass them to other functions as parameters (usually,
	callbacks in Node.js):

	```
	var convertNum = function (num) {
		return num + 10;
	}
	var processNum = function (num, fn) {
		return fn(num);
	}
	processNum(10, convertNum);
	```

	##### Function Invocation vs. Expression
	The function definition is as follows:
	```
	function f () {};
	```
	On the other hand, the function invocation looks like
	```
	f();
	```
	Expression, because it resolves to some value (which could be a number, string, object, or boolean), is as follows:
	```
	function f() {return false;}
	f();
	```
	A statement looks like
	```
	function f(a) {console.log(a);}
	```

#### Arrays

Arrays are also objects that have some special methods inherited from the Array.prototype global object.
var arr = [];
var arr2 = [1, "Hi", {a:2}, function () {console.log('welcome');}];
var arr3 = new Array();
var arr4 = new Array(1,"Hi", {a:2}, function () {console.log('welcome');});

#### Prototypal nature

There are no classes in JavaScript because objects inherit directly from other objects, which is called prototypal
inheritance. There are a few types of inheritance patterns in JavaScript:
* Classical
* Pseudoclassical
* Functional

This is an example of the functional inheritance pattern:
```
var user = function (ops) 
{
	return { 
	firstName: ops.name || 'Nagendra', 
	lastName: ops.name || 'Reddy', 
	email: ops.email || 'nagendra@test.com', 
	name: function() { return this.firstName + this.lastName}
	}
}
var agency = function(ops) 
{
	ops = ops || {}
	var agency = user(ops)
	agency.customers = ops.customers || 0
	agency.isAgency = true
	return agency
}
```
#### Conventions

It’s important to follow the most common language conventions.

* Semicolons
* camelCase
* Naming
* Commas
* Indentations
* Whitespace

These JavaScript/Node.js conventions (with semicolons being an exception) are stylistic and highly preferential.
They don’t impact the execution; however, it’s strongly suggested that you follow one style consistently, especially if
you are a developer working in teams and/or on open-source projects. Some open-source projects might not accept
pull requests if they contain semicolons (e.g., NPM) or if they don’t use comma-first style (e.g., request).

	##### Commas
	An example of a comma-first approach is as follows:
	var obj = { firstName: "John"
			, lastName: "Smith"
			, email: "johnsmith@gmail.com"
		}

## Node.js Process Information

process information in code with the process object
C:\practical-nodejs>node -e "console.log(process.pid)"
1908

## Node.js Core Modules

Node.js doesn’t come with a heavy standard library. 

The main core modules, classes,
methods, and events include the following:
* [http] (http://nodejs.org/api/http.html#http_http)
* [util] (http://nodejs.org/api/util.html)
* [querystring] (http://nodejs.org/api/querystring.html)
* [url] (http://nodejs.org/api/url.html)
* [fs] (http://nodejs.org/api/fs.html)


### [http] (http://nodejs.org/api/http.html)

http is the main module responsible for the Node.js HTTP server. The main methods are as follows:

```
• http.createServer(): returns a new web server object
• http.listen(): begins accepting connections on the specified port and hostname
• http.createClient(): is a client and makes requests to other servers
• http.ServerRequest(): passes incoming requests to request handlers
	• data: emitted when a part of the message body is received
	• end: emitted exactly once for each request
	• request.method(): the request method as a string
	• request.url(): request URL string
• http.ServerResponse(): creates this object internally by an HTTP server — not by
the user— and is used as an output of request handlers
	• response.writeHead(): sends a response header to the request
	• response.write(): sends a response body
	• response.end(): sends and ends a response body
```

### [util] (http://nodejs.org/api/util.html)

The util module provides utilities for debugging. One method is as follows:
```
• util.inspect(): returns a string representation of an object, which is useful for debugging
```

### [querystring] (http://nodejs.org/api/querystring.html)

The querystring module provides utilities for dealing with query strings. Some of the methods include the following:
```
• querystring.stringify(): serializes an object to a query string
• querystring.parse(): deserializes a query string to an object
```

### [url] (http://nodejs.org/api/url.html)

The url module has utilities for URL resolution and parsing. One method is as follows:
```
• parse(): takes a URL string and returns an object
```

### [fs] (http://nodejs.org/api/fs.html)
fs handles file system operations such as reading to and writing from files. There are synchronous and asynchronous
methods in the library. Some of the methods include the following:
• fs.readFile(): reads files asynchronously
• fs.writeFile(): writes data to files asynchronously
There is no need to install or download core modules. To include them in your application, all you need is to use
the following syntax:
var http = require('http');


## Handy Node.js Utilities

Although the core of the Node.js platform was, intentionally, kept small, it has some essential utilities, including
the following:
```
• Crypto(http://nodejs.org/api/crypto.html): has randomizer, MD5, HMAC-SHA1, and
other algorithms
• Path(http://nodejs.org/api/path.html): handles system paths
• String decoder(http://nodejs.org/api/string_decoder.html): decodes to and from buffer and string types
The method we use throughout is path.join and it concatenates the path using an appropriate folder separator (/ or \\).
```

## Reading to and Writing from the File System in Node.js

Reading from files is done via the core fs module (http://nodejs.org/api/fs.html). There are two sets of reading
methods: async and sync. In most cases, developers should use async methods, such as fs.readFile:

```
var fs = require('fs');
var path = require('path');
fs.readFile(path.join(__dirname, '/data/customers.csv'), {encoding: 'utf-8'}, function (err, data) {
	if (err) throw err;
	console.log(data);
});
```
To write to the file, execute the following:
```
var fs = require('fs');
fs.writeFile('message.txt', 'Hello World!', function (err) {
	if (err) throw err;
	console.log('Writing is done.');
});
```

## Streaming Data in Node.js

Streaming data is a phrase that means an application processes the data while it’s still receiving it. This feature is
useful for extra large datasets such as video or database migrations.
Here’s a basic example of using streams that output the binary file content back:
```
var fs = require('fs');
fs.createReadStream('./data/customers.csv').pipe(process.stdout);
```
By default, Node.js uses buffers for streams. For more immersive instruction, take a look at [stream-adventure] (http://npmjs.org/stream-adventure)

## Hello World Server with HTTP Node.js Module

```
var http = require('http'); 
http.createServer(function (req, res) {//creates a server with a callback function which contains the response handler code
res.writeHead(200, {'Content-Type': 'text/plain'});//set the right header and status code
res.end('Hello World\n'); //output Hello World
}).listen(3000, '127.0.0.1');
console.log('Server running at http://127.0.0.1:3000/');

launch in your terminal/cmd the following command
node server.js
```


## Debugging Node.js Programs

Step 1: Install npm inspector utility
```
npm install -g node-inspector
```
Step 2: Create a server file called server.js
```
var express=require('express');
var app=express();
app.use(express.static(__dirname+"/public"));	
app.listen(process.env.PORT || 3000)
```
Step 3: Start the server using the below
C:\angularjs-sample-website>node --debug-brk server.js
Debugger listening on port 5858

Step 4: Open another terminal then type node-inspector
C:\angularjs-sample-website>node-inspector
Node Inspector v0.12.8
Visit http://127.0.0.1:8080/?port=5858 to start debugging.

Step 5: Open the above link to start debugging

