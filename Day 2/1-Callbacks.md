# Callbacks

As we learnt on Day 1, Functions are first class citizens of Javascript. And this stems from the fact that they are objects.

What this means is that functions, like any other value, can be passed into another function as a *parameter*. These kind of functions are called *higher-order functions* or more commmonly known as *callback functions*.

These callback functions are taken in as parameter, and can be executed inside the function body.

```javascript
let cb = () => {
    console.log("This is from the callback function");
}

function A(cb) {
    ... // some execution which is A specific can occur here.

    cb(); // This will execute the callback function
}
```

This pattern is extensively used in libraries like JQuery, and in frameworks like ExpressJS.