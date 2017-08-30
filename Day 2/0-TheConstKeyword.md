# Constants in Javascript

Prior to ES6, defining a constant value in Javascript was not an easy task. However, with the inclusion of the `const` keyword, we can now define immutable values (constants), the same way we define variables.

```javascript
let a = 10; // This is a variable

const b = 10; // This is a constant
```

### Task

1. Create a constant `const b = 10` and try modifiying the value.
2. Try the following

```javascript
const a = {
    "hello": "world"
}

a["foo"] = "bar";
```

-- 

You'll actually notice that Task 2 is a valid operation! :scream:

That is because I might have lied in the beginning. `const` does not create immutable values, it creates immutable `bindings`. What that means is that whatever data location is bound to the variable cannot be altered.