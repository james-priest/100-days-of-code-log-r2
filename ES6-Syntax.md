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

<!--
## 5. Quiz: HTML Fragments (1-2)

## 7. Quiz: Destructuring (1-3)

## 13. Quiz: For..of Loops (1-4)

## 16. Quiz: Rest Parameter (1-5)
-->