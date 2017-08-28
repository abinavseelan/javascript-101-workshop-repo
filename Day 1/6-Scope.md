# Scope in Javascript

A *scope* is an area where a certain variable is relevant and where the variable exists. Javascript has two main scopes (three with the introduction of `let`) - function scope and global scope.

Variables declared within the *global* scope are available everywhere in the program. But whenever a variable is declared *within* a function, it gets added to the function scope. 

```javascript
var a = 10; // global

function A() {
    var b = 10; // function scope
}
```

If a variable of the same name as a global variable can be declared within the function scope. Any references to this variable will only reference the *function* scoped variable.

```javascript
var a = 10;

function A() {
    var a = 30;
    console.log(a); // 30;
}
```

*Function* scopes can be nested.

```javascript
var a = 10; // declared in the global scope

function A() {
    var a = 20; // declared in a function scope
    var B = function() {
        var a = 30; // declared in a new function scope
        console.log(a); // 30;
    }
    console.log(a); // 20;
}

console.log(a); // 10
```

## Scope chaining

In Javascript, when a variable is referenced and the variable does not exist within a given scope, it will check it the outer scope. For example,


```javascript
var a = 10;

function A(){
    console.log(a); // `a` does not exist inside the function scope, so javascript will look in the outer scope - global scope.
}
```

This is called *scope chaining*. 

### Task

What is the output of this? :smile:


```javascript
var a = 10;

function A() {
    var b = 20;
    var B = function() {
        var c = 30;
        console.log(a);
        console.log(b);
        console.log(c);
    }

    console.log(a);
    console.log(b);
    console.log(c);
}

console.log(a);
console.log(b);
console.log(c);
```

## Variable hoisting

Variable hoisting is a big gotcha in Javascript. Let's start of with a task to understand what this is.

### Task

What will this output? :robot:

```javascript
var a = 10;

function A() {
    console.log(a);
}
```

and what will this output?

```javascript
var a = 10;

function A() {
    console.log(a);
    var a = 10;
    console.log(a);
}
```

--
When a `var` declaration exists within a function body, regardless of its position in the body, will be *hoisted* to the top. The reason this happens is because of the way the Javascript compiler works. We can get to this at a later date. But just know that

```javascript
var a = 10;

function A() {
    console.log(a);
    var a = 10;
    console.log(a);
}
```

will, at a high level, be read as this by the javascript compiler

```javascript
var a = 10;

function A() {
    var a;
    console.log(a);
    a = 10;
    console.log(a);
}
```