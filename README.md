<!-- markdownlint-disable MD022 MD032 -->
# James Priest

## 100 Days Of Code Log

**Commitment:** ***I will code for at least an hour a day for the next 100 days.***

This is part of Alexander Kallaway's [#100DaysOfCode](https://github.com/Kallaway/100-days-of-code "the official repo") challenge. More details about the challenge can be found here: [100daysofcode.com](http://100daysofcode.com/ "100daysofcode.com").

|  Start Date   | End Date     |
| ------------- | ------------ |
| June 12, 2017 | ------------ |

## Goals

- Code daily
- Expand portfolio
- Hone Git CLI skills
- Get established in the GitHub community
- Get through as many MOOCs, certifications, and bootcamp classes as possible

### Secondary goals

- Pass my Microsoft Programming in HTML5 with JavaScript & CSS3 Certification - [Exam 70-480](https://www.microsoft.com/en-us/learning/exam-70-480.aspx "Exam 70-480: Programming in HTML5 with JavaScript and CSS3")
- Knock out the following...
  - Complete [FCC Front End Development Certification](https://www.freecodecamp.com/james-priest "FCC Profile") program
  - Complete [Udemy The Web Developer Bootcamp](https://www.udemy.com/the-web-developer-bootcamp/ "The Web Developer Bootcamp by Colt Steele") certificate program
  - Complete [Udemy JavaScript: Understanding the Weird Parts](https://www.udemy.com/understand-javascript "JavaScript: Understanding the Weird Parts by Anthony Alicia") certificate program
- Considering...
  - Maybe [Udacity's Front-End Web Developer Nanodegree](https://www.udacity.com/course/front-end-web-developer-nanodegree--nd001?utm_medium=referral&utm_campaign=api) program
  - Maybe [Coding Dojo's Full Stack Developer Bootcamp](http://www.codingdojo.com/web-development-accelerators)

# Log

<!--
## 32. Node.js HTTP Server
### Day 32: August 13 2017 - Sunday

**Projects:**
- Setup a Node.js http server for running web apps locally

**Progress:**
1. Installed simple http-server: `npm install http-server -g`
1. Ran server from local directory `http-server . -p 8000`
1. Tested web app

**Link to work:**
- [https://threejs.org/docs/#manual/introduction/How-to-run-thing-locally](https://threejs.org/docs/#manual/introduction/How-to-run-thing-locally)

**Thoughts:** Found a great article on the [http://threejs.org](http://threejs.org) site that showed how to get a local http server running with any one of the following technologies:

- Python
- Ruby
- PHP
- Node.js
- lighttpd

Use the link on **Link to work:** to read the article

---

## 31. VSCode Debug JS with Node
### Day 31: August 12 2017 - Saturday

**Projects:**
- Debug js code from within Visual Studio Code

**Progress:**
1. Set up Node debug configuration
1. Configured launch.json file
1. Set breakpoints
1. Ran debugger and stepped through code

**Link to work:**
- [https://github.com/james-priest/code-exercises/blob/master/javascript_exercises/js-internals/vm-internals.js](https://github.com/james-priest/code-exercises/blob/master/javascript_exercises/js-internals/vm-internals.js)
- [https://code.visualstudio.com/docs/editor/debugging](https://code.visualstudio.com/docs/editor/debugging)

**Thoughts:** Debugging from within VSCode is absolutely essential to tracking down errors and evaluating code during execution.

---

## 30. My WordPress Site
### Day 30: August, 11 2017 - Friday

**Project:**
- Setup a WordPress site for a blog on the 100 Days of Code challenge

**Progress:**
1. Registered for an account
1. Chose a theme
1. Customized the template (sidebar, header & footer)
1. Wrote my first post!

**Link to work:**
- [https://100daycodeblog.wordpress.com/](https://100daycodeblog.wordpress.com/)

**Thoughts:** So all of this took me 3-4 hours (off and on) and an entire day to do but it's done.😁

While writing a WordPress blog is not something I thought I'd do I am glad I've started the process.  Writing a blog is a surefire way of letting prospective employers know about your mastery, skill set and breadth of knowledge.

I was actually inspired to do a WordPress blog by [@AdrianaHasburn](https://twitter.com/AdrianaHasbun) while reading her [Process to CSS Images](http://adrianahasbun.com/css/the-process-to-css-images) post. (Thanks Ariana!)

---

## 29. Chrome DevTools Workspaces and Source Maps
### Day 29: August 10, 2017 - Thursday

**Project:**
- Setup for Chrome DevTools

**Progress:**
- Read sections on:
  - Code Editor Setup - They recommend Sublime/I use VSCode
  - Persistence with DevTools Workspaces - Setting up source file mapping allows code changes to persist to source files
  - CSS & JS Preprocessors - Using Source Maps allow direct references to preprocessed source files for saving changes directly from DevTools

**Link to work:**
- Link to [DevTools Getting Started Docs](https://developers.google.com/web/tools/setup/)

**Thoughts:** I learned how to effectively use Chrome DevTools as part of my debug process. The combination of VSCode with Chrome DevTools gives me the power and control that Visual Studio 2017 provides for back end development.

---

## 28. JS Closures & Variable Scope
### Day 28: August 8, 2017 - Tuesday

**Progress:**
- My goal was to create an object literal that contained a recursive function wrapped in a closure.
- Worked on this for days before I got it right!

```javascript
// my five year old nephew's favorite joke...
var comedian = {
    pauseReps: 3,
    pauseTime: 2000,
    setupJoke: function() {
        console.log("What's invisible and smells like carrots...");
    },
    timeThePunchLine: function () {
        var pauseRep = this.pauseReps;
        var pauseTime = this.pauseTime;
        var punchLine = this.punchLine;

        function timeoutHandler() {
            if (pauseRep == 0) {
                console.log(punchLine());
                return;
            } else {
                console.log(".");
                pauseRep--;
                setTimeout(timeoutHandler, pauseTime);
            }
        }

        timeoutHandler();
    },
    punchLine: function() {
        return "bunny farts.😲😂😐";
    }
};

var myNephew = comedian;
myNephew.setupJoke();
myNephew.timeThePunchLine();
```

**Link to work:** [https://codepen.io/james-priest/pen/EvydgE?editors=1011](https://codepen.io/james-priest/pen/EvydgE?editors=1011)

**Thoughts:** I read three articles by Kirupa ([@Kirupa on Twitter](https://twitter.com/kirupa)) of [http://www.kirupa.com](http://www.kirupa.com) that helped explain the concepts I needed to have down before successfully combining closures with object literals, recursion, variable hoisting, and scope chaining. They were from the [Learn JavaScript 101](https://www.kirupa.com/javascript/learn_javascript.htm) section of the site. These were:

- [Variable Scope in JavaScript](https://www.kirupa.com/html5/variable_scope_js.htm)
- [Variable and Function Hoisting](https://www.kirupa.com/html5/hoisting.htm)
- [Closures in JavaScript](https://www.kirupa.com/html5/closures_in_javascript.htm)

I also got syntactic help from here [https://stackoverflow.com/questions/25889950/settimeout-and-recursive-function-with-parameters](https://stackoverflow.com/questions/25889950/settimeout-and-recursive-function-with-parameters).


## 27. Updated GitHub Page for my 100DaysOfCode log
### Day 27: August 6, 2017 - Sunday

**Progress:**
- Updated CSS, jQuery, and Jekyll HTML template

**Link to work:**
- [https://james-priest.github.io/100-days-of-code-log/](https://james-priest.github.io/100-days-of-code-log/)

**Thoughts:**
- Needed to come up with a way of expanding the nav to accommodate a long TOC

---

## 26. Updated My CV site
### Day 26: August 5, 2017 - Saturday

**Progress:**
- Added jQuery Nav
- Added FontAwesome
- Updated icons & links to my various social media & online profiles .

**Link to work:**
- [https://james-priest.github.io](https://james-priest.github.io/ "My online CV")

**Thought:**
- Used jQuery for on-page navigation; dynamic building of the TOC & for basic usability: breadcrumbs, highlights, etc.

---
-->

## 25. Objects, Expressions & Closures, Oh My!
### Day 25: August 3, 2017 - Wednesday

**Today's Challenge:**
- I set out to define different JavaScript constructs that incorporate recursion, setTimeout, and a closure.

**Progress:**
- Set up two test environments for tracing and debugging
  - CodePen for quick proof-of-concept testing
  - VSCode to run Node & step through code using debugger.

**Link to work:**
- [CodePen - setTimeout Patterns](https://codepen.io/james-priest/pen/jLmxvZ "https://codepen.io/james-priest/pen/jLmxvZ")
- [GitHub - setTimeout-patterns.js](https://github.com/james-priest/code-exercises/blob/master/javascript_exercises/design-patterns/closure/setTimeout-patterns.js)

**Thoughts:** This was not easy.😓 I initially wrote this as a Pen but needed additional debug info to trace scope so I also ran this with Node in the integrated Bash terminal I have going inside of VSCode.

I had read a great post from [@Kirupa](https://twitter.com/kirupa) that discussed IIFEs & scope. [Kirupa: Immediately Invoked Function Expressions a.k.a IIFEs](https://www.kirupa.com/html5/immediately_invoked_function_expressions_iife.htm)

Example 1: setTimeout in IIFE
```javascript
var reps = 3;

(function doStuff() {
    if (reps == 0)
        return;
    console.log(reps);

    reps--;
    setTimeout(doStuff, 1000);
})();
```

Example 2: setTimeout in object literal
```javascript
var obj2 = {
    count: 3,
    repeat: function () {
        // bring vars down here so inner function can contain the variable count in it's closure scope
        var enclosedCount = this.count;
        
        function doSomething() {
            if (enclosedCount == 0) {
                return;
            } else {
                console.log(enclosedCount);
                enclosedCount--;
                setTimeout(doSomething, 1000);
            }
        }

        doSomething();
    }
};

var inst = obj2;
inst.repeat();
```

Example 3: setTimeout in function expression
```javascript
var myFunc = function () {
    
    var outer = 3;

    function doStuff() {
        var inner = 3;
        if (outer == 0) {
            return;
        } else {
            for (; inner> 0; inner--) {
                console.log("in: " + inner);
            }
            console.log("outer: " + outer);
            outer--;
            setTimeout(doStuff, 1000);
        }
        
    }

    doStuff();
    return "done"; // occurs after first loop completes. Use Async?
};

var doIt = myFunc();
console.log(doIt);
```

---

## 24. CodePen Lesson!
### Day 24: August 2, 2017 - Wednesday

**Today's Project(s):**
- Creating some proof of concept pens and testing out the environment

[![Plunker](/assets/images/codepen-singleton-pattern.png)](https://codepen.io/james-priest/pen/PKmMzP?editors=1111)

**Progress:**
- Set up my profile
- Created two test pens & a prototyping pen
  - saved all progress
  - had one pen open in two different tabs (my bad); closed one tab & saved the other
  - overwrote my work by saving "wrong" tab. 😠😭

So I rewrote the proof-of-concept code from memory.

**Link to work:**
- [https://codepen.io/james-priest/pen/PKmMzP?editors=1011](https://codepen.io/james-priest/pen/PKmMzP?editors=1011)

**Thoughts:** So, I learned that CodePen doesn't have version control. This makes me real careful and deliberate with my changes.

In the end it turned out fine. By re-coding the exercise I inadvertently ended up employing a learning technique called Spaced Repetition.😁

---

## 23. JSBin vs. Plunker vs. CodePen
### Day 23: Aug 1, 2017 - Tuesday

**Today's Project(s):**
- Evaluated JSBin, Plunker and CodePen.

**Progress:**
- Set up accounts in each
- Created Gists from which to save and pull my code
- Tested out each code environment 

**Link to work:**
- [JSBin](http://jsbin.com/?html,js,output)
- [Plunker](https://plnkr.co/edit/?p=catalogue)
- [CodePen](https://codepen.io/)

**Thoughts:** Here are my two cents...

[![JSBin](/assets/images/jsbin.png)](http://jsbin.com/howuzec/3/edit?html,js,output)
**JSBin** - This is my goto js playground for testing syntax & short proof-of-concepts
- Pros
  - quick setup
  - Console tab is predominantly featured - great for quick debug
  - version control - multiple snapshots
- Cons
  - AutoSave and snapshots are clunky to use/administer; they require manual steps to keep organized
  - Gists don't import/export right
  - loading & switching bins is slow & errs at times
  - collaboration does not work as advertised
  - less used features are not/is not inherently intuitive.
  - editor is limited to one html, css & js file

[![Plunker](/assets/images/plunker.png)](https://plnkr.co/edit/O73CdaJyTJenpBshvjzR?p=info)
**Plunker** - great multi-file environment
- Pros
  - Editor is spacious
  - can have multiple js, css, html & md files in a plunk
  - saved templates, multiple libraries, integrated gitter, live preview
  - multiple js frameworks available
  - version control, linting, chat, toolbox, and collaboration
- Cons
  - no integrated Console

[![CodePen](/assets/images/codepen.png)](https://codepen.io/james-priest/pen/jLmxvZ)
**CodePen** - great UX (fully featured experience)
- Pros
  - Intuitive and configurable ui
  - Pen or Project based workspace
  - clean & focused documentation
  - great social factor - huge community, profile setup & ability to post
- Cons
  - no version control - easy to overwrite saved version with old version

Beyond what I listed, CodePen is designed right. It just works - it "feels" good to use, its responsive, it's intuitive, and it's robust which means it doesn't seem to choke as easily as some others.

In the end, it's the design that makes CodePen attractive.

>"Design is how something works, not what it looks like." - Steve Jobs

---

## 22. JavaScript VM Internals
### Day 22: July 31, 2017 - Monday

**Today's Project(s):** Watched Arindam Paul's YouTube vid: [JavaScript VM Internals, Event loops, Async and Scope Chains](https://youtu.be/QyUFheng6J0)

**Progress:** Followed along with the video and coded the proof of concepts 

**Link to work:**
- [https://github.com/james-priest/code-exercises/tree/master/javascript_exercises/js-internals](https://github.com/james-priest/code-exercises/tree/master/javascript_exercises/js-internals)

**Thoughts:** JavaScript goes through a two phase process when a program is run. Phase one is the _compilation phase_ and phase two is the _execution phase_. The compiler actually alternates between these two phases as it digs deeper into nested functions. These nested function environments are referred to as _local scope_ or _lexical scope_ (The scope of the variable can be defined by its position in the source code).

When JavaScript goes through the _compilation phase_ it actually just extracts out declarations - the variable declarations and the function declarations (the value doesn't matter at this point). It moves them to the top of the code block and then prepares the memory so that it can execute the code. It is through this extraction that variable hoisting occurs.

Let's look at this example...

(column 1 & columns 3: _compilation phase_; column 2 & column 4: _execution phase_)

```javascript
 1 var a = 2;             // Global Scope (Window)
 2 b = 1;                 // a | a=2    |   |
 3                        // f | f="λf" |---|------> Lambda "f"
 4 function f(z) {        //   | b=1    |   | b=3    ('b' created at runtime)
 5     b = 3;             //   |        |   | c=4
 6     c = 4;             // ------------------------
 7     var d = 6;
 8     e = 1;             // Local execution scope for f()
 9                        // z | z=1    |   |
10     function g() {     // d | d=6    |   | d=18
11         var e = 0;     // g | g="λg" |---|------> Lambda "g"
12         d = 3 * d;     //   | e=1    |   |
13         return d;      // ------------------------
14     }
15                        // Local execution scope for g()
16     return  g();       // e | e=0
17     var e;             // ------------------------
18 }
19
20 f(1); //18
```

The compiler goes through the global scope, extracts the declarations `a` and `f` (column 1). It does not know what `b` is referring to at this point so it skips it. It then checks `f` for syntax, saves the contents of `function f` as a string blob - `Lambda "f"`, and then skips to line 18. This concludes the _compilation phase_ which then immediately kicks off the _execution phase_. This is where values are assigned to `a` and `f`. `b` is created at runtime and assigned a value as well (column 2).

Code execution continues onto line 20, `function f` is executed and the compiler creates a memory allocation in heap for `f` which can be thought of as a _local execution context_. This is where it enters into `f` and starts the _compilation phase_ once again. As soon as the compiler sees `z` as the function parameter, it declares it as a local variable. `b` and `c` are skipped over and `d` is declared. `e` is skipped and `g` is declared. Finally `e` on line 17 is declared before the _execution phase_ begins. This declaration of `e` is an example of variable hoisting because it occurs after the assignment in code but is actually _hoisted_ to be declared before execution. This concludes the _compilation phase_ for `f`.

We now enter the _execution phase_ for `f`. The first thing that happens is the value passed to `f` is assigned to the variable declaration `z`. JavaScript then encounter an assignment to `b` which it has no local reference to. It then checks it's stack pointer back to the parent function to see if `b` exists there (which it does) and then happily assigns `b` the new value of 3.

During the _execution phase_ JavaScript will follow the pointer chain all the way back to global scope looking for the referenced variable regardless of how many scope chains it has to go through. If it finds the variable before reaching global scope it will assign the value. If not, it will create the variable in global scope and then assign the value. This is what happens with variable `c` during execution.

Next, `d` is assigned the value of 6 followed by `e` being assigned the value of 1. `g` is then assigned the contents of `function g` as a string blob before line 16 is reached where the code says, "function g, execute self". At this point a heap memory allocation is created as a _local execution context_ for `g`. We then enter the _compilation phase_ for `g`. 

At this point the _compilation phase_ for `g` creates a pointer back to the _local execution scope_ for `f`. `e` is declared and that is all that happens in the _compilation phase_ for `g`.

The _execution phase_ for `g` looks for a local reference to `d` which it does not find so it goes up the scope chain and finds it it in the lexical scope of `f`. It then assigns `d` the value of 18 before hitting line 13 where it actually returns the value of  `d` which is 18. Execution context then continues to line 16 where `g()` is replaced with the value 18 which is then returned back to `f(1)` on line 20.

After F of 1 is done there is no reachability or reference to anything other than the Global scope. In JavaScript, if you have an object, or a function definition, or a function execution, or any other type of thing, if you do not have a way to reach it, it will be garbage collected.

---

## 21. JS Namespace Patterns
### Day 21: July 30, 2017 - Sunday

**Progress:**
- Practiced creating various namespace objects
- Created namespace objects with different singleton conventions

```javascript
// Option 1
var myApp = myApp || {};

// Option 2
if (!myApp) { myApp = {}; }

// Option 3 - useful only in a parameter/argument scenario
window.myApp || (window.myApp = {});

// Option 4 - jQuery plug-in
var myApplication = $.fn.myApplication = function () { };

// Option 5 - Long form (unnecessary)
var myApplication = myApplication === undefined ? {} : myApplication;
```

**Link to work:**
- [https://github.com/james-priest/code-exercises/tree/master/javascript_exercises/design-patterns/namespace](https://github.com/james-priest/code-exercises/tree/master/javascript_exercises/design-patterns/namespace)

**Thoughts:** Played with six different namespace design patterns. These incorporated a Singleton pattern to ensure one (and only one) instance is ever created. Some used coercion to test if an instance already existed, some instantiate an empty object and add properties to the object after the fact. Some define/declare the entire namespace object as an object literal. Some use IIFEs to immediate invoke and return  an object.

---

## 20. Singleton Design Pattern with IIFEs
### Day 20: July 28, 2017 - Friday

**Today's Project(s):**
- Singleton pattern using Immediately Invoked Function Expression (IIFE)

**Progress:**
- Read [The Singleton Pattern](https://addyosmani.com/resources/essentialjsdesignpatterns/book/#singletonpatternjavascript) in Addy Osmani's Essential JavaScript Design Patterns.

**Link to work:**
- [https://github.com/james-priest/code-exercises/blob/master/javascript_exercises/design-patterns/singleton/global-instance-iife.js](https://github.com/james-priest/code-exercises/blob/master/javascript_exercises/design-patterns/singleton/global-instance-iife.js)

**Thoughts:** Read a great post by [@kirupa](https://twitter.com/kirupa "Twitter profile") of [http://kirupa.com](http://kirupa.com) called [Immediately Invoked Function Expressions (aka IIFE)](https://www.kirupa.com/html5/immediately_invoked_function_expressions_iife.htm)  this is part of his site's [Learning JavaScript 101](https://www.kirupa.com/javascript/learn_javascript.htm) section.

Writing the function by following a pattern is pretty straight forward.  The key is to
1. understand what's going on under the hood
1. know when to use it
1. know why you're using it

Here are the key take-aways about IIFEs from @kirupa:
- The function executes in its own bubble. It comes into existence, does its work, and then disappears. No reference is created to the function so there's no way to access it after execution.
- An IIFE leaves behind no evidence of its existence after it has run. This is largely because IIFEs are anonymous functions that are nameless.
- Because the code runs in it's own function scope it's protected from accidental modification by code outside of it.
- IIFEs are great for protecting the IIFE code from the rest of your js, but they don't stop your IIFE code from wreaking havoc on the code outside of your IIFE.
- It executes immediately. No waiting time and no instantiating a var to then invoke the function with.
- Side Note: The reason the function executes immediately is because the compiler is ~~tricked~~ told to treat the function, which is normally just a _declaration_, as an _expression_.
- There are ways other than using wrapping parentheses to reach a valid point in the grammar so that your function is treated as an expression. (Although, parens should be used for readability since they are the convention)
  - void function(e){ console.log(e) }('hi')
  - !function(e){ console.log(e) }('hi')
  - typeof function(e){ console.log(e) }('hi')

![Singleton with IIFEs](/assets/images/vscode-singleton-iife.png)

---

## 19. JS Object Literals
### Day 19: July 27, 2017 - Thursday

**Today's Project(s):**
- Object literals

**Progress:**
- Created three types of objects using object-literal notation.

**Link to work:**
- [https://github.com/james-priest/code-exercises/tree/master/javascript_exercises/design-patterns/object-literals](https://github.com/james-priest/code-exercises/tree/master/javascript_exercises/design-patterns/object-literals)

**Thoughts:** Object literals are a beautiful way to organize your code. It uses key/value pairs and nests well for deeper hierarchies. It also reads well and is easy to understand if structured properly.

![Object Literal Notation](/assets/images/vscode_object_literals.png)

---

## 18. Npm, packages and scripts
### Day 18: July 26, 2017 - Wednesday

**Today's Project(s):** Set up a js project environment

**Progress:**

- set up a `package.json` file through `npm init`
- added dev-only and runtime packages through `npm install --save-dev` and `npm install`
- used `npm uninstall` and `npm update`
- created _build_, _test_, _prepublish_ and _flow_ scripts
- used `npm run`

**Link to work:**
- [https://github.com/james-priest/code-exercises/blob/master/package.json](https://github.com/james-priest/code-exercises/blob/master/package.json)

**Thoughts:** I love npm and its documentation. Organized well. Super simple. Intuitive.

---

## 17. Flow testing
### Day 17: July 25, 2017 - Tuesday

**Today's Project(s):**
- Flow JavaScript type checker

**Progress:**
- Completed installation & testing

**Link to work:**
- [https://github.com/james-priest/code-exercises/tree/master/javascript_exercises/flow](https://github.com/james-priest/code-exercises/tree/master/javascript_exercises/flow)

**Thoughts:**
- Flow was put out by Facebook and it allows static type checking of JavaScript code as well as a deeper capability to make smart decisions by understanding the code at a deeper level.

---

## 16. ESLint testing
### Day 16: July 24, 2017 - Monday

**Today's Project(s):**
- ESLint - config, fine-tune, & test

**Progress:**
- installed globally and as a dev dependency
  - `npm install -g eslint@latest`
  - `npm install eslint@latest --save-dev`
- created `.eslintrc.json` in script `./src` directory and a global config in my home directory
  - `eslint --init`
- run
  - `eslint a.js`
- installed VSCode ESLint extension
- Test Playground: [http://eslint.org/demo/](http://eslint.org/demo/)

**Link to work:**
- [https://github.com/james-priest/code-exercises/tree/master/javascript_exercises/linting#eslint](https://github.com/james-priest/code-exercises/tree/master/javascript_exercises/linting#eslint)

**Thoughts:** This was the third linter I tried and looks to be the most flexible. I like the extensibility capabilities and ability to choose between various different style guides.

---

## 15. JSHint testing
### Day 15: July 23, 2017 - Sunday

**Today's Project(s):**
- Linting with JSHint

**Progress:**
- installed globally
  - `npm install -g jshint@latest`
- created `.jshintrc` in my home directory & `./src` directory
  - configured using [docs](http://jshint.com/docs/options/) and this [reference](https://github.com/jshint/jshint/blob/master/examples/.jshintrc)
- run
  - `jshint a.js`
- installed VSCode JSHint extension
- [http://jshint.com](http://jshint.com) has a configurable code test playground on the homepage

**Link to work:**
- [https://github.com/james-priest/code-exercises/tree/master/javascript_exercises/linting#jshint](https://github.com/james-priest/code-exercises/tree/master/javascript_exercises/linting#jshint)

**Thoughts:**
- Configuring JSHint required that I learn & understand the various JavaScript pitfalls developers run into so I can understand why each recommendation is made by JSHint. Things like no `for..in` iterators, use of the `new` keyword and `"option strict"` for functions.
- [http://jshint.com](http://jshint.com) has a configurable code test playground on the homepage for quick code block tests

---

## 14. JSLint testing
### Day 14: July 21, 2017 - Friday

**Today's Project(s):**
- JSLint command line linting

**Progress:**
- Did an npm global install.

**Link to work:**
- [https://github.com/james-priest/code-exercises/tree/master/javascript_exercises/linting#jslint](https://github.com/james-priest/code-exercises/tree/master/javascript_exercises/linting#jslint)

**Thoughts:** This is the granddaddy of them all and was originally written by Douglas Crockford in 2002 with the latest stable version released in 2011. It offers no config and is highly opinionated as to what "The Good Parts" are. See [JavaScript: The Good Parts](http://bdcampbell.net/javascript/book/javascript_the_good_parts.pdf "Book in pdf"). Still, this is the staple linter to use if you are just starting out and want to see where it all began. Simple install. No configuration needed.

---

## 13. Jekyll Build Environment
### Day 13: July 20, 2017 - Thursday

**~~Today's~~ Last Week's Project(s):**

- Created Jekyll Build Environment on Ubuntu 16.04. This is for testing locally before committing changes to GitHub Pages.

**Progress:**

- Completed the following
  1. Spun up a Linux VM
  1. Installed, configured & updated Ubuntu
  1. Installed Nodejs, NPM, Git, Ruby, RubyGems, Bundle, Jekyll, Visual Studio Code & Chrome
  1. Cloned my Personal Page repo from GitHub
  1. Started Jekyll server - `bundle exec jekyll serve` - this watches for changes to code or content and rebuilds the site when it detects any. It also runs a lightweight http server to view changes on the fly. Pretty cool!
  1. Started local development & testing

**Link to work:**

- [README.md](https://github.com/james-priest/james-priest.github.io/blob/master/README.md "Link to GitHub README.md") from my Personal Page. This is the raw source that the template engine uses to build the site.
- [Generated Site](http://james-priest.github.io "Link to my GitHub Personal Page") This is the Jekyll static site that's generated on GitHub whenever I update, commit and push my README.md.

**Thoughts:**

- This was a good exercise in building a complete end-to-end dev solution.
- I started with `jekyll-theme-leap-day`, one of GitHub's officially supported templates and made modifications to the html, css, & javascript.
- This also gave me a good opportunity to practice Bash shell scripting, npm package management and VS Code plug-in configuration

---

## 12. Finished jQuery on FCC
### Day 12: July 12, 2017 - Wednesday

**Today's Project(s):**

- Free Code Camp exercises - jQuery manipulation of DOM

**Progress:**

- Steady... I finished the jQuery section today

**Link to work:**

- [My FCC Code Portfolio](https://www.freecodecamp.com/james-priest "james-priest's code portfolio on FreeCodeCamp")

**Thoughts:**

- I've now finished up the following FCC sections:
  - HTML5 and CSS
  - Responsive Design with Bootstrap
  - jQuery
- Next are the two Front End Development Projects to test the skills learned. These are:
  - Build a Tribute Page
  - Build a Personal Portfolio Webpage

---

## 11. Windows 10, Ubuntu 16.04, Jekyll, & GitHub Pages
### Day 11: July 9, 2017 - Sunday

**~~Today's~~ This Week's Project(s):**

- FCC Code Challenges
- Created GitHub personal page
  - Cloned repo
  - Followed this process: _work locally, push changes, review & repeat..._
  - Decided to get the Jekyll static site generator runnung locally so I don't have to push changes live in order to view/test them
  - Docs said to enable Bash on Ubuntu on Windows 10... I'm running a highly customized Windows 8.1. 😣
- Upgraded VMware Workstation to version 12.5.7
- Upgraded virtual instance of Ubuntu 9.10 to 14.04
  - this upgrade choked miserably and required lots of manual fixes
  - had to fix bootloader
  - reset passwords
  - reinstall display drivers, etc...
- Installed FRESH copy of Ubuntu 16.04 in a VM - all went well 😅
- Installed a fresh copy of Windows 10 Pro Creators update in a VM - so far so good 😊
- Sync'd bookmarks across browsers (Chrome, FF, Edge, Safari) and platforms (Win, Linux, Mac) with [Xmarks](http://xmarks.com)
  - This plugin is awesome. It works with the synchronization that Google, Microsoft & Firefox do within their browsers but you have to turn off bookmark sync for theses and let Xmarks do the Bookmark sync. I run many VMs so this works great to keep everything in check.
- Windows 7 VM
  - Streamlined OS - removed hibernation and paging. Returned them after defragmentation of virtual disk
  - Uninstalled unnecessary applications, removed duplicate data and removed old snapshots for smaller disk footprint
  - Reduced vmdk (virtual disk) size to reclaim space
- Ubuntu 16.04 VM
  - Installed & updated all default packages
  - installed vmware tools for host/guest OS integration
  - apt-got git, ruby, rubygems, jekyll and nodejs 😉
  - now I'm ready to clone my GitHub portfolio page and go to town
- Windows 10 VM
  - Researched, installed, & configured OS features. Now I'm testing, modifying and evaluating.
  - Holding off on upgrading host OS until I can make sure all 8.1 customizations will transfer/upgrade gracefully.
  - Enabled _Developer mode_ in VM hosted instance of Win 10
  - Installed `Windows Subsystem for Linux` which is basically an Ubuntu-based Bash shell for Windows. Yay! 👏😍

**Progress:**

- Continued jQuery DOM manipulation exercises of FCC
- Started online portfolio / resume / profile on GitHub

**Link to work:**

- [My FCC Code Portfolio](https://www.freecodecamp.com/james-priest "james-priest's code portfolio on FreeCodeCamp")
- My Online Resume and personal page: [https://james-priest.github.io/](https://james-priest.github.io/)

**Thoughts:**

- Getting my personal GitHub page going was way more involved than I thought it would be. To be fair, it's very straight forward to choose a theme and set up a personal page on GitHub. Customizing requires a bit more. Here are the steps I took:
   1. Created a repo for my personal account profile page and named it `james-priest.github.io`.
   1. Went into Settings for that repo and turned on GitHub Pages and chose a theme.
   1. Modified the README.md
- So far so good! This would have been it if I didn't need a higher level of customization. Fortunately, GitHub provides [very clear docs](https://help.github.com/articles/using-jekyll-as-a-static-site-generator-with-github-pages/ "Using Jekyll as a static site generator with GitHub Pages") on how to modify the CSS (scss), HTML, and create a local dev environment with Jekyll - a Ruby-based static site generator. This allows you to modify and preview without a commit to GitHub for each change. So here are the remaining steps:
  1. Upgrade my OS to Win10 to use the integrated bash shell
  1. Install ruby, gems, git & jekyll
  1. Clone repo & then it's: modify (VS Code), build (Jekyll), test (local) & deploy (git) 
- I'll finish those this week.

---

## 10. GitHub Page for this log
### Day 10: July 4, 2017 - Tuesday

**Today's Project(s):**

- Created GitHub Page for this repo and code log
- Watched [Intro to ASP.NET Core 1.1](https://mva.microsoft.com/en-US/training-courses/introduction-to-asp-net-core-1-0-16841) on Microsoft Virtual Academy

**Progress:**

- Completed the setup of a GitHub Page for this log
- Got about halfway through Intro ASP.NET Core training

**Link to work:**

- [100 Days of Code Log GitHub Page](https://james-priest.github.io/100-days-of-code-log/)  (this page)

**Thoughts:**

Created the GitHub Page through GitHub. It uses Jekyll and one of the pre-built templates. It also add a yaml file. I may look into how to modify the template in order to correct for limited number of links on the sidebar as well as modification of the top nav bar

The Intro to ASP.NET Core class is great. It's hosted by Scott Hanselman and Maria Naggaga. I love both of them. I can't wait to finish the FCC Front End Development cert so I can switch to .NET Core Back End with C#.

---

## 9. JavaScript Array Methods
### Day 9: July 2, 2017 - Sunday

**Today's Project(s):**

- javascript-array-methods - Vanilla JavaScript project to show what each JS Array object method does
- FCC Code Challenges

**Progress:**

- Completed migration of javascript-array-methods v1.0.0 to GitHub
- Started jQuery selector section of FCC

**Link to work:**

[![https://gyazo.com/0a5f8557493931c87ebf87e9cabcfb85](https://i.gyazo.com/0a5f8557493931c87ebf87e9cabcfb85.png)](http://javascript-array-methods.netlify.com/)

- [JavaScript Array Methods](https://github.com/james-priest/javascript-array-methods "GitHub repo") on  GitHub - click image to see demo
- [My FCC Code Portfolio](https://www.freecodecamp.com/james-priest "james-priest's code portfolio on FreeCodeCamp")

**Thoughts:** Finally good to get the JavaScript Array Methods app up on GitHub. Next I need to modify it to use Bootstrap and Objects to hold data rather than arrays.

---

## 8. Code & Dev activities
### Day 8: June 30, 2017 - Friday

**~~Today's~~ Last Week's Project(s):**

- FCC Code Challenges
- Received and accepted an invitation to join [**DWYL**](https://github.com/dwyl "Do What You Love") on GitHub
- Added projects and people to my [Stars](https://github.com/james-priest?tab=stars) & [Following](https://github.com/james-priest?tab=following) tabs on GitHub
- Signed up for [Netlify](http://netlify.com) - they host static sites through CLI deploy. npm install and deploy any repo
- Researched Back End learning path and decided on .NET Core since its going to be the high💲dollar💲 technology for 2018. Read the ASP.NET Core [prediction](https://stackify.com/net-core-csharp-next-programming-language/ "Why .NET Core and C# are the Next Big Thing") about how it will be the next big thing. I also know & love the MS development environment.
- Retooled my dev environments:
  - Updated Visual Studio 2017 to Enterprise and v15.2
  - Got my VS Code plugins in line
  - Installed [notepad2](https://xhmikosr.github.io/notepad2-mod/) (great notepad replacement)
- Evaluated many of the Code Playgrounds out there to solve for two needs:
  - having a place to test code as I go through tutorials
  - having a place to organize and  host samples of work
- Decided to set up a [GitHub repo](https://github.com/james-priest/code-exercises "code-exercises") to contain my source code instead. I'll still use JSBin for quick JS, ES6 and TypeScript tests.
- Created additional repos to migrate my test projects to:
  - [code-exercises](https://github.com/james-priest/code-exercises)
  - [javascript-array-methods](https://github.com/james-priest/javascript-array-methods)
  - [web-calculator](https://github.com/james-priest/web-calculator)
- Researched [Open Source Friday](https://opensourcefriday.com/), [FirstTimersOnly](http://www.firsttimersonly.com/) movement and [How to Contribute](https://opensource.guide/how-to-contribute/ "") in Open Source
- Got caught in a rabbit hole of learning regarding JavaScript concepts, HTML5 api features & Google Web articles. Covered the following:
  - [Functional Composition](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-function-composition-20dfb109a1a0 "Master the JavaScript Interview: What is Functional Composition?")
  - [Closures](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-closure-b2f0d2152b36 "Master the JavaScript Interview: What is a Closure?")
  - [Hoisting](https://dev.to/imwiss/understanding-hoisting-in-javascript "Understanding Hoisting in JavaScript")
  - [Service Workers](https://developers.google.com/web/fundamentals/getting-started/primers/service-workers "Service Workers: An Introduction") or Web Workers
  - [Promises](https://developers.google.com/web/fundamentals/getting-started/primers/promises)
  - App Cache, Local Storage, Sessions Storage, IndexedDB & Web SQL
  - [Chrome Dev Tools](https://developers.google.com/web/tools/chrome-devtools/)
  - Researched Google's [Material Design](https://material.io/guidelines/material-design/introduction.html "Introduction to Material Design")
  - Read through Google Codelabs - [Your First PWA](https://developers.google.com/web/fundamentals/getting-started/codelabs/your-first-pwapp/ "You First Progressive Web App") and [Your First Offline Web App](https://developers.google.com/web/fundamentals/getting-started/codelabs/offline/)
  - Read about [CSS Grid vs. Flexbox](https://tutorialzine.com/2017/03/css-grid-vs-flexbox "CSS Grid vs. Flexbox: A Practical Comparison")

**Progress:**

- Completed Responsive Design with Bootstrap section of FCC! 😃

**Link to work:**

- [My FCC Code Portfolio](https://www.freecodecamp.com/james-priest "james-priest's code portfolio on FreeCodeCamp")

**Thoughts:** All this research and learning was great and necessary but it ate up another week's worth of "code" time. I'm not worried about it though.  I've come to the conclusion that it all moves me towards the same ends.

I also don't trip on whether I'm doing a tutorial or coding something from scratch. It's all development time and one usually proceeds the other if I'm going to employ the most effective learning style.

The one challenge I need to get in check is following through to the end of one project, learning path, or class with a single mindedness of purpose before getting distracted or caught up in another. I feel I might be missing something if I don't investigate and dig deep into a concept I don't fully understand. This is the thinking that gets me spread out with 10 browser instances of 20 open tabs each and then scrambling to keep it all straight. [OneTab Chrome extension](https://www.one-tab.com/ "Reduces tab clutter and memory footprint by 95%") is **great** for this.

Bottom line is I'm making progress and learning how to organize and keep 10 plates spinning at any given time. The next soft skill to incorporate will be the concept of _balance_!

---

## 7. Bootstrap Responsive Design
### Day 7: June 24, 2017 - Saturday

**Today's Project(s):**

- FCC Code Challenges

**Progress:**

- Started Responsive Design with Bootstrap section of FCC

**Link to work:**

- [My FCC Code Portfolio](https://www.freecodecamp.com/james-priest "james-priest's code portfolio on FreeCodeCamp")

**Thoughts:** It's easy for me to get distracted with any one of the six different projects I'm working on at the same time.  I need to limit my WIP in order to make consistent headway.

---

## 6. Hoisting, Closures, and Module Patterns
### Day 6: June 22, 2017 - Thursday

**Today's Project(s):**

- FCC Code Challenges
- Learned about closures & module patterns in JavaScript

**Progress:**

- Finished the Gear Up for Success section of FCC (Joined FCC forum, Linked-In Alumni Network & Free Code Camp Group in Pasadena)

**Link to work:**

- [My FCC Code Portfolio](https://www.freecodecamp.com/james-priest "james-priest's code portfolio on FreeCodeCamp")
- [Understanding Hoisting in JavaScript](https://dev.to/imwiss/understanding-hoisting-in-javascript)
- [What is a Closure](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures)
- [JavaScript Module System Showdown: CommonJS vs AMD vs ES2015](https://t.co/l3SLLnxvZf "JavaScript article on auth0.com")

**Thoughts:** I'm taking time to read about technologies, methodologies and language conventions. Right now it's a jumble of information but I know eventually it will all start to click and make sense.

---

## 5. HTML & CSS in FreeCodeCamp
### Day 5: June 20, 2017 - Tuesday

**Today's Project(s):**

- FCC Code Challenges

**Progress:**

- Finished the HTML5 & CSS section

**Link to work:**

- [My FCC Code Portfolio](https://www.freecodecamp.com/james-priest "james-priest's code portfolio on FreeCodeCamp")

**Thoughts:** So I skipped 5 days of postings & tweets but still was productive in my studies. I spend 8-10 hours in front of the computer daily; sometimes its directly related to learning and code challenges but half the time it's about reading about a new technology or configuring my dev environment or fine-tuning a process. It's constant learning and applying that knowledge.

The key is to get and find efficiencies in your daily process and turn those into routine...

---

## 4. HTML5 Exercises
### Day 4: June 15, 2017 - Thursday

**Today's Project(s):**

- FCC Code Challenges

**Progress:**

- Completed some form element exercises
- Completed css class & id selectors

**Link to work:**

- [My FCC Code Portfolio](https://www.freecodecamp.com/james-priest "james-priest's code portfolio on FreeCodeCamp")

**Thoughts:** Today was a little light on the workload. It's funny how I can spend ALL day on the computer do code-related activities without actually coding. :/ Go figure...

The important thing is that I did get something done and posted. I'm keeping it pushin...

---

## 3. My Personal Kanban
### Day 3: June 14, 2017 - Wednesday

**Today's Project(s):**

- Kanban board
- FCC Code Challenges

**Progress:**

- Got going on my Kanban board

**Link to work:**

- [My FCC Code Portfolio](https://www.freecodecamp.com/james-priest "james-priest's code portfolio on FreeCodeCamp")

**Thoughts:** This took a little while to get started on.  I'm reading Personal Kanban by Jim Benson. Here's a link to the companion site: [Personal Kanban](http://www.personalkanban.com/pk/ "Short Overview and YouTube video of Personal Kanban").

![My Kanban Board](/assets/images/KanbanBoard.jpg "My Kanban board")

---

## 2. My Time Map
### Day 2: June 13, 2017 - Tuesday

**Today's Project(s):**

- Time Map - My Daily Code Schedule
- FCC Code Challenges

**Progress:**

- Wrapped up Time Map

**Link to work:**

- [My FCC Code Portfolio](https://www.freecodecamp.com/james-priest "james-priest's code portfolio on FreeCodeCamp")

**Thoughts:** Today's work was more organizational and productivity-based in nature but necessary nonetheless. It took me a while to come up with an aggressive but reasonable schedule.

My goal is to do 4 Pomodoros for each two-hour Study block (in blue).

![Time Map Schedule](/assets/images/TimeMap.jpg)

---

## 1. The Web Developer Bootcamp
### Day 1: June 12, 2017 - Monday

**Today's Project(s):**

- FCC Code Challenges
- Udemy's [The Web Developer Bootcamp](https://www.udemy.com/the-web-developer-bootcamp/ "Web Developer Bootcamp Udemy Course by Colt Steele") course

**Progress:**

- More CSS on FCC
- set font styles

**Link to work:**

- [My FCC Code Portfolio](https://www.freecodecamp.com/james-priest "james-priest's code portfolio on FreeCodeCamp")

**Thoughts:** Signed up for Colt Steele's [The Web Developer Bootcamp](https://www.udemy.com/the-web-developer-bootcamp/ "Web Developer Bootcamp Udemy Course by Colt Steele") course at Udemy today. I'm looking forward to using the bootcamp along side FCC as part of my dev program. Apparently folks are doing this with [good results](https://forum.freecodecamp.com/t/the-web-developer-bootcamp-udemy-review/61595/8 "Review of Web Developer Bootcamp").

It'll go something like this:

1. Watch video
1. Code the exercises myself
1. Do FCC Code Challenges
1. Update my [100 days of Code log](https://github.com/james-priest/100-days-of-code-log "this log") and [tweet](https://twitter.com/james_priest1 "James Priest on Twitter") my results

---

## Pre-launch - Learning How to Learn in 4 weeks
### Day 0: June 11, 2017 - Sunday

**Today's Project(s):**

- FCC Code Challenges
- Learning How to Learn MOOC

**Progress:**

- More CSS
- set font styles

**Link to work:**

- [My FCC Code Portfolio](https://www.freecodecamp.com/james-priest "james-priest's code portfolio on FreeCodeCamp")

**Thoughts:** Finished Coursera's [Learning How to Learn](https://www.coursera.org/learn/learning-how-to-learn "Coursera: Learning How to Learn") and passed with 100% on my final exam!

---

## Pre-launch - Learning How to Learn on Coursera

### Day 0: June 10, 2017 - Saturday

**Today's Project(s):**

- FCC Code Challenges
- Learning How to Learn MOOC

**Progress:**

- Worked on CSS
- Imported Google font
- set font styles

**Link to work:**

- [My FCC Code Portfolio](https://www.freecodecamp.com/james-priest "james-priest's code portfolio on FreeCodeCamp")

**Thoughts:** I'm wrapping up a great MOOC from Coursera called [Learning How to Learn](https://www.coursera.org/learn/learning-how-to-learn "Coursera: Learning How to Learn") This in the top ten of all-time most popular MOOCs. I can't recommend it enough for getting prep'd to do FCC or any other intensive development program, bootcamp or online course.

---

## Pre-launch - GitHub, Twitter & Free Code Camp
### Day 0: June 9, 2017 - Friday

**Today's Project(s):**

- GitHub profile
- Twitter account
- FCC Profile

**Progress:**  Prep work...Today was time spent on setup. This includes:

- Setup
  - Forked the Official [100-days-of-code GitHub Repo](https://github.com/Kallaway/100-days-of-code "Official #100DaysOfCode GitHub Repo")
  - Updated [my GitHub profile](https://github.com/james-priest "James Priest on GitHub") (@james-priest)
  - Got [my Twitter account](https://twitter.com/james_priest1 "James Priest on Twitter") going (@james_priest1)
- Tweet'd my commitment to the 100-days-of-code challenge

**Link to work:**

- My GitHub [100-days-of-code-log](https://github.com/james-priest/100-days-of-code-log "this repo")

**Thoughts:** Glad to be starting this.

<!--
##
### Day : July 1, 2017 - Thursday

**Today's Project(s):**

-

**Progress:**

-

**Link to work:**

- [My FCC Code Portfolio](https://www.freecodecamp.com/james-priest "james-priest's code portfolio on FreeCodeCamp")

**Thoughts:**

---

1. [Find the Longest Word in a String](https://www.freecodecamp.com/challenges/find-the-longest-word-in-a-string)
2. [Title Case a Sentence](https://www.freecodecamp.com/challenges/title-case-a-sentence)-->
