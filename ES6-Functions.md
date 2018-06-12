---
title: ES6 - Functions
description: Grow with Google Scholarship Challenge - Mobile Web Track
---
<!-- markdownlint-disable MD022 MD024 MD032 -->

[<-- back to Mobile Web Specialist Phase 1 Notes TOC](MWS-TOC.html)

---

# Lesson 2: Functions
Notes from _**Lesson 2: Functions**_ of _**ES6 JavaScript Improved**_ by Richard Kalehoff and James Parkes. This class is part of the Udacity course [ES6 - JavaScript Improved](https://www.udacity.com/course/es6-javascript-improved--ud356)

This is an Intermediate skill level course which takes approximately 4 weeks to complete and is offered for **FREE**!

| Lesson 1 | Lesson 2 | Lesson 2.5 | Lesson 3 | Lesson 3.5 | Lesson 4 |
| --- | --- | --- | --- | --- | --- |
| [Syntax](ES6-Syntax.html) | **Functions** | [Classes](ES6-Classes.html) | [Built-ins](ES6-Built-ins.html) | [Built-ins Pt2](ES6-Built-ins-Pt2.html) | [Professional Developer-fu](ES6-Professional-Developer-fu.html) |

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

## 7. 'this' and Regular Functions
To get a handle on how `this` works differently with arrow functions, let's do a quick recap of how `this` works in a standard function.

The value of the `this` keyword is based completely on how its function (or method) is called. `this` could be any of the following:

---

### 1. A new object
If the function is called with `new`:

```js
const mySundae = new Sundae('Chocolate', ['Sprinkles', 'Hot Fudge']);
```

In the code above, the value of `this` inside the `Sundae` constructor function is a new object because it was called with `new`.

---

### 2. A specified object
If the function is invoked with `call/apply`:

```js
const result = obj1.printName.call(obj2);
```

In the code above, the value of `this` inside `printName()` will refer to `obj2` since the first parameter of `call()` is to explicitly set what `this` refers to.

---

### 3. A context object
If the function is a method of an object:

```js
data.teleport();
```

In the code above, the value of `this` inside `teleport()` will refer to the `data` object.

---

### 4. The global object or undefined
If the function is called with no context:

```js
teleport();
```

In the code above, the value of `this` inside `teleport()` is either the global object or, if in strict mode, it's `undefined`.

---

> **TIP:** this in JavaScript is a complicated topic. We just did a quick overview, but for an in-depth look at how `this` is determined, check out ['this' All Makes Sense Now!](https://github.com/getify/You-Dont-Know-JS/blob/master/this%20%26%20object%20prototypes/ch2.md) from Kyle Simpson's book series [You Don't Know JS](https://github.com/getify/You-Dont-Know-JS/blob/master/README.md).

#### Question 1 of 2
What is the value of `this` inside the `Train` constructor function below?

```js
const redTrain = new Train('red');
```

1. [ ] the `window` object
1. [ ] a new object
1. [ ] `undefined`

#### Solution
Since the new keyword was used, the correct answer is a new object.

- [x] a new object

#### Question 2 of 2
What is the value of `this` inside the `increaseSpeed()` function below?

```js
const redTrain = new Train('red');
redTrain.increaseSpeed(25);
```

1. [ ] the `window` object
1. [ ] a new object
1. [ ] the `redTrain` object
1. [ ] `undefined`

#### Solution
Since the `increaseSpeed()` function is called from a context object (`redTrain`) that context object will be the value of `this` in the function.

- [x] the `redTrain` object

## 8. 'this' and Arrow Functions
With regular functions, the value of `this` is set based on _how the function is called_. With arrow functions, the value of `this` is based on the _function's surrounding context_. In other words, the value of `this` _inside_ an arrow function is the same as the value of `this` _outside_ the function.

Let's check out an example with `this` in regular functions and then look at how arrow functions will work.

```js
// constructor
function IceCream() {
  this.scoops = 0;
}

// adds scoop to ice cream
IceCream.prototype.addScoop = function() {
  setTimeout(function() {
    this.scoops++;
    console.log('scoop added!');
  }, 500);
};

const dessert = new IceCream();
dessert.addScoop();
```

> **Prints:**<br>
> scoop added!

After running the code above, you'd _think_ that `dessert.scoops` would be 1 after half a millisecond. But, unfortunately, it's not:

```js
console.log(dessert.scoops);
```

> **Prints:**<br>
> 0

Can you tell why?

The function passed to `setTimeout()` is called without `new`, without `call()`, without `apply()`, and without a context object. That means the value of `this` inside the function is the global object and **NOT** the `dessert` object. So what actually happened was that a new `scoops` variable was created (with a default value of `undefined`) and was then incremented (`undefined + 1` results in `NaN`):

```js
console.log(scoops);
```

> **Prints:**<br>
> NaN

One way around this is to use closure:

```js
// constructor
function IceCream() {
  this.scoops = 0;
}

// adds scoop to ice cream
IceCream.prototype.addScoop = function() {
  const cone = this; // sets `this` to the `cone` variable
  setTimeout(function() {
    cone.scoops++; // references the `cone` variable
    console.log('scoop added!');
  }, 0.5);
};

const dessert = new IceCream();
dessert.addScoop();
```

The code above _will_ work because instead of using `this` inside the function, it sets the cone variable to this and then looks up the cone variable when the function is called. This works because it's using the value of the this outside the function. So if we check the number of scoops in our dessert right now, we'll see the correct value of `1`:

```js
console.log(dessert.scoops);
```

> **Prints:**<br>
> 1

Well that's exactly what arrow functions do, so let's replace the function passed to `setTimeout()` with an arrow function:

```js
// constructor
function IceCream() {
  this.scoops = 0;
}

// adds scoop to ice cream
IceCream.prototype.addScoop = function() {
  setTimeout(() => { // an arrow function is passed to setTimeout
    this.scoops++;
    console.log('scoop added!');
  }, 0.5);
};

const dessert = new IceCream();
dessert.addScoop();
```

Since arrow functions inherit their this value from the surrounding context, this code works!

```js
console.log(dessert.scoops);
```

> **Prints:**<br>
> 1

When `addScoop()` is called, the value of `this` _inside_ `addScoop()` refers to `dessert`. Since an arrow function is passed to `setTimeout()`, it's using its surrounding context to determine what `this` refers to inside itself. So since `this` _outside_ of the arrow function refers to `dessert`, the value of `this` _inside_ the arrow function will also refer to `dessert`.`

Now what do you think would happen if we changed the `addScoop()` method to an arrow function?

```js
// constructor
function IceCream() {
    this.scoops = 0;
}

// adds scoop to ice cream
IceCream.prototype.addScoop = () => { // addScoop is now an arrow function
  setTimeout(() => {
    this.scoops++;
    console.log('scoop added!');
  }, 0.5);
};

const dessert = new IceCream();
dessert.addScoop();
```

Yeah, this doesn't work for the same reason - arrow functions inherit their `this` value from their surrounding context. Outside of the `addScoop()` method, the value of `this` is the global object. So if `addScoop()` is an arrow function, the value of `this` _inside_ `addScoop()` is the global object. Which then makes the value of `this` in the function passed to `setTimeout()` also set to the global object!

## 9. Default Function Parameters
Take a look at this code:

```js
function greet(name, greeting) {
  name = (typeof name !== 'undefined') ?  name : 'Student';
  greeting = (typeof greeting !== 'undefined') ?  greeting : 'Welcome';

  return `${greeting} ${name}!`;
}

greet(); // Welcome Student!
greet('James'); // Welcome James!
greet('Richard', 'Howdy'); // Howdy Richard!
```

> **Returns:**
> Welcome Student!
> Welcome James!
> Howdy Richard!

What is all that horrible mess in the first two lines of the `greet()` function? All of that is there to provide default values for the function if the required arguments aren't provided. It's pretty ugly, though...

Fortunately, ES6 has introduced a new way to create defaults. It's called _default function parameters_.

### Default function parameters
**Default function parameters** are quite easy to read since they're placed in the function's parameter list:

```js
function greet(name = 'Student', greeting = 'Welcome') {
  return `${greeting} ${name}!`;
}

greet(); // Welcome Student!
greet('James'); // Welcome James!
greet('Richard', 'Howdy'); // Howdy Richard!
```

> **Returns:**
> Welcome Student!
> Welcome James!
> Howdy Richard!

Wow, that's a lot less code, so much cleaner, and significantly easier to read!

To create a default parameter, you add an equal sign ( `=` ) and then whatever you want the parameter to default to if an argument is not provided. In the code above, both parameters have default values of strings, but they can be any JavaScript type!

#### Quiz Question
Take a look at the following code:

```js
function shippingLabel(name, address) {
  name = (typeof name !== 'undefined') ? name : 'Richard';
  address = (typeof address !== 'undefined') ?  address : 'Mountain View';
  return `To: ${name} In: ${address}`;
}
```

Which of the following choices is the correct way to write the shippingLabel() function using default function parameters?

1. [ ]
```js
function shippingLabel(name = '', address = '') {
  return `To ${name} In: ${address}`;
}
```

1. [ ]
```js
function shippingLabel(name, address) {
  name = name || 'Richard';
  address = address || 'Mountain View';
  return `To: ${name} In: ${address}`;
}
```

1. [ ]
```js
function shippingLabel(name, address) {
  return `To: ${name} In: ${address}`;
}
```

1. [ ]
```js
function shippingLabel(name = 'Richard', address = 'Mountain View') {
  return `To: ${name} In: ${address}`;
}
```

#### Solution
Option 4 uses default function parameters correctly by setting the defaults directly to the parameters.

- [x]
```js
function shippingLabel(name = 'Richard', address = 'Mountain View') {
  return `To: ${name} In: ${address}`;
}
```

## 10. Default and Destructuring
You can combine default function parameters with [destructuring](ES6-Syntax.html#6-destructuring-arrays) to create some pretty powerful functions!

```js
function createGrid([width = 5, height = 5]) {
  return `Generates a ${width} x ${height} grid`;
}

createGrid([]); // Generates a 5 x 5 grid
createGrid([2]); // Generates a 2 x 5 grid
createGrid([2, 3]); // Generates a 2 x 3 grid
createGrid([undefined, 3]); // Generates a 5 x 3 grid
```

> **Returns:**
> Generates a 5 x 5 grid
> Generates a 2 x 5 grid
> Generates a 2 x 3 grid
> Generates a 5 x 3 grid

The `createGrid()` function expects an array to be passed to it. It uses destructuring to set the first item in the array to the `width` and the second item to be the `height`. If the array is empty or if it has only one item in it, then the default parameters kick in and give the missing parameters a default value of `5`.

There is a problem with this though, the following code will not work:

```js
createGrid(); // throws an error
```

> **Uncaught TypeError:** Cannot read property 'Symbol(Symbol.iterator)' of undefined

This throws an error because `createGrid()` expects an array to be passed in that it will then destructure. Since the function was called without passing an array, it breaks. But, we can use default function parameters for this!

```js
function createGrid([width = 5, height = 5] = []) {
  return `Generates a ${width} x ${height} grid`;
}
```

See that new `= []` in the function's parameter? If `createGrid()` is called without any argument then it will use this default empty array. And since the array is empty, there's nothing to destructure into `width` and `height`, so their default values will apply! So by adding `= []` to give the entire parameter a default, the following code will now work:

```js
createGrid(); // Generates a 5 x 5 grid
```

> **Returns:** Generates a 5 x 5 grid

#### QUESTION 1 OF 2
Take a look at the following code:

```js
function houseDescriptor([houseColor = 'green', shutterColors = ['red']]) {
  return `I've a ${houseColor} house w/ ${shutterColors.join(' and ')} shutters`;
}
```

Which of the following choices will run without throwing an error?

1. [ ] houseDescriptor('red', ['white', 'gray', 'pink']);
1. [ ] houseDescriptor(['green', ['white', 'gray', 'pink']]);
1. [ ] houseDescriptor(['blue', 'purple']);
1. [ ] houseDescriptor(['green]);

#### Solution
Options 2 and 4 are the only choices that will run correctly without throwing an error.

- [ ] Since `houseDescriptor` is expecting only a single argument (an array) to be passed in, Option 1 has to be incorrect since it's calling the function with two arguments.
- [x] Option 2 is correct.
- [ ] Option 3 does call the function with a single array argument, but the second item in the list is a string and `.join()` is not a method of strings, so the code throws an error.
- [x] Option 4 is correct.

### Defaults and destructuring objects
Just like array destructuring with array defaults, a function can have an object be a default parameter and use object destructuring:

```js
function createSundae({scoops = 1, toppings = ['Hot Fudge']}) {
  const scoopText = scoops === 1 ? 'scoop' : 'scoops';
  return `Your sundae has ${scoops} ${scoopText} with ${toppings.join(' and ')} toppings.`;
}

createSundae({});
// Your sundae has 1 scoop with Hot Fudge toppings.
createSundae({scoops: 2});
// Your sundae has 2 scoops with Hot Fudge toppings.
createSundae({scoops: 2, toppings: ['Sprinkles']});
// Your sundae has 2 scoops with Sprinkles toppings.
createSundae({toppings: ['Cookie Dough']});
// Your sundae has 1 scoop with Cookie Dough toppings.
```

> **Returns:**
> Your sundae has 1 scoop with Hot Fudge toppings.
> Your sundae has 2 scoops with Hot Fudge toppings.
> Your sundae has 2 scoops with Sprinkles toppings.
> Your sundae has 1 scoop with Cookie Dough toppings.

Just like the array example before, if you try calling the function without any arguments it won't work:

```js
createSundae(); // throws an error
```

> **Uncaught TypeError:** Cannot match against 'undefined' or 'null'.

We can prevent this issue by providing a default object to the function:

```js
function createSundae({scoops = 1, toppings = ['Hot Fudge']} = {}) {
  const scoopText = scoops === 1 ? 'scoop' : 'scoops';
  return `Your sundae has ${scoops} ${scoopText} with ${toppings.join(' and ')} toppings.`;
}
```

By adding an empty object as the default parameter in case no arguments are provided, calling the function without any arguments now works.

```js
createSundae(); // Your sundae has 1 scoop with Hot Fudge toppings.
```

> **Returns:** Your sundae has 1 scoop with Hot Fudge toppings.

#### Question 2 of 2
Take a look at the following code:

```js
function houseDescriptor({houseColor = 'green', shutterColors = ['red']} = {}) {
  return `I have a ${houseColor} house with ${shutterColors.join(' and ')} shutters`;
}
```

Which of the following choices will run without throwing an error?

1. [ ] houseDescriptor({houseColor: 'red', shutterColors: ['white', 'gray', 'pink']});
1. [ ] houseDescriptor({houseColor: 'red'});
1. [ ] houseDescriptor();
1. [ ] houseDescriptor({shutterColors: ['orange', 'blue']});
1. [ ] houseDescriptor({});

#### Solution
Actually, every single one of these function calls will work correctly! 

The only option that would NOT work is:

- [ ] houseDescriptor({houseColor: 'red', shutterColors: 'white'});<br>
  Uncaught TypeError: `.join` is not a function of String. The function is expecting an array as the `shutterColors` property.

### Array defaults vs. object defaults
Default function parameters are a simple addition, but it makes our lives so much easier! One benefit of object defaults over array defaults is how they handle skipped options. Check this out:

```js
function createSundae({scoops = 1, toppings = ['Hot Fudge']} = {}) { }
```

With the `createSundae()` function using object defaults with destructuring, if you want to use the default value for `scoops` but change the `toppings`, then all you need to do is pass in an object with `toppings`:

```js
createSundae({toppings: ['Hot Fudge', 'Sprinkles', 'Caramel']});
```

Compare the above example with the same function that uses array defaults with destructuring.

```js
function createSundae([scoops = 1, toppings = ['Hot Fudge']] = []) { }
```

With this function setup, if you want to use the default number of scoops but change the toppings, you'd have to call your function a little...oddly:

```js
createSundae([undefined, ['Hot Fudge', 'Sprinkles', 'Caramel']]);
```

Since arrays are positionally based, we have to pass `undefined` to "skip" over the first argument (and accept the default) to get to the second argument.

**Unless you've got a strong reason to use array defaults with array destructuring, we recommend going with object defaults with object destructuring!**

## 11. Quiz: Default Function Parameters
### Directions:
Create a `buildHouse()` function that accepts an object as a default parameter. The object should set the following properties to these default values:

- `floors = 1`
- `color = 'red'`
- `walls = 'brick'`

The function should return the following if no arguments or any empty object is passed to the function.

> Your house has 1 floor(s) with red brick walls.

#### Code

```js
/*
 * Programming Quiz: Using Default Function Parameters (2-2)
 */

// your code goes here

// tests
console.log(buildHouse());
console.log(buildHouse({}));
console.log(buildHouse({floors: 3, color: 'yellow'}));

// Your house has 1 floor(s) with red brick walls.
// Your house has 1 floor(s) with red brick walls.
// Your house has 3 floor(s) with yellow brick walls.
```

#### Solution

```js
/*
 * Programming Quiz: Using Default Function Parameters (2-2)
 */

function buildHouse({floors = 1, color = 'red', walls = 'brick'} = {}) {
    return `Your house has ${floors} floor(s) with ${color} ${walls} walls.`;
}

// tests
console.log(buildHouse());
console.log(buildHouse({}));
console.log(buildHouse({floors: 3, color: 'yellow'}));

// Your house has 1 floor(s) with red brick walls.
// Your house has 1 floor(s) with red brick walls.
// Your house has 3 floor(s) with yellow brick walls.
```

> **Note:** Remember to return the result (as shown above) rather than `console.log()` from inside the function.