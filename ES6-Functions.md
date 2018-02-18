---
title: ES6 - Functions
description: Grow with Google Scholarship Challenge - Mobile Web Track
---
<!-- markdownlint-disable MD022 MD024 MD032 -->
# Lesson 2: Functions
Notes from _**Lesson 2: Functions**_ of _**ES6 JavaScript Improved**_ by Richard Kalehoff and James Parkes. This class is part of the Udacity course [ES6 - JavaScript Improved](https://www.udacity.com/course/es6-javascript-improved--ud356)

This is an Intermediate skill level course which takes approximately 4 weeks to complete and is offered for **FREE**!

| Lesson 1 | Lesson 2 | Lesson 3 | Lesson 4 |
| --- | --- | --- | --- |
| [Syntax](ES6-Syntax.html) | **Functions** | [Built-ins](ES6-Built-ins.html) | [Professional Developer-fu](ES6-Professional-Developer-fu.html) |

## 1. Updates to Functions
In this lesson we're going to cover updates to functions in es6. Functions have changed a lot since the last version of JavaScript. We've now got a new way to write functions called arrow functions ( `name => name.toUpperCase()` ) and a new `class` keyword that lets you create functions as classes ( `class Cone { }` ).

That's not all. In es6 you can now set up default function parameters plus you can connect different classes together using the new `super` and `extends` keywords.

```js
class MintCode extends Cone {
  constructor(data) {
    super(data);
      this.flavor = 'Mint';
  }
}
```

The first thing we'll look at is arrow functions.

## 2. Arrow Functions
Functions are one of the primary data structures in JavaScript; they've been around _forever_.

### Arrow functions
ES6 introduces a new kind of function called the **arrow function**. Arrow functions are very similar to regular functions in behavior, but are quite different syntactically. The following code takes a list of names and converts each one to uppercase using a regular function:

```js
const upperizedNames = ['Farrin', 'Kagure', 'Asser'].map(function(name) {
  return name.toUpperCase();
});
```

The code below does the same thing except instead of passing a regular function to the `map()` method, it passes an arrow function. Notice the arrow in the arrow function ( `=>` ) in the code below:

```js
const upperizedNames = ['Farrin', 'Kagure', 'Asser'].map(
  name => name.toUpperCase()
);
```

The only change to the code above is the code inside the map() method. It takes a regular function and changes it to use an arrow function.

> **NOTE:** Not sure how `map()` works? It's a method on the Array prototype. You pass a function to it, and it calls that function once on every element in the array. It then gathers the returned values from each function call and makes a new array with those results. For more info, check out [MDN's documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map).

### Convert a function to an arrow function

```js
const upperizedNames = ['Farrin', 'Kagure', 'Asser'].map(function(name) {
  return name.toUpperCase();
});
```

1. remove the `function` keyword
1. remove the parentheses
1. remove the opening and closing curly braces
1. remove the `return` keyword
1. remove the semicolon
1. add an arrow ( `=>` ) between the parameter list and the function body

```js
// es5
const upperizedNames = ['Farrin', 'Kagure', 'Asser']
  .map(function(name) {
    return name.toUpperCase();
  });

// es6
const upperizedNames = ['Farrin', 'Kagure', 'Asser']
  .map( name => name.toUpperCase() );
```

#### Quiz Question
Take a look at the following code:

```js
const names = ['Afghanistan', 'Aruba', 'Bahamas', 'Chile', 'Fiji', 'Gabon',
                'Luxembourg', 'Nepal', 'Singapore', 'Uganda', 'Zimbabwe'];

const longNames = names.filter(function(name) {
  return name.length > 6;
});
```

Which of the following choices does the same thing, but replaces .filter()'s function with an arrow function?

1. [ ] const longNames = names.filter( function(name) => return name.length > 6; );
1. [ ] const longNames = names.filter( return name.length > 6 );
1. [ ] const longNames = names.filter( name => {names.length > 6} );
1. [ ] const longNames = names.filter( name => name.length > 6 );

#### Solution
This arrow function returns country names that are six characters or longer.

- [x] const longNames = names.filter( name => name.length > 6 );

## 3. Using Arrow Functions
Regular functions can be either **function declarations** or **function expressions**, however **arrow functions are _always_ expressions**. In fact, their full name is "arrow function expressions", so they can only be used where an expression is valid. This includes being:

- stored in a variable,
- passed as an argument to a function,
- and stored in an object's property.

One confusing syntax is when an arrow function is stored in a variable.

```js
const greet = name => `Hello ${name}!`;
```

In the code above, the arrow function is stored in the `greet` variable and you'd call it like this:

```js
greet('James');
```

> **Returns:** Hello James!

### Parentheses and arrow function parameters
You might have noticed the arrow function from the greet() function looks like this:

```js
name => `Hello ${name}!`
```

If you recall, the parameter list appears before the arrow function's arrow (i.e. `=>`). If there's only **one** parameter in the list, then you can write it just like the example above. But, if there are **two or more** items in the parameter list, or if there are **zero** items in the list, then you need to wrap the list in parentheses:

```js
// empty parameter list requires parentheses
const sayHi = () => console.log('Hello Udacity Student!');
sayHi();
```

> **Prints:** Hello Udacity Student!

```js
// multiple parameters requires parentheses
const orderIceCream = (flavor, cone) => console.log(`Here's your ${flavor} ice cream in a ${cone} cone.`);
orderIceCream('chocolate', 'waffle');
```

> **Prints:** Here's your chocolate ice cream in a waffle cone.

#### Question 1 of 2
Which of the following choices have correctly formatted arrow functions?

1. [ ]
```js
setTimeout(() => {
  console.log('starting the test');
  test.start();
}, 2000);
```

1. [ ]
```js
setTimeout( _ => {
  console.log('starting the test');
  test.start();
}, 2000);
```

1. [ ]
```js
const vowels = 'aeiou'.split('');
const bigVowels = vowels.map( (letter) => letter.toUpperCase() );
```

1. [ ]
```js
const vowels = 'aeiou'.split('');
const bigVowels = vowels.map( letter => letter.toUpperCase() );
```

#### Solution
Actually, each one of these is correct.

1. [x] setTimeout(**()** => {
1. [x] setTimeout( **_** => {
1. [x] const bigVowels = vowels.map( **(letter)** => letter.toUpperCase() );
1. [x] const bigVowels = vowels.map( **letter** => letter.toUpperCase() );

If there's no parameter to the function, you just use a pair of empty parentheses like option 1.

Alternatively, some developers choose to use an underscore as their single parameter. The underscore never gets used, so it's `undefined` inside the function, but it's a common technique.

The only difference between options 3 and 4 is the use of the parentheses around `letter`. Typically, if there's only one parameter, then no parentheses are used, but it's not wrong.

### Concise and block body syntax
All of the arrow functions we've been looking at have only had a single expression as the function body:

```js
const upperizedNames = ['Farrin', 'Kagure', 'Asser'].map(
  name => name.toUpperCase()
);
```

This format of the function body is called the _"concise body syntax"_. The concise syntax:

- has no curly braces surrounding the function body
- and automatically returns the expression.

If you need more than just a single line of code in your arrow function's body, then you can use the _"block body syntax"_.

```js
const upperizedNames = ['Farrin', 'Kagure', 'Asser'].map( name => {
  name = name.toUpperCase();
  return `${name} has ${name.length} characters in their name`;
});
```

Important things to keep in mind with the block syntax:

it uses curly braces to wrap the function body
and a `return` statement needs to be used to actually return something from the function.

#### Question 2 of 2
Using your knowledge of how arrow functions work with automatic returns and curly braces, which of the following choices have correctly formatted arrow functions?

1. [ ]
```js
const colors = ['red', 'blue', 'yellow', 'orange', 'black'];
const crazyColors = color.map( color => {
  const jumble = color.split('').reverse();
  return jumble.join('') + '!';
});
```

1. [ ]
```js
const colors = ['red', 'blue', 'yellow', 'orange', 'black'];
const crazyColors = color.map( color => {
  color.split('').reverse().join('') + '!';
});
```

1. [ ]
```js
const colors = ['red', 'blue', 'yellow', 'orange', 'black'];
const crazyColors = color.map( color => return color.split('').reverse().join('') + '!' );
```

1. [ ]
```js
const colors = ['red', 'blue', 'yellow', 'orange', 'black'];
const crazyColors = color.map( color => color.split('').reverse().join('') + '!' );
```

#### Solution
Options 1 and 4 both use correct syntax for arrow functions.

1. [x] Option 1 is correct. Because the arrow function uses curly braces, there has to be a `return` in there somewhere for something to actually be returned.
1. [ ] Option 2 is not correct because it has curly braces and no `return`. This function runs, but nothing gets returned to crazyColors.
1. [ ] Option 3 doesn't have curly braces. This means it needs to be in the concise syntax and automatically return the expression so it should not have a `return` keyword, so this one isn't correct.
1. [x] Option 4 is correct. This is the most common way you'll see arrow functions written—as one-liners that automatically return.

So arrow functions are awesome!

- The syntax is a lot shorter,
- it's easier to write and read short, single-line functions,
- and they automatically return when using the concise body syntax!

> **WARNING:** Everything's not all ponies and rainbows though, and there are definitely times when you might not want to use an arrow function. So before you wipe from your memory how to write a traditional function, check out these implications:
>
> - there's a gotcha with the `this` keyword in arrow functions
>   - go to the next lesson to find out the details!
>
> - arrow functions are only _expressions_
>   - there's no such thing as an arrow function declaration

## 4. Quiz: Convert to Arrow Function
### Directions:
Convert the function passed to the map() method into an arrow function.

#### Code

```js
/*
 * Programming Quiz: Convert Function into an Arrow Function (2-1)
 */

// convert to an arrow function
const squares = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10].map(function(square) {
  return square * square;
});

console.log(...squares);
```

#### Solution

```js
/*
 * Programming Quiz: Convert Function into an Arrow Function (2-1)
 */

// convert to an arrow function
const squares = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10].map(square => square * square);

console.log(...squares);
```

## 5. Arrow Functions Recap
Arrow functions are awesome and can really clean up your code by removing:

- the `function` keyword
- the `return` keyword
- curly braces ( `{}` )

But don't go converting all functions into arrow functions just yet because there's a big gotcha with arrow functions.

The way arrow functions handle the `this` keyword is different from regular functions.

## 6. Arrow Functions and 'this' Keyword
`this` can be pretty confusing since it's a dynamic value that's different depending on how a function is called.

With regular functions the value of `this` depends on how the function is called.

With arrow functions it depends on where that function is located in the code.

We'll briefly review how the `this` keyword works in general and then we'll review how it works in arrow functions.