# Operators in Javascript

## Numeric operators

Javascript supports the following numeric operators

- `+` (Addition)
- `-` (Subtraction)
- `*` (Multiplication)
- `/` (Division)
- `%` (Modulus)

```javascript
var a = 10;

a = 10 + 5; // 15
a = 10 - 5; // 5
a = 10 * 5; // 50
a = 10 / 5; // 2
a = 10 % 5; // 0
```

These operators are evaluated following the BODMAS rule.

## Assignment

The `=` operator is also an operator. This operator is used to assign a value to a variable.

```javascript
var a = 10;
```

This operator is evaluated right to left.

```javascript
var a = b = c = 10;
```

This will evaluate `c = 10` first, followed by `b = 10` and then finally `a = 10`. But wait? How does `b = 10` actually work after we do `c = 10`. 

That's because the assignment operation *actually* returns a value. It returns the value that is being assigned. `c = 10` returns `10`, which leaves the expression as `a = b = 10`. Now the same goes for `b`. :smile:

## Unary

An operator is unary if it has a single operand. For example,

```javascript
var a = 10;

a = a++; // 11
a = a--; // 10;
a = ++a; // 11;
a = -a; // -11;
```


## String Concatenation

The `+` operator can be used for String concatenation

```javascript
var a = "Hello " + "World";

console.log(a); // Hello World
```

## Comparison

Javascript supports the following comparison operators:

- `>` & `>=` (greater than | greater than and equal to)
- `<` & `<=` (less than | less than and equal to)
- `==` & `!=` (Equal to | Not Equal to)
- `===` & `!==` (Equal to and checks same type | Not Equal to and checks same type)

These operators return either `true` or `false` based on whether the condition is satisfied or not satisfied

```javascript
var a = 5;
var b = 10;

a > b; // false
a < b; // true
a == 5; // true
b != 5; // true
```

### Task

What would be the output of the following?

```javascript
var a = 5;

a == '5'; // ?
a === '5'; // ?
```

--

The comparison operators can also be used with strings. Strings can be `>` or `<` than other strings, based on a dictionary based evaluation.

While comparing different types, all types are converted to numbers.

```javascript
var a = 10;
var b = '20';

a < b; // true

```

### Task

What do you think is the output of the following? :smile:

```javascript
let a = 0;
console.log( Boolean(a) ); 

let b = "0";
console.log( Boolean(b) );

console.log(a == b);
```

--

`null` and `undefined` are very notorious for creating comparison problems.

```javascript
console.log( null === undefined ); // false
console.log( null == undefined ); // true

console.log( null > 0 );  // (1) false
console.log( null == 0 ); // (2) false
console.log( null >= 0 ); // (3) true

console.log( undefined > 0 ); // false (1)
console.log( undefined < 0 ); // false (2)
console.log( undefined == 0 ); // false (3)
```

## Conditional

Javascript supports the following conditional operators:

- `&&` (AND)
- `||` (OR)
- `!` (NOT)

The conditional operators can be used to evaluate conditions. But they also have a really helpful side-effect, they return a value.

### Task

1. What do you think the following output would be? :smile:

```javascript
var a = 10 && 20;
var b = 20 || 10;
var c = 0 && 10;
var d = 0 || 10;

console.log(a);
console.log(b);
console.log(c);
console.log(d);
```

2. Hmm. And what about this? :smile:

```javascript
var a = !5;
var b = !0;
var c = !!5;
var d = !!0;

console.log(a);
console.log(b);
console.log(c);
console.log(d);
```
