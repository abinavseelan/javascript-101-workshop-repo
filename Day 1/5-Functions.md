# Functions in Javascript

Functions are snippets of code that can invoked on demand, and can be invoked in different forms based on the input given to them. To define a function in Javascript,

```javascript
function sayHello(text) {
    console.log("Hello " + text);
}

sayHello('World'); // Hello World
sayHello('Foo'); // Hello Foo
sayHello('Bar'); // Hello Bar
```

Functions can be split into *function declaration* and *function invocation*. *Function declaration* is the stencil of what the function will do, and *function invocation* is the process of actually calling a function.

```javascript
function sayHello(text) {
    console.log("Hello " + text); // function declaration
}

sayHello('World'); // function invocation
```

Functions can have their own variables defined within them, which are local to the function (read scope, which we will get to in a bit).

Functions also have access to two more types of variables - outer variables and function parameters

```javascript
var hello = "Hello"; // outer variable
function sayHello(text) { // text is a parameter
    var whatAmIDoing = "I'm Learning JS";
    console.log(hello + text + whatAmIDoing);
}

sayHello('World'); // Hello World. I'm learning JS
```

## Passing parameters

Parameters are defined in the *function declaration* and are passed in during *function invocation*. There variables become a part of the list of variable that the function can access.

```javascript
function A(a, b) { // a and b are parameters
    ...
}

A(10, 20); // 10 and 20 are the actual parameters passed into that instance of the function.
```

In Javascript, all parameters are passed in by *value*. That means that any modifications to the value inside the function will be local to that function.

```javascript
var a = 10;

function A(val) { // a is passed in by value.
    val = 20; // a is modified inside the function
    console.log(val); // 20
}

A(a);

console.log(a); // 10, since the value was passed by value, aka, copied into the function.
```

**However**, if the value being passed into the function is of type `object`, then the value is passed by reference, ie, only the reference to the object is copied into the function. 

### Task

What would happen here? :robot:

```javascript
var a = {
    "hello": "world"
};

function A(obj) {
    obj["foo"] = "bar";
    console.log(obj);
}

A(a);

console.log(a);
```

## Functions are First-class citizens


Unlike other languages like C and Java, Functions in Javascript are first class citizens of the language. What that means is functions can be thrown around just like any other value, can be assigned to variables and more importantly can be passed as parameters to other functions.

```javascript
var a = function() {
    ...
}

function a() {
    ...
}

function a(param1, param2, function b() { console.log('hey');} );
```

## Arrow functions

Arrow functions were introduced in ES6. Arrow functions and regular functions work pretty much the same, but like the difference between `let` and `var`, there are some minor, but really important differences between the two, mostly to do with the *this* keyword. But let's not get to that yet.

Arrow functions are a short hand for the `function` keyword.

```javascript
var a = function() { // regular function

}

var b = () => { // arrow function

}
```

Arrow functions can be shortened even further. If there is only one argument, then the brackets are optional. If the function just *returns* a value, the the `{}` brackets are optional.

```javascript
var a = (singleParam) => {
    return true;
}
```

can be shortened to

```javascript
var a = singleParam => {
    return true;
}
```

and can be further shortened to

```javascript
var a = singleParams => true;
```
