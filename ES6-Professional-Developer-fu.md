---
title: ES6 - Professional Developer-fu
description: Grow with Google Scholarship Challenge - Mobile Web Track
---
<!-- markdownlint-disable MD022 MD024 MD032 -->
# Lesson 4: Professional Developer-fu
Notes from _Lesson 4: Professional Developer-fu_ of _**ES6 JavaScript Improved**_ by Richard Kalehoff and James Parkes. This class is part of the Udacity course [ES6 - JavaScript Improved](https://www.udacity.com/course/es6-javascript-improved--ud356)

This is an Intermediate skill level course which takes approximately 4 weeks to complete and is offered for **FREE**!

| Lesson 1 | Lesson 2 | Lesson 2.5 | Lesson 3 | Lesson 3.5 | Lesson 4 |
| --- | --- | --- | --- | --- | --- |
| [Syntax](ES6-Syntax.html) | [Functions](ES6-Functions.html)  | [Classes](ES6-Classes.html) | [Built-ins](ES6-Built-ins.html) | [Built-ins Pt2](ES6-Built-ins-Pt2.html) | **Professional Developer-fu** |

## 1. The Web is Growing Up
This lesson will prepare you for deploying ES6 in the ever-changing environment that is the web.

Basically the web had a beginning but it won't have an end. As new technology comes out it won't be supported by older browsers and this can make it challenging when you want to work with ES6.

How are you supposed to write ES6 but still support older browsers?

Let's take a look.

## 2. Old and New Browsers
### Code doesn't work in old browsers
The code we've been looking at in this course is not supported by older browsers. Older browsers that were developed prior to the release of ES6 were developed to support the version of JavaScript at the time (which was ES5.1). If you try running any ES6 code in an older browser, it won't work.

[![9-1](assets/images/sm_lesson9-1.jpg)](assets/images/full-size/lesson9-1.png)

> An arrow function is run and causes a syntax error in Safari 9.

It makes sense that code doesn't work in older browsers that were developed prior to the release of ES6, but there are some browsers that have been released after ES6 that don't support the new JavaScript syntax and functionality yet.

Try using an arrow function in your code and opening it up in IE 11, and it won't work. There'll be an error on the console saying that it doesn't recognize the syntax.

[![9-2](assets/images/sm_lesson9-2.jpg)](assets/images/full-size/lesson9-2.png)

> An arrow function is run and causes a syntax error in IE 11.

Most of us don't think much about the browser and all it can do...until it doesn't work! But really, browser makers have a tough time. Think about HTML, CSS, and JavaScript - these languages are fluid and are always improving. Browser makers have to keep up with all of these changes.

#### But how do they know about these changes?

They learn (or actually build) the language specifications!

Just like the [World Wide Web Consortium (W3C)](https://www.w3.org/) is the standards body for things like HTML, CSS, and SVG, [Ecma International](https://www.ecma-international.org/) is an industry association that develops and oversees standards like JavaScript and JSON. You can find the specifications for ES6 [here](http://www.ecma-international.org/ecma-262/6.0/index.html).

### Further Info
Ecma International is an important industry community and definitely worth checking out in more detail:

- [https://en.wikipedia.org/wiki/Ecma_International](https://en.wikipedia.org/wiki/Ecma_International)
- [http://www.ecma-international.org/memento/index.html](http://www.ecma-international.org/memento/index.html)

> **NOTE:** The code we've been looking at in this course is not supported by older browsers. Older browsers that were developed prior to the release of ES6 were developed to support the version of JavaScript at the time (which was ES5.1). If you try running any ES6 code in an older browser, it won't work.

### 3. ES6 Specification
The specification (commonly shortened to "spec") for ES6 can be found [here](http://www.ecma-international.org/ecma-262/6.0/index.html). The spec lists the set of rules and guidelines on _how_ the language is supposed to function. It doesn't give specific details on how browser makers are supposed to achieve functionality, but it does provide step-by-step instructions on how the language is supposed to work. While making this course, we repeatedly referred to this official spec.

Ok, so honestly, it can be a little difficult to decipher some of the cryptic wording of the spec. But when you have a question about ES6, we recommend checking out info on the topic like that provided by the [Mozilla Developer Network](https://developer.mozilla.org/) and then also reviewing what the spec actually says.

#### Quiz Question
Check out the [ES6 Specification](http://www.ecma-international.org/ecma-262/6.0/index.html). Which section in the spec covers arrow functions?

1. [ ] section 6
1. [ ] section 10.3.2
1. [ ] section 14.2
1. [ ] section 18.3.29

#### Solution
The section on arrow functions is number 14.2

- [x] section 14.2

## 4. Supported Features
### How Can You Know What Features Browsers Support?
With new language specifications coming out every year and with browsers updating every other month, it can be quite challenging to know what browser supports which language features. Each browser maker (except for Safari) has a website that tracks its development status. Checkout the platform feature updates for each browser:

- Google Chrome - [https://www.chromestatus.com/features#ES6](https://www.chromestatus.com/features#ES6)
- Microsoft Edge - [https://developer.microsoft.com/en-us/microsoft-edge/platform/status/?q=ES6](https://developer.microsoft.com/en-us/microsoft-edge/platform/status/?q=ES6)
- Mozilla Firefox - [https://platform-status.mozilla.org/](https://platform-status.mozilla.org/)

> **NOTE:** Safari doesn't have it's own platform status website. Under the hood, though, Safari is powered by the open source browser engine, Webkit. The status for Webkit features can be found [here](https://webkit.org/status/).

This can be a lot of information to track down. If you prefer a birdseye view of all the feature support for all JavaScript code, check out 

- [https://caniuse.com/#search=arrow](https://caniuse.com/#search=arrow)

[![9-3](assets/images/sm_lesson9-3.jpg)](assets/images/full-size/lesson9-3.png)


You can also use the ECMAScript Compatibility Table built by [@kangax](https://twitter.com/kangax):

- [http://kangax.github.io/compat-table/es6/](http://kangax.github.io/compat-table/es6/)

[![9-4](assets/images/sm_lesson9-4.jpg)](assets/images/full-size/lesson9-4.png)

#### Quiz Question
Looking at the ECMAScript Compatibility Table, what kind of information does the first _colored_ column display?

1. [ ] The list of up-to-date browsers that support ES6.
1. [ ] The list of all ES6 features.
1. [ ] The status of all ES6 features supported by your current browser.
1. [ ] Links to each browser platform's status for the specific ES6 feature.

#### Solution
The very first column lists all of the ES6 features. The second column in the table is the first one that's colored and displays the support of each ES6 feature in your the current browser.

- [x] The status of all ES6 features supported by your current browser.

## 5. The Web is Eternal
You're a pro at JavaScript but that doesn't mean you can just kick back and coast. These new additions in ES6 have brought a major change to the language. You can't just ignore them and bank on your existing knowledge of a now behind the times technology. You've got to get up, dig into the features, read the specification, follow some tutorials, maybe even write some of your own.

The web is an evolving platform and you need to evolve with it. Imagine being stuck on old horrible equipment when there are newer nicer tools available for you to use. You now know how JavaScript language improvements are made and where to find browser support for them.

You've got the tools, now its time to use them.

## 6. Polyfills
When a wall has holes in it and is in bad shape we have a way to repair and deal with the missing parts. We fill the holes so you won't be able to tell anything's wrong with it or missing.

In the United States this fill is called _Spackling_ and it's just a common paste to fill holes and cracks. It also smooths out any defects in the wall. In the United Kingdom, a popular brand name for this is _Polyfilla_. Using _Spackling_ or _Polyfilla_, it's impossible to tell that there was ever a hole in the wall.

For the web, a polyfill does the same thing. There's some bit of functionality that might be missing in a browser that needs to get filled.

A polyfill is a JavaScript file that patches a hole by replicating some native feature for browsers that don't have it yet.

## 7. Using Polyfills
### What is a polyfill?

> A polyfill, or polyfiller, is a piece of code (or plugin) that provides the technology that you, the developer, expect the browser to provide natively.

Coined by Remy Sharp - [https://remysharp.com/2010/10/08/what-is-a-polyfill](https://remysharp.com/2010/10/08/what-is-a-polyfill)

> We, as developers, should be able to develop with the HTML5 APIs, and scripts can create the methods and objects that should exist. Developing in this future-proof way means as users upgrade, your code doesn't have to change but users will move to the better, native experience cleanly. From the HTML5 Boilerplate team on polyfills - [https://github.com/Modernizr/Modernizr/wiki/HTML5-Cross-Browser-Polyfills](https://github.com/Modernizr/Modernizr/wiki/HTML5-Cross-Browser-Polyfills)

Further research:
[https://en.wikipedia.org/wiki/Polyfill](https://en.wikipedia.org/wiki/Polyfill)

### An example polyfill
The code below is a polyfill for the new ES6 String method, startsWith():

```js
if (!String.prototype.startsWith) {
  String.prototype.startsWith = function (searchString, position) {
    position = position || 0;
    return this.substr(position, searchString.length) === searchString;
  };
}
```

As you can see, a polyfill is just regular JavaScript.

This code is a simple polyfill (check it out on MDN), but there's also a significantly more robust one, [here](https://github.com/mathiasbynens/String.prototype.startsWith/blob/master/startswith.js)

#### Quiz Question
Why does the startsWith() polyfill begin with the following line?:

```js
if (!String.prototype.startsWith)
```

1. [ ] Without it, the script would throw an error.
1. [ ] It checks to make sure the `String.prototype` exists.
1. [ ] It avoids overwriting the native `startsWith` method.

#### Solution
Remember that a polyfill is used to patch missing functionality. If the browser supports ES6 and has the native startsWith method, then there's no reason to polyfill it. If this check didn't exist, then this polyfill would overwrite the native implementation.

- [x] It avoids overwriting the native `startsWith` method.

## 8. Polyfill Walkthrough
Remember that a polyfill is used to fill a hole in a browser that doesn't yet support the native feature.

This polyfill starts with a check to see if the native `startsWith` method actually exists. If it does exist then we don't want to override the native version with this one. If it doesn't exist then the browser will then run the code following.

```js
if (!String.prototype.startsWith) {
  String.prototype.startsWith = function (searchString, position) {
    position = position || 0;
    return this.substr(position, searchString.length) === searchString;
  };
}

/* Sample usage */
'Udacity'.startsWith('Udac'); // returns `true`
'Udacity'.startsWith('Udac', 2); // returns `false`
'Udacity'.startsWith('ES6'); // returns `false`
```

This adds a new method to String's prototype object. The function defaults to the position indicated by this second argument that's passed in or it'll be the first character of the string.

Then it returns `true` or `false` if the string that's passed in is the same as the string that we're looking at.

## 9. Other Uses for Polyfills
### Polyfills aren't only for patching missing JavaScript features
JavaScript is the language used to create a polyfill, but a polyfill doesn't just patch up missing JavaScript features! There are polyfills for all sorts of browser features:

- SVG
- Canvas
- Web Storage (local storage / session storage)
- Video
- HTML5 elements
- Accessibility
- Web Sockets
- and many more!

For a more-complete list of polyfills, check out [this link](https://github.com/Modernizr/Modernizr/wiki/HTML5-Cross-Browser-Polyfills)

<!--
## 10. Transpiling
You've probably heard the term compiler before. A compiler is a computer program that takes a program written in some source code language, let's say C++, and then converts it to a target language like machine code.

Running code through a compiler changes its level of abstraction- how close it is to human readable code vs machine runnable code.

So that's compiling. Taking a source language and converting it into a lower level language.

Transpiling is a subset of compiling so it takes source code and converts it into target code - just like a compiler, but the source code and the target code are at the same level of abstraction. Basically if the source code starts out as human readable then the output language will also be human readable.

But why would we want this? Well, we just saw that older browsers do not fully support ES6 but they do support ES5 code. This way we could write our JavaScript using ES6 syntax and
functionality and then use a transpiler to convert it from Es6 code to ES5.

So, we write code using the newest and best but convert it so that it'll run everywhere.
-->