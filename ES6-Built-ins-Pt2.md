---
title: ES6 - Built-ins Pt2
description: Grow with Google Scholarship Challenge - Mobile Web Track
---
<!-- markdownlint-disable MD022 MD024 MD032 -->
# Lesson 3: Built-ins Pt2
Notes from _**Lesson 3: Built-ins**_ of _**ES6 JavaScript Improved**_ by Richard Kalehoff and James Parkes. This class is part of the Udacity course [ES6 - JavaScript Improved](https://www.udacity.com/course/es6-javascript-improved--ud356)

This is an Intermediate skill level course which takes approximately 4 weeks to complete and is offered for **FREE**!

| Lesson 1 | Lesson 2 | Lesson 2.5 | Lesson 3 | Lesson 3.5 | Lesson 4 |
| --- | --- | --- | --- | --- | --- |
| [Syntax](ES6-Syntax.html) | [Functions](ES6-Functions.html) | [Classes](ES6-Classes.html) | [Built-ins](ES6-Built-ins.html) | **Built-ins Pt2** | [Professional Developer-fu](ES6-Professional-Developer-fu.html) |

## 17. Promises Intro
Promises are an interesting concept and solve some tricky problems that we've had in previous versions of JavaScript.

Using a JavaScript Promise is the new way to handle _asynchronous requests_, and just like most changes in ES6, it's an improvement on the way we've structured code in the past.

### Promise example

James has been waiting patiently to take my order.

> **Me:** "Hey, can I get an ice cream sundae?"
>
> **Him:** "Finally, I thought you would never ask."

Great, so I've made my request and he gives me a receipt to represent that he'll return with something in the future. But should I have to wait right here for him to come back and give it to me?

While he's making it can I get back to work on my next project? Then when he's finished with the ice-cream he can notify me that it's ready and I can pick up where I left off.

> **Him:** "Richard your Sunday's ready."
>
> **Me:** "Great can I get some hot fudge, some caramel, some whipped cream, some cherries?"
>
> **Him:** "Sure."
>
> **Me:** "Thanks." (I receive back the receipt.)

Now I'm back to waiting again. Going back and forth from...

1. making a request for something
1. the downtime while that request is being fulfilled
1. being able to do work during that downtime
1. then being notified that my request is finished

...is what promises do for us in JavaScript.

It handles the, "Do this thing now, then notify me when it's done so I can pick up where I left off."

**Him:** "Your sundae's ready."

**Me:** "Thanks it looks awesome. Here you go." (Hands over the receipt once again.)

Let's take a look at how you actually create and work with Promises.

## 18. Promises
A JavaScript Promise is created with the new [Promise constructor function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) - `new Promise()`. A promise will let you start some work that will be done **asynchronously** and let you get back to your regular work.

When you create the promise, you must give it the code that will be run asynchronously. You provide this code as the argument of the constructor function:

```js
new Promise(function () {
    window.setTimeout(function createSundae(flavor = 'chocolate') {
        const sundae = {};
        // request ice cream
        // get cone
        // warm up ice cream scoop
        // scoop generous portion into cone!
    }, Math.random() * 2000);
});
```

This code creates a promise that will start in a few seconds after I make the request. Then there are a number of steps that need to be made in the `createSundae` function.

### Indicated a Successful Request or a Failed Request
But once that's all done, how does JavaScript notify us that it's finished and ready for us to pick back up? It does that by passing two functions into our initial function. Typically we call these `resolve` and `reject`.

The function gets passed to the function we provide the Promise constructor - typically the word "resolve" is used to indicate that this function should be called when the request completes successfully. Notice the `resolve` on the first line:

```js
new Promise(function (resolve, reject) {
    window.setTimeout(function createSundae(flavor = 'chocolate') {
        const sundae = {};
        // request ice cream
        // get cone
        // warm up ice cream scoop
        // scoop generous portion into cone!
        resolve(sundae);
    }, Math.random() * 2000);
});
```

Now when the sundae has been successfully created, it calls the `resolve` method and passes it the data we want to return - in this case the data that's being returned is the completed sundae. So the `resolve` method is used to indicate that the request is complete and that it completed _successfully_.

If there is a problem with the request and it couldn't be completed, then we could use the second function that's passed to the function. Typically, this function is stored in an identifier called "reject" to indicate that this function should be used if the request fails for some reason. Check out the `reject` on the first line:

```js
new Promise(function (resolve, reject) {
    window.setTimeout(function createSundae(flavor = 'chocolate') {
        const sundae = {};
        // request ice cream
        // get cone
        // warm up ice cream scoop
        // scoop generous portion into cone!
        if ( /* iceCreamConeIsEmpty(flavor) */ ) {
            reject(`Sorry, we're out of that flavor :-(`);
        }
        resolve(sundae);
    }, Math.random() * 2000);
});
```

So the `reject` method is used when the request _could not be completed_. Notice that even though the request fails, we can still return data - in this case we're just returning text that says we don't have the desired ice cream flavor.

A Promise constructor takes a function that will run and then, after some amount of time, will either complete successfully (using the `resolve` method) or unsuccessfully (using the `reject` method). When the outcome has been finalized (the request has either completed successfully or unsuccessfully), the promise is now _fulfilled_ and will notify us so we can decide what to do with the response.

### Promises Return Immediately
The first thing to understand is that a Promise will immediately return an object.

```js
const myPromiseObj = new Promise(function (resolve, reject) {
    // sundae creation code
});
```

That object has a `.then()` method on it that we can use to have it notify us if the request we made in the promise was either successful or failed. The `.then()` method takes two functions:

1. the function to run if the request completed successfully
1. the function to run if the request failed to complete

```js
mySundae.then(function(sundae) {
    console.log(`Time to eat my delicious ${sundae}`);
}, function(msg) {
    console.log(msg);
    self.goCry(); // not a real method
});
```

As you can see, the first function that's passed to `.then()` will be called and passed the data that the Promise's `resolve` function used. In this case, the function would receive the `sundae` object. The second function will be called and passed the data that the Promise's `reject` function was called with. In this case, the function receives the error message "Sorry, we're out of that flavor :-(" that the `reject` function was called with in the Promise code above.

## 19. More Promises
Promises are an incredibly powerful addition to the language. A ton of both existing and future changes make use of them. So being able to work with and write JavaScript Promises is vital.

The reason is that Promises make it so much easier to do asynchronous code. With promises your code is gonna be easier to read, easier to write, and most importantly, it's going to be a lot easier to debug.

They're so important Udacity has actually created a standalone course dedicated just to JavaScript Promises. While you're working on this class you'll be also building an
app called the exoplanet Explorer.

This is a really cool app because it helps people learn about planets around other stars in our galaxy.

Check out our [Promises course](https://www.udacity.com/course/javascript-promises--ud898) where we'll take a deep dive into:

- JavaScript Promises
- how to handle returned data and errors
- build an app called Exoplanet Explorer that uses JavaScript Promises to fetch remote data asynchronously

## 21. Proxies Intro
Let's switch gears for a moment to talk about proxies the dictionary defines a proxy as something that represents someone else.

New in ES6 are JavaScript proxies. A JavaScript proxy will let one object stand in for another object to handle all the interactions for that other object.

The proxy can handle requests directly, pass data back and forth to the target object, and a whole bunch of other things.

Let's look at how you can create a proxy in JavaScript.

## 21. Proxies
To create a proxy object, we use the Proxy constructor - `new Proxy();`. The proxy constructor takes two items:

- the object that it will be the proxy for
- an object containing the list of methods it will handle for the proxied object

The second object is called the **handler**.

### A Pass Through Proxy
The simplest way to create a proxy is to provide an object and then an empty handler object.

```js
var richard = {status: 'looking for work'};
var agent = new Proxy(richard, {});

agent.status; // returns 'looking for work'
```

The above doesn't actually do anything special with the proxy - it just passes the request directly to the source object! If we want the proxy object to actually intercept the request, that's what the handler object is for!

The key to making Proxies useful is the handler object that's passed as the second object to the Proxy constructor. The handler object is made up of a methods that will be used for property access. Let's look at the `get`:

### Get Trap
The `get` trap is used to "intercept" calls to properties:

```js
const richard = {status: 'looking for work'};
const handler = {
    get(target, propName) {
        console.log(target); // the `richard` object, not `handler`, not `agent`
        console.log(propName); // the name of the property the proxy is checking
                               // (`agent` in this case)
    }
};
const agent = new Proxy(richard, handler);
agent.status; // logs out the richard object (not the agent object!)
              // and logs out the name of the property being accessed (`status`)
```

In the code above, the `handler` object has a `get` method (called a "trap" since it's being used in a Proxy). When the code `agent.status;` is run on the last line, because the `get` trap exists, it "intercepts" the call to get the status property and runs the `get` trap function.

This will log out the target object of the proxy (the `richard` object) and then logs out the name of the property being requested (the `status` property). _And that's all it does!_ It doesn't actually log out the property!

This is important - _if a trap is used, you need to make sure you provide all the functionality for that specific trap._

### Accessing the Target object from inside the proxy
If we wanted to actually provide the real result, we would need to return the property on the target object:

```js
const richard = {status: 'looking for work'};
const handler = {
    get(target, propName) {
        console.log(target);
        console.log(propName);
        return target[propName];
    }
};
const agent = new Proxy(richard, handler);
agent.status; // (1)logs the richard object, (2)logs the property being accessed, 
              // (3)returns the text in richard.status
```

Notice we added the `return target[propName];` as the last line of the `get` trap. This will access the property on the target object and will return it.

### Having the proxy return info, directly
Alternatively, we could use the proxy to provide direct feedback:

```js
const richard = {status: 'looking for work'};
const handler = {
    get(target, propName) {
        return `He's following many leads, so you should offer a contract ASAP!`;
    }
};
const agent = new Proxy(richard, handler);
agent.status; // returns the text `He's following many leads, so you should ...`
```

With this code, the Proxy doesn't even check the target object, it just directly responds to the calling code.

So the `get` trap will take over whenever any property on the proxy is accessed. If we want to intercept calls to change properties, then the `set` trap needs to be used!

The `set` trap is used for intercepting code that will _change a property_. The `set` trap receives: the object it proxies the property that is being set the new value for the proxy.

```js
const richard = {status: 'looking for work'};
const handler = {
    set(target, propName, value) {
        // if the pay is being set, take 15% as commission
        if (propName === 'payRate') {
            value = value * 0.85;
        }
        target[propName] = value;
    }
};
const agent = new Proxy(richard, handler);
agent.payRate = 1000; // set the actor's pay to $1,000
agent.payRate; // $850 the actor's actual pay
```

In the code above, notice that the `set` trap checks to see if the `payRate` property is being set. If it is, then the proxy (the agent) takes 15 percent off the top for her own commission! Then, when the actor's pay is set to one thousand dollars, since the `payRate` property was used, the code took 15% off the top and set the actual `payRate` property to `850`;

### Other Traps
So we've looked at the `get` and `set` traps (which are probably the ones you'll use most often), but there are actually a total of 13 different traps that can be used in a handler!

1. [the get trap](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/get) - lets the proxy handle calls to property access
1. [the set trap](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/set) - lets the proxy handle setting the property to a new value
1. [the apply trap](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/apply) - lets the proxy handle being invoked (the object being proxied is a function)
1. [the has trap](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/has) - lets the proxy handle the using `in` operator
1. [the deleteProperty trap](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/deleteProperty) - lets the proxy handle if a property is deleted
1. [the ownKeys trap](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/ownKeys) - lets the proxy handle when all keys are requested
1. [the construct trap](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/construct) - lets the proxy handle when the proxy is used with the `new` keyword as a constructor
1. [the defineProperty trap](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/defineProperty) - lets the proxy handle when defineProperty is used to create a new property on the object
1. [the getOwnPropertyDescriptor trap](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/getOwnPropertyDescriptor) - lets the proxy handle getting the property's descriptors
1. [the preventExtenions trap](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/preventExtensions) - lets the proxy handle calls to `Object.preventExtensions()` on the proxy object
1. [the isExtensible trap](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/isExtensible) - lets the proxy handle calls to `Object.isExtensible` on the proxy object
1. [the getPrototypeOf trap](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/getPrototypeOf) - lets the proxy handle calls to `Object.getPrototypeOf` on the proxy object
1. [the setPrototypeOf trap](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/setPrototypeOf) - lets the proxy handle calls to `Object.setPrototypeOf` on the proxy object

As you can see, there are a lot of traps that let the proxy manage how it handles calls back and forth to the proxied object.

## 22. Proxies vs. ES5 Getter/Setter
Initially, it can be a bit unclear as to why proxies are all that beneficial when there are already getter and setter methods provided in ES5. With ES5's getter and setter methods, you need to know _before hand_ the properties that are going to be get/set:

```js
var obj = {
    _age: 5,
    _height: 4,
    get age() {
        console.log(`getting the "age" property`);
        console.log(this._age);
    },
    get height() {
        console.log(`getting the "height" property`);
        console.log(this._height);
    }
};
```

With the code above, notice that we have to set `get age()` and `get height()` when initializing the object. So when we call the code below, we'll get the following results:

```js
obj.age; // logs 'getting the "age" property' & 5
obj.height; // logs 'getting the "height" property' & 4
```

But look what happens when we now add a new property to the object:

```js
obj.weight = 120; // set a new property on the object
obj.weight; // logs just 120
```

Notice that a `getting the "weight" property` message wasn't displayed like the `age` and `height` properties produced.

With ES6 Proxies, we _do not need to know the properties beforehand_:

```js
const proxyObj = new Proxy({age: 5, height: 4}, {
    get(targetObj, property) {
        console.log(`getting the ${property} property`);
        console.log(targetObj[property]);
    }
});

proxyObj.age; // logs 'getting the age property' & 5
proxyObj.height; // logs 'getting the height property' & 4
```

All well and good, just like the ES5 code, but look what happens when we add a new property:

```js
proxyObj.weight = 120; // set a new property on the object
proxyObj.weight; // logs 'getting the weight property' & 120
```

See that?!? A `weight` property was added to the proxy object, and when it was later retrieved, it displayed a log message!

So some functionality of proxy objects may seem similar to existing ES5 getter/setter methods. But with proxies, you do not need to initialize the object with getters/setters for each property when the object is initialized.

## 23. Proxies Recap
A proxy object sits between a real object and the calling code. The calling code interacts with the proxy instead of the real object. To create a proxy:

- use the `new Proxy()` constructor
  - pass the object being proxied as the first item
  - the second object is a handler object
- the handler object is made up of 1 of 13 different "traps"
- a trap is a function that will intercept calls to properties and let you run code
- if a trap is not defined, the default behavior is sent to the target object

Proxies are a powerful new way to create and manage the interactions between objects.

## 24. Generators
Whenever a function is invoked, the JavaScript engine starts at the top of the function and runs every line of code until it gets to the bottom. There's no way to stop the execution of the function in the middle and pick up again at some later point. This **"run-to-completion"** is the way it's always been:

```js
function getEmployee() {
    console.log('the function has started');

    const names = ['Amanda', 'Diego', 'Joe', 'James', 'Kagure', 'Kavita', 'Orit'];

    for (const name of names) {
        console.log(name);
    }

    console.log('the function has ended');
}

getEmployee();
```

Running the code above produces the following output to the console:

```text
the function has started
Amanda
Diego
Joe
James
Kagure
Kavita
Orit
the function has ended
```

But what if you want to print out the first 3 employee names then stop for a bit, then, at some later point, you want to continue where you left off and print out more employee names. With a regular function, you can't do this since there's no way to "pause" a function in the middle of its execution.

### Pausable Functions
If we _do_ want to be able to pause a function mid-execution, then we'll need a new type of function available to us in ES6 - generator functions! Let's look at one:

```js
function* getEmployee() {
    console.log('the function has started');

    const names = ['Amanda', 'Diego', 'Joe', 'James', 'Kagure', 'Kavita', 'Orit'];

    for (const name of names) {
        console.log( name );
    }

    console.log('the function has ended');
}
```

Notice the asterisk (i.e. `*`) right after the `function` keyword? That asterisk indicates that this function is actually a generator!

Now check out what happens when we try running this function:

```js
getEmployee();

// this is the response I get in Chrome:
getEmployee {[[GeneratorStatus]]: "suspended", [[GeneratorReceiver]]: Window}
```

...umm, what? Where's the "the function has started" text from the top of the function? And why didn't we get any names printed to the console? Those are good questions, but first, a quiz.

#### Quiz Question
Which of the following are valid generators? Pay attention to the placement of the asterisk.

If you're not sure, try running them in your browser's console.

1. [ ] `function* names() { /* */ }`
1. [ ] `function * names() { /* */ }`
1. [ ] `function *names() { /* */ }`

#### Solution
The asterisk of the generator can actually be placed anywhere between the `function` keyword and the function's name. So all three of these are valid generator declarations!

1. [x] `function* names() { /* */ }`
1. [x] `function * names() { /* */ }`
1. [x] `function *names() { /* */ }`

The community has coalesced into having the asterisk appear right next to the `function` keyword (i.e. `function* name() { … }`). But there others that recommend having the asterisk touch the function's name instead. So it's important to realize that the asterisk indicates that it is a generator but that the placement of the asterisk is not important.

## 25. Generators & Iterators
> **WARNING:** We looked at iteration in a previous section, so if you're rusty on it, better check it out again because they're resurfacing here with generators!

When a generator is invoked, it doesn't actually run any of the code inside the function. Instead, it creates and returns an iterator. This iterator can then be used to execute the actual generator's inner code.

```js
const generatorIterator = getEmployee();
generatorIterator.next();
```

Produces the code we expect:

```text
the function has started
Amanda
Diego
Joe
James
Kagure
Kavita
Orit
the function has ended
```

Now if you tried the code out for yourself, the first time the iterator's `.next()` method was called it ran all of the code inside the generator. Did you notice anything? The code never paused! So how do we get this magical, pausing functionality?

### The Yield Keyword
The `yield` keyword is new and was introduced with ES6. It can only be used inside generator functions. `yield` is what causes the generator to pause. Let's add yield to our generator and give it a try:

```js
function* getEmployee() {
    console.log('the function has started');

    const names = ['Amanda', 'Diego', 'Joe', 'James', 'Kagure', 'Kavita', 'Orit'];

    for (const name of names) {
        console.log(name);
        yield;
    }

    console.log('the function has ended');
}
```

Notice that there's now a `yield` inside the `for..of` loop. If we invoke the generator (which produces an iterator) and then call `.next()`, we'll get the following output:

```js
const generatorIterator = getEmployee();
generatorIterator.next();
```

Logs the following to the console:

```text
the function has started
Amanda
```

It's paused! But to really be sure, let's check out the next iteration:

```js
generatorIterator.next();
```

Logs the following to the console:

```text
Diego
```

So it remembered exactly where we left off! It took the next item in the array (Diego), logged it, and then hit the `yield` again, so it paused again.

Now pausing is all well and good, but what if we could send data from the generator back to the "outside" world? We can do this with `yield`.

### Yielding Data to the "Outside" World
Instead of logging the names to the console and then pausing, let's have the code "return" the name and then pause.

```js
function* getEmployee() {
    console.log('the function has started');

    const names = ['Amanda', 'Diego', 'Joe', 'James', 'Kagure', 'Kavita', 'Orit'];

    for (const name of names) {
        yield name;
    }

    console.log('the function has ended');
}
```

Notice that now instead of `console.log(name)`; that it's been switched to `yield name;`. With this change, when the generator is run, it will "yield" the name back out to the function _and then pause its execution_. Let's see this in action:

```js
const generatorIterator = getEmployee();
let result = generatorIterator.next();
result.value // "Amanda"

generatorIterator.next().value // "Diego"
generatorIterator.next().value // "Farrin"
```

#### Quiz Question
How many times will the iterator's .next() method need to be called to fully complete/"use up" the udacity generator function below:

```js
function* udacity() {
    yield 'Richard';
    yield 'James'
}
```

1. [ ] 0 times
1. [ ] 1 time
1. [ ] 2 times
1. [ ] 3 times

#### Solution
It will be called one more time than there are `yield` expressions in the generator function.

- [x] 3 times

The first call to `.next()` will start the function and run to the first `yield`. The second call to `.next()` will pick up where things left off and run to the second `yield`. The third and final call to `.next()` will pick up where things left off again and run to the end of the function.

## 26. Sending Data into/out of a Generator
So we can get data out of a generator by using the `yield` keyword. We can also send data back _into_ the generator, too. We do this using the `.next()` method:

```js
function* displayResponse() {
    const response = yield;
    console.log(`Your response is "${response}"!`);
}

const iterator = displayResponse();

iterator.next(); // starts running the generator function
iterator.next('Hello Udacity Student'); // send data into the generator
// the line above logs to the console: Your response is "Hello Udacity Student"!
```

Calling `.next()` with data (i.e. `.next('Richard')`) will send data into the generator function where it last left off. It will "replace" the yield keyword with the data that you provided.

So the `yield` keyword is used to pause a generator _and_ used to send data outside of the generator, and then the `.next()` method is used to pass data `into` the generator. Here's an example that makes use of both of these to cycle through a list of names one at a time:

```js
function* getEmployee() {
    const names = ['Amanda', 'Diego', 'Joe', 'James', 'Kagure', 'Kavita', 'Orit'];
    const facts = [];

    for (const name of names) {
        // yield *out* each name AND store the returned data into the facts array
        facts.push(yield name); 
    }

    return facts;
}

const generatorIterator = getEmployee();

// get the first name out of the generator
let name = generatorIterator.next().value;

// pass data in *and* get the next name
name = generatorIterator.next(`${name} is cool!`).value; 

// pass data in *and* get the next name
name = generatorIterator.next(`${name} is awesome!`).value; 

// pass data in *and* get the next name
name = generatorIterator.next(`${name} is stupendous!`).value; 

// you get the idea
name = generatorIterator.next(`${name} is impressive!`).value;
name = generatorIterator.next(`${name} is stunning!`).value;
name = generatorIterator.next(`${name} is awe-inspiring!`).value;

// pass the last data in, generator ends and returns the array
const positions = generatorIterator.next(`${name} is magnificent!`).value; 

// displays each name with description on its own line
positions.join('\n');
```

#### Quiz Question
What will happen if the following code is run?

```js
function* createSundae() {
    const toppings = [];

    toppings.push(yield);
    toppings.push(yield);
    toppings.push(yield);

    return toppings;
}

var it = createSundae();
it.next('hot fudge');
it.next('sprinkles');
it.next('whipped cream');
it.next();
```

1. [ ] The `toppings` array will have `undefined` as its last item
1. [ ] An error will occur
1. [ ] The generator will be paused, waiting for it's last call to `.next()`


#### Solution
Remember that the first call to `.next()` will initiate the generator which will stop at the first `yield`. The second call to `.next()` is the call that will supply that `yield with the data.

Count how many yields there are and when data is passed into each of the calls to `.next()`.

- [x] The `toppings` array will have `undefined` as its last item

Because the first call to `.next()` passes in some data. But that data doesn't get stored anywhere. The last call to `.next()` should have some data since it's being yielded into the last call to `toppings.push()`.

### Generators Summary
Generators are a powerful new kind of function that is able to pause its execution while also maintaining its own state. Generators are great for iterating over a list of items one at a time so you can handle each item on its own before moving on to the next one. You can also use generators to handle nested callbacks. For example, let's say that an app needs to get a list of all repositories _and_ the number of times they've been starred. Well, before you can get the number of stars for each repository, you'd need to get the user's information. Then after retrieving the user's profile the code can then take that information to find all of the repositories.

Generators will also be used heavily in upcoming additions to the JavaScript language. One upcoming feature that will make use of them is [async functions](https://github.com/tc39/ecmascript-asyncawait).

## 27. Lesson 3 Summary
At this point you've seen almost everything there is to see in ES6 but we still have one
more lesson.

You'd think that with all the advancements to JavaScript that you'd be able to start using every new feature in Es6 right now but that's not really the case. Sometimes there are situations where browsers haven't quite cut up to the latest and greatest features in JavaScript.

In lesson 4 you'll see how in spite of this you can still write Es6 code that is future proof for when browsers catch up but will still work for browsers that aren't quite up to snuff.

Let's put what you've learned to good use in the next lesson.