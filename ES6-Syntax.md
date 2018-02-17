---
title: ES6 JavaScript Improved
description: Grow with Google Scholarship Challenge - Mobile Web Track
---
<!-- markdownlint-disable MD022 MD024 MD032 -->
# Lesson 1: Syntax
Notes from _Lesson 1: Syntax_ of _ES6 JavaScript Improved_ by Richard Kalehoff and James Parkes. This class is part of the Udacity course [ES6 - JavaScript Improved](https://www.udacity.com/course/es6-javascript-improved--ud356)

This is an Intermediate skill level course which takes approximately 4 weeks to complete and is offered for **FREE**!

## 1. Harmony, ES6, ES2015
Technically Harmony, ES6 and ES2015 they're all different names for virtually the same thing. The important thing is that these names represent the biggest update to the JavaScript programming language to date.

Fast forward from 1995 to today and javascript has undergone a renaissance of sorts by making some much-needed im batch of keywords, ways of writing functions, asynchronous goodies. and so much more.

In this course will explore the additions to the JavaScript programming language so you can write faster, cleaner, and more efficient code.

[![Syntax 1](assets/images/sm_lesson6-syntax1.jpg)](assets/images/full-size/lesson6-sytnax1.png)

- Lesson 1 - We outline changes and additions to the JavaScript syntax.
- Lesson 2 - We investigate updates to JavaScript functions
- Lesson 3 - We cover new es6 built-ins
- Lesson 4 - We wrap things up by showing you how you can incorporate these latest updates into your next JavaScript project.

Lets start with new keywords have been added to the language.

## 2. Let and Const
There are now two new ways to declare variables in JavaScript: **let** and **const**.

Up until now, the only way to declare a variable in JavaScript was to use the keyword `var`. To understand why `let` and `const` were added, it’s probably best to look at an example of when using `var` can get us into trouble.

Take a look at the following code.

#### Question 1 of 3
what would you expect the output to be from running `getClothing(false)`?

```js
function getClothing(isCold) {
  if (isCold) {
    var freezing = 'Grab a jacket!';
  } else {
    var hot = 'It’s a shorts kind of day.';
    console.log(freezing);
  }
}
```

1. [ ] ReferenceError: freezing is not defined
1. [ ] Grab a jacket!
1. [ ] undefined
1. [ ] It's a shorts kind of day.

#### Solution
- [x] undefined

It actually outputs `undefined`, weird right? Continue reading to learn more about this quirk of JavaScript.

---

### Hoisting
Hoisting is a result of how JavaScript is interpreted by your browser. Essentially, before any JavaScript code is executed, all variables are "hoisted", which means they're raised to the top of the function scope. 

So at run-time, the `getClothing()` function actually looks more like this…

```js
function getClothing(isCold) {
  var freezing, hot;
  if (isCold) {
    freezing = 'Grab a jacket!';
  } else {
    hot = 'It’s a shorts kind of day.';
    console.log(freezing);
  }
}
```

Before the function is executed, all variables are hoisted to the top of the function scope. So what’s our solution?

---

### let and const
Variables declared with `let` and `const` eliminate this specific issue of hoisting because they’re **scoped to the block, not to the function**. Previously, when you used `var`, variables were either scoped globally or locally to an entire function scope.

If a variable is declared using `let` or `const` inside a block of code (denoted by curly braces { }), then the variable is stuck in what is known as the **temporal dead zone** until the variable’s declaration is processed. This behavior prevents variables from being accessed only until after they’ve been declared.

Variables declared with `let` and `const` are **only available within the block they're declared**.

#### Question 2 of 3
What do you expect the output from running `getClothing(false)`?

```js
function getClothing(isCold) {
  if (isCold) {
    const freezing = 'Grab a jacket!';
  } else {
    const hot = 'It’s a shorts kind of day.';
    console.log(freezing);
  }
}
```

1. [ ] ReferenceError: freezing is not defined
1. [ ] Grab a jacket!
1. [ ] undefined
1. [ ] It's a shorts kind of day.

#### Solution
- [x] ReferenceError: freezing is not defined

Because freezing is not declared inside the else statement, the function scope, or the global scope, a ReferenceError is thrown.

---

### Rules for using let and const
`let` and `const` also have some other interesting properties.

- Variables declared with `let` can be reassigned, but can’t be redeclared in the same scope.
- Variables declared with `const` must be assigned an initial value, but can’t be redeclared in the same scope, and can’t be reassigned.

#### Question 3 of 3
What do you expect to be output from running the following code?

```js
let instructor = 'James';
instructor = 'Richard';
console.log(instructor);
```

1. [ ] James
1. [ ] Richard
1. [ ] undefined
1. [ ] SyntaxError: Identifier 'instructor' has already been declared

#### Solution
- [x] Richard

This is the correct way to use `let`. Use `let` to declare variables when you plan on changing the value of a variable later in your code.

---

### Use cases
The big question is when should you use `let` and `const`? The general rule of thumb is as follows:

- use `let` when you plan to reassign new values to a variable, and
- use `const` when you don’t plan on reassigning new values to a variable.

Since `const` is the strictest way to declare a variable, we suggest that you always declare variables with `const` because it'll make your code easier to reason about since you know the identifiers won't change throughout the lifetime of your program. If you find that you need to update a variable or change it, then go back and switch it from `const` to `let`.

That’s pretty straightforward, right? But what about `var`?

### What about var?
Is there any reason to use `var` anymore? _Not really_.

There are some arguments that can be made for using `var` in situations where you want to globally define variables, but this is often considered bad practice and should be avoided. From now on, we suggest ditching `var` in place of using `let` and `const`.

## 3. Quiz: Let and Const (1-1)
Replace the variable declarations using `let` or `const`.

```js
/*
 * Programming Quiz: Using Let and Const (1-1)
 */
var CHARACTER_LIMIT = 255;
var posts = [
  "#DeepLearning transforms everything from self-driving cars to language translations. AND it's our new Nanodegree!",
  "Within your first week of the VR Developer Nanodegree Program, you'll make your own virtual reality app",
  "I just finished @udacity's Front-End Web Developer Nanodegree. Check it out!"
];

// prints posts to the console
function displayPosts() {
  for (var i = 0; i < posts.length; i++) {
    console.log(posts[i].slice(0, CHARACTER_LIMIT));
  }
}

displayPosts();

```

#### Solution

```js
const CHARACTER_LIMIT = 255;
const posts = [
  "#DeepLearning transforms everything from self-driving cars to language translations. AND it's our new Nanodegree!",
  "Within your first week of the VR Developer Nanodegree Program, you'll make your own virtual reality app",
  "I just finished @udacity's Front-End Web Developer Nanodegree. Check it out!"
];

// prints posts to the console
function displayPosts() {
  for (let i = 0; i < posts.length; i++) {
    console.log(posts[i].slice(0, CHARACTER_LIMIT));
  }
}

displayPosts();
```

## 4. Template Literals
Prior to ES6, the old way to concatenate strings together was by using the string concatenation operator ( `+` ).

```js
const student = {
  name: 'Richard Kalehoff',
  guardian: 'Mr. Kalehoff'
};

const teacher = {
  name: 'Mrs. Wilson',
  room: 'N231'
}

let message = student.name + ' please see '
  + teacher.name + ' in ' + teacher.room
  + ' to pick up your report card.';
```

> **Returns:** Richard Kalehoff please see Mrs. Wilson in N231 to pick up your report card.

This works alright, but it gets more complicated when you need to build multi-line strings.

```js
let note = teacher.name + ',\n\n' +
  'Please excuse ' + student.name + '.\n' +
  'He is recovering from the flu.\n\n' +
  'Thank you,\n' +
  student.guardian;
```

> **Returns:**<br>
> Mrs. Wilson,
>
> Please excuse Richard Kalehoff.<br>
> He is recovering from the flu.
>
> Thank you,<br>
> Mr. Kalehoff

However, that’s changed with the introduction of _template literals_ (previously referred to as "template strings" in development releases of ES6).

> **NOTE:** As an alternative to using the string concatenation operator ( `+` ), you can use the String's `concat()` method, but both options are rather clunky for simulating true [string interpolation](https://en.wikipedia.org/wiki/String_interpolation#JavaScript).

### Template Literals
**Template literals** are essentially string literals that include embedded expressions.

Denoted with backticks( \`\` ) instead of single quotes ( `''` ) or double quotes ( `""` ), template literals can contain placeholders which are represented using `${expression}`. This makes it much easier to build strings.

Here's the previous examples using template literals.

```js
let message = `${student.name} please see ${teacher.name} in ${teacher.room}.`;
```

> **Returns:** Richard Kalehoff please see Mrs. Wilson in N231.

By using template literals, you can drop the quotes along with the string concatenation operator. Also, you can reference the object's properties inside expressions.

Here, you try. Change the `greeting` string below to use a template literal. Also, feel free to swap in your name for the placeholder.

```js
/*
 * Instructions: Change the `greeting` string to use a template literal.
 */

const myName = '[NAME]';
const greeting = 'Hello, my name is ' + myName;
console.log(greeting);
```

#### Solution

```js
/*
 * Instructions: Change the `greeting` string to use a template literal.
 */

const myName = 'James';
const greeting = `Hello, my name is ${myName}`;
console.log(greeting);
```

...but what about the multi-line example from before?

```js
let note = teacher.name + ',\n\n' +
  'Please excuse ' + student.name + '.\n' +
  'He is recovering from the flu.\n\n' +
  'Thank you,\n' +
  student.guardian;
```

becomes,

```js
var note = `${teacher.name},

  Please excuse ${student.name}.
  He is recovering from the flu.

  Thank you,
  ${student.guardian}`;
```

Template literals make multi-line strings easier to read and more concise.

Here’s where template literals really shine. In the animation above, the quotes and string concatenation operator have been dropped, as well as the newline characters ( `\n` ). That's because template literals also preserve newlines as part of the string!

> **TIP:** Embedded expressions inside template literals can do more than just reference variables. You can perform operations, call functions and use loops inside embedded expressions!

## 5. Quiz: HTML Fragments (1-2)
### Directions:
Modify the `createAnimalTradingCardHTML()` function to use a template literal for `cardHTML`.

```js
/*
 * Programming Quiz: Build an HTML Fragment (1-2)
 */

const cheetah = {
    name: 'Cheetah',
    scientificName: 'Acinonyx jubatus',
    lifespan: '10-12 years',
    speed: '68-75 mph',
    diet: 'carnivore',
    summary: 'Fastest mammal on land, the cheetah can reach speeds of 60 or perhaps even 70 miles (97 or 113 kilometers) an hour over short distances. It usually chases its prey at only about half that speed, however. After a chase, a cheetah needs half an hour to catch its breath before it can eat.',
    fact: 'Cheetahs have “tear marks” that run from the inside corners of their eyes down to the outside edges of their mouth.'
};

// creates an animal trading card
function createAnimalTradingCardHTML(animal) {
    const cardHTML = '<div class="card">' +
        '<h3 class="name">' + animal.name + '</h3>' +
        '<img src="' + animal.name + '.jpg" alt="' + animal.name +'" class="picture">' +
        '<div class="description">' +
            '<p class="fact">' + animal.fact + '</p>' +
            '<ul class="details">' +
                '<li><span class="bold">Scientific Name</span>: ' + animal.scientificName + '</li>' +
                '<li><span class="bold">Average Lifespan</span>: ' + animal.lifespan + '</li>' +
                '<li><span class="bold">Average Speed</span>: ' + animal.speed + '</li>' +
                '<li><span class="bold">Diet</span>: ' + animal.diet + '</li>' +
            '</ul>' +
            '<p class="brief">' + animal.summary + '</p>' +
        '</div>' +
    '</div>';

    return cardHTML;
}

console.log(createAnimalTradingCardHTML(cheetah));
```

#### Solution

```js
/*
 * Programming Quiz: Build an HTML Fragment (1-2)
 */

const cheetah = {
    name: 'Cheetah',
    scientificName: 'Acinonyx jubatus',
    lifespan: '10-12 years',
    speed: '68-75 mph',
    diet: 'carnivore',
    summary: 'Fastest mammal on land, the cheetah can reach speeds of 60 or perhaps even 70 miles (97 or 113 kilometers) an hour over short distances. It usually chases its prey at only about half that speed, however. After a chase, a cheetah needs half an hour to catch its breath before it can eat.',
    fact: 'Cheetahs have “tear marks” that run from the inside corners of their eyes down to the outside edges of their mouth.'
};

// creates an animal trading card
function createAnimalTradingCardHTML(animal) {
    const cardHTML = `<div class="card">
        <h3 class="name">${animal.name}</h3>
        <img src="${animal.name}.jpg" alt="${animal.name}" class="picture">
        <div class="description">
            <p class="fact">${animal.fact}</p>
            <ul class="details">
                <li><span class="bold">Scientific Name</span>: ${animal.scientificName}</li>
                <li><span class="bold">Average Lifespan</span>: ${animal.lifespan}</li>
                <li><span class="bold">Average Speed</span>: ${animal.speed}</li>
                <li><span class="bold">Diet</span>: ${animal.diet}</li>
            </ul>
            <p class="brief">${animal.summary}</p>
        </div>
    </div>`;

    return cardHTML;
}

console.log(createAnimalTradingCardHTML(cheetah));
```

## 6. Destructuring Arrays
In ES6, you can extract data from arrays and objects into distinct variables using _destructuring_.

This probably sounds like something you’ve done before, for example, look at the two code snippets below that extract data using pre-ES6 techniques:

#### Extracting values from an array

```js
const point = [10, 25, -34];

const x = point[0];
const y = point[1];
const z = point[2];

console.log(x, y, z);
```

> **Prints:** 10 25 -34

#### Extracting values from an object

```js
const type = gemstone.type;
const color = gemstone.color;
const karat = gemstone.karat;

console.log(type, color, karat);
```

> **Prints:** quartz rose 21.29

Both are pretty straightforward, however, neither of these examples are actually using destructuring.

So what exactly is _destructuring_?

### Destructuring
**Destructuring** borrows inspiration from languages like **Perl** and **Python** by allowing you to specify the elements you want to extract from an array or object _on the left side of an assignment_. It sounds a little weird, but you can actually achieve the same result as before, but with much less code; and it's still easy to understand.

Let’s take a look at both examples rewritten using destructuring.

### Destructuring values from an array

```js
const point = [10, 25, -34];

const [x, y, z] = point;

console.log(x, y, z);
```

> **Prints:** 10 25 -34

In this example, the brackets `[ ]` represent the array being destructured and `x`, `y`, and `z` represent the variables where you want to store the values from the array. Notice how you don’t have to specify the indexes for where to extract the values from because the indexes are implied.

> **TIP:** You can also ignore values when destructuring arrays. For example, `const [x, , z] = point;` ignores the `y` coordinate and discards it.

#### Question 1 of 2
What do you expect to be the value of `second` after running the following code?

```js
let positions = ['Gabrielle', 'Jarrod', 'Kate', 'Fernando', 'Mike', 'Walter'];
let [first, second, third] = positions;
```

1. [ ] Kate
1. [ ] Gabrielle
1. [ ] Jarrod
1. [ ] Walter

#### Answer
The variables first, second, and third get populated with the first 3 values in the positions array while the remaining values are ignored.

- [x] Jarrod

---

### Destructuring values from an object

```js
const gemstone = {
  type: 'quartz',
  color: 'rose',
  karat: 21.29
};

const {type, color, karat} = gemstone;

console.log(type, color, karat);
```

> **Prints:** quartz rose 21.29

In this example, the curly braces `{ }` represent the object being destructured and `type`, `color`, and `karat` represent the variables where you want to store the properties from the object. Notice how you don’t have to specify the property from where to extract the values. Because `gemstone` has a property named `type`, the value is automatically stored in the type variable. Similarly, `gemstone` has a `color` property, so the value of `color` automatically gets stored in the `color` variable. And it's the same with `karat`.

> **TIP:** You can also specify the values you want to select when destructuring an object. For example, `let {color} = gemstone;` will only select the `color` property from the `gemstone` object.

#### Question 2 of 2
What do you expect to be returned from calling `getArea()`?

```js
const circle = {
  radius: 10,
  color: 'orange',
  getArea: function() {
    return Math.PI * this.radius * this.radius;
  },
  getCircumference: function() {
    return 2 * Math.PI * this.radius;
  }
};

let {radius, getArea, getCircumference} = circle;
```

1. [ ] 314.1592653589793
1. [ ] NaN
1. [ ] 62.83185307179586
1. [ ] pie

#### Answer

- [x] NaN

Calling getArea() will return NaN. When you destructure the object and store the getArea() method into the getArea variable, it no longer has access to this in the circle object which results in an area that is NaN.

## 7. Quiz: Destructuring (1-3)
### Directions:
Use array destructuring to pull out the three colors from the array of `things` and store them into the variables `one`, `two`, and `three`.

```js
/*
 * Programming Quiz: Destructuring Arrays (1-3)
 *
 * Use destructuring to initialize the variables `one`, `two`, and `three`
 * with the colors from the `things` array.
 */

const things = ['red', 'basketball', 'paperclip', 'green', 'computer', 'earth', 'udacity', 'blue', 'dogs'];

const one = things;
const two = '';
const three = '';

const colors = `List of Colors
1. ${one}
2. ${two}
3. ${three}`;

console.log(colors);
```

#### Solution

```js
/*
 * Programming Quiz: Destructuring Arrays (1-3)
 *
 * Use destructuring to initialize the variables `one`, `two`, and `three`
 * with the colors from the `things` array.
 */

const things = ['red', 'basketball', 'paperclip', 'green', 'computer', 'earth', 'udacity', 'blue', 'dogs'];

const [one,,, two,,,, three] = things;

const colors = `List of Colors
1. ${one}
2. ${two}
3. ${three}`;

console.log(colors);
```

We use commas to to skip values in the array assignment in order to single out each of the colors.

## 8. Object Literal Shorthand
A recurring trend in ES6 is to remove unnecessary repetition in your code. By removing unnecessary repetition, your code becomes easier to read and more concise. This trend continues with the introduction of new _shorthand_ ways for initializing objects and adding methods to objects.

Let’s see what those look like.

### Object literal shorthand
You’ve probably written code where an object is being initialized using the same property names as the variable names being assigned to them.

But just in case you haven’t, here’s an example.

```js
let type = 'quartz';
let color = 'rose';
let carat = 21.29;

const gemstone = {
  type: type,
  color: color,
  carat: carat
};

console.log(gemstone);
```

> **Prints:** Object {type: "quartz", color: "rose", carat: 21.29}

Do you see the repetition? Doesn't `type: type`, `color: color`, and `carat:carat` seem redundant?

The good news is that you can remove those duplicate variables names from object properties if the properties have the same name as the variables being assigned to them.

Check it out!

```js
let type = 'quartz';
let color = 'rose';
let carat = 21.29;

let gemstone = { type, color, carat };

console.log(gemstone);
```

If object properties have the same name as the variables being assigned to them, then you can drop the duplicate variable names.

Speaking of shorthand, there’s also a shorthand way to add methods to objects.

To see how that looks, let’s start by adding a `calculateWorth()` method to our `gemstone` object. The `calculateWorth()` method will tell us how much our gemstone costs based on its `type`, `color`, and `carat`.

```js
let type = 'quartz';
let color = 'rose';
let carat = 21.29;

const gemstone = {
  type,
  color,
  carat,
  calculateWorth: function() {
    // will calculate worth of gemstone based on type, color, and carat
  }
};
```

In this example, an anonymous function is being assigned to the property `calculateWorth`, but is the **function** keyword _really_ needed? In ES6, it’s not!

### Shorthand method names
Since you only need to reference the gemstone’s `calculateWorth` property in order to call the function, having the function keyword is redundant, so it can be dropped.

```js
let gemstone = {
  type,
  color,
  carat,
  calculateWorth() { ... }
};
```

## 9. Lesson 1 Checkup
So far we've covered the following improvements to the JavaScript language.

### Declaring Variables

- let & const
- template literals
- destructuring
- object literal shorthand

Hopefully, it's clear how these shorthand improvements will make your code more clear and concise.

What we'll cover next is:

### Language Constructs

- for.. of loop
- rest parameter
- spread operator

Before moving on we need to discuss **iteration**.

_Iteration_ is a new mechanism for looping through data in ES6. Understanding what it is and how it works will be important for finishing up this lesson.

## 10. Iteration
So, what is iteration? Probably the best way to describe it is by looking at a normal for loop.

```js
for (let i = 0; i < 10; i++) {
  console.log(digits[i]);
}
```

When you write a for loop, you provide the loop with a variable (`let i`). This variable is typically the letter `i` because it's being used as an iterator to keep track of your place in the loop.

```js
const years = ['1999', '2001', '2013', '2016'];

for (let i = 0; i < years.length; i++) {
  console.log(years[i]);
}
```

When you're looping over something like an array, this iterator works like an index, letting you access each item in the array one after the other.

This process of getting the next item, one after the other, is iteration, and we've been using it for a long time. So, why even bring this up? It sounds like iteration has always been a part of Javascript. So, what's new in ES6?

Well, there are a couple of things. First, there's a new iterable interface that
allows us to customize how objects are iterated. So, basically how they're looped over.

> **iterable protocol** - allows JavaScript objects to define or customize their **iteration behavior**

```js
const teacher = ['Richard'];

teacher[Symbol.iterator] = function () {
  // returns a custom iterator
}
```

We'll look at this more closely in lesson three, when we talk about symbols.

The second thing is there's a new loop, it's called the `for..of loop`, which loops exclusively over iterable objects.

> **for..of loop** a loop that **iterates over iterable objects**

Now, when I say iterable objects, I just mean an object that has implemented this new iterable interface.

```js
const names = ['James', 'Kavita', 'Richard'];

for (const name of names) {
  console.log(name);
}

// logs the following names:
// James
// Kavita
// Richard
```

See the `for` and the `of` keywords in the loop definition?

Now, this might sound a little bit fuzzy. So let's actually take a step back and look at some code examples of traditional for loops, and then see how the new for-of loop really stands out as your best option for looping.

## 11. Family of For Loops
The **for...of loop** is the most recent addition to the family of for loops in JavaScript.

It combines the strengths of its siblings, the **for loop** and the **for...in loop**, to loop over any type of data that is **iterable** (meaning it follows the [iterable protocol](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols) which we'll look at in lesson 3). By default, this includes the data types String, Array, Map, and Set—notably absent from this list is the `Object` data type (i.e. `{}`). Objects are not iterable, by default.

Before we look at the for...of loop, let’s first take a quick look at the other for loops to see where they have weaknesses.

### The for loop
The for loop is obviously the most common type of loop there is, so this should be a quick refresher.

```js
const digits = [ 0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

for (let i = 0; i < digits.length; i++) {
  console.log(digits[i]);
}
```

> **Prints:**<br>
> 0<br>
> 1<br>
> 2<br>
> 3<br>
> 4<br>
> 5<br>
> 6<br>
> 7<br>
> 8<br>
> 9<br>

Really the biggest downside of a for loop is having to keep track of **the counter** and **exit condition**.

In this example, we’re using the variable `i` as a counter to keep track of the loop and to access values in the array. We’re also using `digits.length` to determine the exit condition for the loop. If you just glance at this code, it can sometimes be confusing exactly what’s happening; especially for beginners.

While for loops certainly have an advantage when looping through arrays, some data is not structured like an array, so a for loop isn’t always an option.

### The for..in loop
The for...in loop improves upon the weaknesses of the for loop by eliminating the counting logic and exit condition.

```js
const digits = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

for (const index in digits) {
  console.log(digits[index]);
}
```

> **Prints:**<br>
> 0<br>
> 1<br>
> 2<br>
> 3<br>
> 4<br>
> 5<br>
> 6<br>
> 7<br>
> 8<br>
> 9<br>

But, you still have to deal with the issue of using an **index** to access the values of the array, and that stinks; it almost makes it more confusing than before.

Also, the for..in loop can get you into big trouble when you need to add an extra method to an array (or another object). Because for..in loops loop over **all enumerable properties**, this means if you add any additional properties to the array's prototype, then those properties will also appear in the loop.

```js
Array.prototype.decimalfy = function() {
  for (let i = 0; i < this.length; i++) {
    this[i] = this[i].toFixed(2);
  }
};

const digits = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

for (const index in digits) {
  console.log(digits[index]);
}
```

> **Prints:**<br>
> 0<br>
> 1<br>
> 2<br>
> 3<br>
> 4<br>
> 5<br>
> 6<br>
> 7<br>
> 8<br>
> 9<br>
> function() {<br>
>   for (let i = 0; i < this.length; i++) {<br>
>     this[i] = this[i].toFixed(2);<br>
>   }<br>
> }

This is why for...in loops are discouraged when looping over arrays.

> **NOTE:** The **forEach loop** is another type of for loop in JavaScript. However, `forEach()` is actually an array method, so it can only be used exclusively with arrays. **There is also no way to stop or break a forEach loop. If you need that type of behavior in your loop, you’ll have to use a basic for loop.**

## 12. For..of Loop
Finally, we have the mighty for...of loop.

### For..of loop
The **for..of loop** is used to loop over any type of data that is _iterable_.

You write a **for..of** loop almost exactly like you would write a **for..in** loop, except you swap out in with of and you can drop the **index**.

```js
const digits = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

for (const digit of digits) {
  console.log(digit);
}
```

> **Prints:**<br>
> 0<br>
> 1<br>
> 2<br>
> 3<br>
> 4<br>
> 5<br>
> 6<br>
> 7<br>
> 8<br>
> 9<br>

**This makes the for...of loop the most concise version of all the for loops.**

> **TIP:** It’s good practice to use plural names for objects that are collections of values. That way, when you loop over the collection, you can use the singular version of the name when referencing individual values in the collection. For example, `for (const button of buttons) {...}`.

### Progression of loops

```js
const digits = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

// for loop
for (let i = 0; i < digits.length; i++) {
  console.log(digits[i]);
}

// for..in  loop
for (let index in digits) {
  console.log(digits[index]);
}

// for..of loop
for (let digits of digit) {
  console.log(digit);
}
```

But wait, there’s more! The `for..of` loop also has some additional benefits that fix the weaknesses of the `for` and `for..in` loops.

You can stop or break a for...of loop at anytime.

```js
const digits = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

for (const digit of digits) {
  if (digit % 2 === 0) {
    continue;
  }
  console.log(digit);
}
```

> **Prints:**<br>
> 1<br>
> 3<br>
> 5<br>
> 7<br>
> 9<br>

And you don’t have to worry about adding new properties to objects. The for..of loop will only loop over the values in the object.

```js
Array.prototype.decimalfy = function() {
  for (i = 0; i < this.length; i++) {
    this[i] = this[i].toFixed(2);
  }
};

const digits = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

for (const digit of digits) {
  console.log(digit);
}
```

> **Prints:**<br>
> 0<br>
> 1<br>
> 2<br>
> 3<br>
> 4<br>
> 5<br>
> 6<br>
> 7<br>
> 8<br>
> 9<br>

## 13. Quiz: For..of Loops (1-4)
### Directions
Write a for...of loop that:

- loops through each day in the days array
- capitalizes the first letter of the day
- and prints the day out to the console

Your code should log the following to the console:

> Sunday<br>
> Monday<br>
> Tuesday<br>
> Wednesday<br>
> Thursday<br>
> Friday<br>
> Saturday<br>

```js
/*
 * Programming Quiz: Writing a For...of Loop (1-4)
 */

const days = ['sunday', 'monday', 'tuesday', 'wednesday', 'thursday', 'friday', 'saturday'];

// your code goes here

```

#### Solution

```js
/*
 * Programming Quiz: Writing a For...of Loop (1-4)
 */

const days = ['sunday', 'monday', 'tuesday', 'wednesday', 'thursday', 'friday', 'saturday'];

// your code goes here
for(let day of days) {
    let word = day[0].toUpperCase() + day.substr(1);
    console.log(word);
}
```