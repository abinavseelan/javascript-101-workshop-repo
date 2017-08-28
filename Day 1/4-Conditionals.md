# Conditionals

Javascript conditional statements are:

- `if...else`
- `switch`
- The ternary operator `? :`

## If...Else

The if...else construct functions just like any other programming language - an expression is evaluated and
if the expression is truthy, then you run the `if` block and if it's falsely, you run the `else` block.

```javascript
var a = 10;

if (a === 10) {
    console.log('It's true');
} else {
    console.log('It's false');
}
```

# Task

What would be the output here? :smile:

```javascript
var a;
var b = null;
var c = 0;
var d = 10;

if (a) {
    console.log('Its true');
} else {
    console.log('Its false');
}

if (b) {
    console.log('Its true');
} else {
    console.log('Its false');
}

if (c) {
    console.log('Its true');
} else {
    console.log('Its false');
}

if (d) {
    console.log('Its true');
} else {
    console.log('Its false');
}
```

## The switch statements

The switch statement is a more intricate `if...else` statement. A switch statement takes a value, and has
`case`s that handle the different forms of the value.

For example,

```javascript
var a = 10;

switch(a) {
    case 1: {
        console.log('The value is 1');
        break;
    }

    case 2: {
        console.log('The value is 2');
        break;
    }

    ...

    case 100: {
        console.log('The value is 100');
        break;
    }

    default: {
        console.log('The value is not between 1 and 100');
    }
}
```

All `switch`s *should* have a `default` case in the end, which is like the last `else` in a `if...else if..else` ladder. The `break` statement is necessary to stop execution within the given the case. If a `break` is not giving, execution will be carried forward to the next `case`. 

In Javascript, the `case` can evaluate a value of any type.

### Task

1. Create a switch case that will handle the different types of values.
2. A variable `a` can take values 1 to 10. Create a switch case wherein if you pass an odd number, it should print the number, but if you pass an even number, then you must print the adjacent odd number that is less than it. For example, the value `8` should print `8 7`, while the value `7` should print only `7`

## The Ternary operator

The ternary operator is a conditional operator. While the syntax might seem odd at first, it is actually very handy while evaluating conditions **within** other statments, like `return`.

```javascript
var a = 10;
var b = a === 10 ? 5 : 7;

console.log(b); // 5
```