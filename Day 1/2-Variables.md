# Variables in Javascript

Variables are *named values*. Going back to algebra, the statement `x = 5` would mean that any instance of you writing `x`, such as in `x + 10`, the `x` would carry the value 5, evaluating `x + 10` to 15.

Variables in Javascript are defined using the `var` keyword. Post ES6, we now use `let` keyword to define variables.

```javascript
// ES5

var x = 5;

// ES6

let x = 5;
```

The `var` and `let` keywords function more or less the same way. However, there are some subtle differences between them that are actually very important to know. We will get to those differences later. For now, they both create variables :smile:

## Javascript - A dynamically typed language

Javascript is a dynamically typed language. In strongly typed languages like C or Java, you would be required to specify two things while creating a variable - the value the variable is going to store **and** the type of value the variable is storing.

For example, in the C programming language, if you needed to store a integer in a variable, you would create the variable like this,

```C
int a = 10;
```

and if you wanted to store a decimal number, you would create it like this

```C
float a = 10.5;
```

In Javascript, there is no such requirement. The `let` keyword can be used to hold any *type* of value.

```javascript
let a = 10;
let b = 10.5;
let c = "Hola Amigo!";
```

## Types

Although Javascript does not have typed variables, like `int a`, it does have typed values. What that means is the a value stored in a variable can be of the following types:

- number (A numeric value like 10 or 5.5)
- boolean (A conditional value like true or false)
- string (A character value like "Hey")
- object (An aggregate value of properties and values)
- undefined (An undefined value)

Javascript has a `typeof` operator. You can use the `typeof` operator to find out the type of value a variable holds

```javascript
var a;

console.log(a); // undefined

a = 10;
console.log(typeof a); // number

a = 'Hello World!';
console.log(typeof a); // string

a = true;
console.log(typeof a); // boolean

a = {
    property1: value1,
    property2: value2
};

console.log(typeof a); // object
```

## Other types

The types listed above are pure types. However, there are some abstract types that we as programmers will have to use, that are just modifications of the `object` type

### Objects

An `object` is a collection of properties and their values. A property is a named location that you can store values in.

For example,

```javascript
var a = {
    b: 10,
    c: 20,
    d: "Hey!"
};
```

To access the value stored in these properties, you use the `.` notation. 

```javascript
var a = {
    b: 10,
    c: 20,
    d: "Hey!"
};

a.b; // 10
a.c // 20
a.d // "Hey!"
```

Object properties can be objects themselves.

```javascript
var a = {
    b: 10,
    c: 20,
    d: {
        e: 50,
        f: 60
    }
}

a.d.e; // 50
a.d.f; // 60
```

Object properties' values can also be accessed via the *bracket* notation, `a["b"] // 10`

### Arrays

Arrays are slightly different from Objects. Unlike Objects, Arrays do not have properties, but instead store the values in numericaly indexed positions, starting from 0.

To create an Array

```javascript
var a = [10, 20, 30, 40, 50];

a[0]; // 10
a[1]; // 20
a[2]; // 30
```

### Functions

Functions in Javascript are of type `object` as well. However, there is a small variation here. The `typeof` operator will return type `function` for a function. That is because functions are a subset of the `object` type. All functions are objects.

```javascript
function a () {
    var b = 10;
}

console.log(a); // [Function a]

a.b = 10;

console.log(a); // { [Function a], b:10 }
```

## Coercion

Coercion is the programming paradigm of type conversion. For example, when you're trying to print a value of type `number` using `console.log()`, the value would be converted to type `string`.

Coercion in Javascript is of two types - implicit and explicit.

An example of explicit coercion

```javascript
let a = 10;

let b = String(10);

console.log(b); // "10"
typeof b; // string
typeof a; // number
```

An example of implicit coercion

```javascript
let a = "10";
let b =  a + 5; // a is coerced to number here.
```

### Task

Boolean values are `true` and `false`. Find out what `string` and `number` values coerce to `true` and which ones coerce to `false`.

## Copying variables

In javascript, you can copy a variable by just assigning a new variable to an existing variable

```javascript
var a = 10;
var b = a;

console.log(b); // 10;
```

However, copying actually is of two types - deep and shallow copy. 

### Deep Copy

Let's explain this with an example. I create a variable `a`. `a` is assigned the value `10`. Now, when I create another variable `b` and assign it `a`, then the entire value of `a` is copied over to `b`. Another changes to `b` are will not change anything in `a` since the value has been completely copies over.

```javascript
var a = 10;
var b = 10;

console.log(a); // 10
console.log(b); // 10

b = 20;

console.log(a); // 10
console.log(b); // 20
```

### Shallow Copy

Shallow copy occurs where two variables point to the same data location. For example, let's say we have a variable `a`. We assign a value of type `object` to it . The variable `a` will now point to a location in memory that houses the value. Now, when we create another variable `b` and assign it `a`, then instead of the entire value being copied over, only the reference to the data location is copied. 

### Task

What would happen here? :robot:

```javascript
var a = {
    "hello": "world"
};

var b = a;

console.log(a);
console.log(b);

b["foo"] = "bar";

console.log(a);
console.log(b);
```



