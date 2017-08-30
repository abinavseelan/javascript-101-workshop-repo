# The Javascript Event Loop

Javascript is run by the Javascript Engine. The Engine's responsibilty is to go through all the lines of code, one at a time, and execute them.

What that means is that the language is *single threaded*, ie, only one thread is executing the program. 

But wait? Doesn't that mean that if there is a line of code that takes a loooonnnggg time to execute or has a sleep state linked to it, then the execution would be *blocked*?

Let's highlight this with an example.

Javascript comes with an function to *sleep* called `setTimeout()`. The `setTimeout` method takes a function to execute as the first argument, and the time to wait as the second.

```javascript
setTimeout(() => {
    console.log('Hi');
}, 5000);
```

Now, given what we just learnt above, what would the following output be?


```javascript
console.log("This should print first");

setTimeout(() => {
    console.log("This should print second");
}, 5000);

console.log("This should print third");
```

--

You'll actually find that the output is

```javascript
This should print first
This should print third
This should print second
```

Woah! Wait. What happened?

And this is where the *Javascript Event Loop* fits in. While the Javascript Engine executes the actual code, it is not the only entity involved in the execution process.

## The Moving Parts

The Javascript Engine uses what's called a *Call Stack* to a line of code at a time to execute. Any time it finds a line of code, it adds it to the call stack and the line gets executed.

Since the Engine runs within an environment, like the Browser, it also has access to other entities provided by the Browser, called Web APIs. These Web APIs run in their own threads. An example of Web APIs would be network request (XMLHTTPRequest) or the sleep method.

When the call stack runs into a line of code that requires a Web API to function, it offloads the responsibility of execution to the Web API. Once done, it removes the line of code from the call stack, and execution for the javascript code can continue in a *non-blocking* way.

Once the Web API completes its execution, it pushes the deferred execution, usually a callback provided to the method calling the Web API, like `setTimeout`, into something called the *Callback Queue*.

Once the Call Stack is empty, the callbacks in the callback queue are then pushed into the stack to execute.

The above is illustrated in gif below. (Courtesy: http://cek.io/blog/2015/12/03/event-loop/)

![event loop](http://cek.io/images/event-loop/loupe.gif)

### Task

What is the output of the following :robot:

1. 

```javascript
console.log("one");

setTimeout(() => {
    console.log("two");
}, 5000);

setTimeout(() => {
    console.log("three");
}, 2000);

console.log("four");
```

2. 
```javascript
console.log("one");

setTimeout(() => {
    console.log("two");
}, 5000);

setTimeout(() => {
    console.log("three");
}, 0);

console.log("four");
```

3.
```javascript
console.log("one");

setTimeout(() => {
    console.log("two");
}, 0);

setTimeout(() => {
    console.log("three");
}, 0);

console.log("four");
```

4.
```javascript
console.log("one");

setTimeout(() => {
    console.log("two")
    setTimeout(() => {
        console.log("three");
    }, 5000);
}, 5000);

setTimeout(() => {
    console.log("four");
}, 10000);

console.log("five");
```

