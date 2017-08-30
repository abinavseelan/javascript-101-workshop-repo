# Immediately Invoked Function Expressions (IIFE)

As we've seen on Day 1, any time a function is created, it generates a new scope. This is sometimes very useful to prevent the bleeding the scope. For example, if you define a variable in the global scope, and you use this file in a shared environment, you might end up with scope bleeding out and end up with some unintended side-effects.

A way to combat this is by creating an *Immediately Invoked Function Express*. At a barebones level, it's just nesting all of your content that you want encapsulated within a function that is immediately invoked.

```javascript
(function() {
    console.log("This is within an IIFE");
})();
```

There are some cases were an IIFE is necessary. This will be highlighted with the next task. :smile:

### Task

Build a function that would print the numbers 1 to `n`, where `n` is passed as a parameter. The printing of the numbers should happen after 10 seconds.

*Hint*: You might need to keep the event loops, closures and IIFEs in mind here