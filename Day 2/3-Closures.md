# Closures

Closures are a very misunderstood topic. Rather than defining what a closure is, I'll actually explain what happens when a closure is created.

Let's say we have a function A that some variables defined within it's scope.

```javascript
function A() {
    let a = 10;
    let b = 20;
}
```

Now let's create a new nested function within `A`.

```javascript
function A() {
    let a = 10;
    let b = 20;

    function B() {
        
    }

    B();
}
```

Now, because of scope chaining, we do have access to `a` and `b` within function `B`.

```javascript
function A() {
    let a = 10;
    let b = 20;

    function B() {
        console.log(a + b);
    }

    B(): // This will print 30
}
```

All this is well and good. But remember how functions are first-class citizens of the language. What that means is that we *can* return the function.


```javascript
function A() {
    let a = 10;
    let b = 20;

    let B = function () {
        console.log(a + b);
    }

    return B;
}
```

And a usage of this would be

```javascript
function A() {
    let a = 10;
    let b = 20;

    let B = function () {
        console.log(a + b);
    }

    return B;
}

let thisWillHoldTheReturnedFunction = A();

thisWillHoldTheReturnedFunction(); // This will execute the nested function.
```

What's the output? It's still `30`!

But how's that possible, how does the function `thisWillHoldTheReturnedFunction` have access to `a` and `b`.

And this is what a closure is. When a function has access to variables outside it's immediate scope, it creates a *Closure* over that scope.

## Function Currying

Remember math, where we can do `f(g(x))`. Is would evaluate from inside to outside, `x` followed by `g(x)`, then `f(g(x))`

The same can be done in Javascript, and we've actually seen that in the above section. Returning an instance of a function and executing it through another variable.

To give you an example of currying

```javascript
function f(x) {
    return function(y) {
        return x + y;
    }
}

// One way we can perform the function currying is

f(10)(20); // returns 30;

//or 

let returnedFunction = f(10);
returnedFunction(20); // returns 30;
```

A really good use case for function currying will be highlighted by the following tasks :smile:

### Task

1. Use function currying to create an `Adder`. For example, `Add5(10)` will return 15, and `Add10(10)` will return 20;

2. Create a Prime number checker. `Prime(10)` should return `false`. `Prime(7)` should return `true`. Once done, create a means to reduce execution time for the function if the same execution is being carried out multiple times.

For example, if I run `Prime(10)`, it should return `false` after performing some execution. Now, if I run `Prime(10)` again, it should have *prior* knowledge of the previous execution and return `false` immediately!