---
title: ES6 - Built-ins
description: Grow with Google Scholarship Challenge - Mobile Web Track
---
<!-- markdownlint-disable MD022 MD024 MD032 -->

[<-- back to Mobile Web Specialist Phase 1 Notes TOC](MWS-TOC.html)

---

# Lesson 3: Built-ins
Notes from _**Lesson 3: Built-ins**_ of _**ES6 JavaScript Improved**_ by Richard Kalehoff and James Parkes. This class is part of the Udacity course [ES6 - JavaScript Improved](https://www.udacity.com/course/es6-javascript-improved--ud356)

This is an Intermediate skill level course which takes approximately 4 weeks to complete and is offered for **FREE**!

| Lesson 1 | Lesson 2 | Lesson 2.5 | Lesson 3 | Lesson 3.5 | Lesson 4 |
| --- | --- | --- | --- | --- | --- |
| [Syntax](ES6-Syntax.html) | [Functions](ES6-Functions.html) | [Classes](ES6-Classes.html) | **Built-ins** | [Built-ins Pt2](ES6-Built-ins-Pt2.html) | [Professional Developer-fu](ES6-Professional-Developer-fu.html) |

## 1. New Built-ins
In this lesson we'll explore the latest batch of new built-ins provided in the ES6. We now have **Sets**, **Maps**, **Promises**, and a whole new bunch of other built-ins at our disposal.

It's taken a while for JavaScript to catch up but these built-ins make it much easier for us to execute tasks that were once more difficult in earlier versions of the language.

As you go through this lesson you'll see

- how these new built-ins are structured
- how they work
- when it's the most appropriate time to use them

To get started let's kick it off with symbols.

## 2. Symbols Intro
Symbols are the latest addition to the list of primitive data types available to us in JavaScript. Previously JavaScript only had

- `number`
- `string`
- `boolean`
- `null`
- `undefined`

as its primitives. but now `symbol` has entered the mix.

What's a symbol?

> ### Symbol
> A unique identifier, most often used to uniquely identify properties within an object.

For example, let's assume this bowl is an object. So we add this Apple and this orange and this banana to the bowl. Now keep in mind these fruits are also objects, but now they're properties of this bowl.

Now here's where things get interesting.  If I add another banana to the bowl can you see what the problem is? If I ask you to hand me a banana from the bowl you won't know which one I need exactly. We need a way to uniquely identify this banana from the other banana. 

In code I can do something like I represent the first banana as `banana1` and the second banana as `banana2`. But what happens when I keep adding more bananas to the bowl? I think you see where we're going with this. Thankfully with the addition of symbols and es6 we've got a solution.

## 3. Symbols
A **symbol** is a unique and immutable data type that is often used to identify object properties.

To create a symbol, you write `Symbol()` with an optional string as its **description**.

```js
const sym1 = Symbol('apple');
console.log(sym1);
```

> `Symbol(apple)`

This will create a unique symbol and store it in `sym1`. The description `"apple"` is just a way to describe the symbol, but it **can’t** be used to access the symbol itself.

And just to show you how this works, if you compare two symbols with the same description…

```js
const sym2 = Symbol('banana');
const sym3 = Symbol('banana');
console.log(sym2 === sym3);
```

> `false`

…then the result is `false` because the description is _only_ used to describe the symbol. It’s not used as part of the symbol itself. Each time, a new symbol is created, regardless of the description.

Still, this can be hard to wrap your head around, so let’s use the example from the previous section to see how symbols can be useful. Here’s the code to represent the bowl from the example.

```js
const bowl = {
  'apple': { color: 'red', weight: 136.078 },
  'banana': { color: 'yellow', weight: 183.15 },
  'orange': { color: 'orange', weight: 170.097 }
};
```

The bowl contains fruit which are objects that are properties of the bowl. But, we run into a problem when the second banana gets added.

```js
const bowl = {
  'apple': { color: 'red', weight: 136.078 },
  'banana': { color: 'yellow', weight: 183.151 },
  'orange': { color: 'orange', weight: 170.097 },
  'banana': { color: 'yellow', weight: 176.845 }
};
console.log(bowl);
```

> `Object {apple: Object, banana: Object, orange: Object}`

Instead of adding another banana to the bowl, our previous banana is overwritten by the new banana being added to the bowl. To fix this problem, we can use symbols.

```js
const bowl = {
  [Symbol('apple')]: { color: 'red', weight: 136.078 },
  [Symbol('banana')]: { color: 'yellow', weight: 183.15 },
  [Symbol('orange')]: { color: 'orange', weight: 170.097 },
  [Symbol('banana')]: { color: 'yellow', weight: 176.845 }
};
console.log(bowl);
```

> `Object {Symbol(apple): Object, Symbol(banana): Object, Symbol(orange): Object, Symbol(banana): Object}`

By changing the bowl’s properties to use symbols, each property is a unique Symbol and the first banana doesn’t get overwritten by the second banana.

## 4. Iteration & Iterable Protocols
Before you move on, let’s spend some time looking at two new protocols in ES6:

- the iterable protocol
- the iterator protocol

These protocols aren’t built-ins, but they will help you understand the new concept of iteration in ES6, as well as show you a use case for symbols.

### The Iterable Protocol
The **iterable protocol** is used for defining and customizing the iteration behavior of objects. What that really means is you now have the _flexibility_ in ES6 to specify a way for iterating through values in an object. For some objects, they already come built-in with this behavior. For example, strings and arrays are examples of built-in iterables.

```js
const digits = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
for (const digit of digits) {
  console.log(digit);
}
```

> 0
> 1
> 2
> 3
> 4
> 5
> 6
> 7
> 8
> 9

If you recall from earlier lesson 1, any object that is iterable can use the new `for..of` loop. Later in this lesson, you’ll also learn about Sets and Maps which are other examples of built-in iterables.

#### How it Works
In order for an object to be iterable, it must implement the **iterable interface**. If you come from a language like Java or C, then you’re probably familiar with interfaces, but for those of you who aren’t, that basically means that in order for an object to be iterable it must contain a default iterator method. This method will define how the object should be iterated.

The **iterator method**, which is available via the constant `[Symbol.iterator]`, is a zero arguments function that returns an iterator object. An iterator object is an object that conforms to the iterator protocol.

### The Iterator Protocol
The **iterator protocol** is used to define a standard way that an object produces a sequence of values. What that really means is you now have a process for defining how an object will iterate. This is done through implementing the `.next()` method.

#### How it Works
An object becomes an iterator when it implements the `.next()` method. The `.next()` method is a zero arguments function that returns an object with two properties:

1. `value` : the data representing the next value in the sequence of values within the object
1. `done` : a boolean representing if the iterator is done going through the sequence of values
    - If done is true, then the iterator has reached the end of its sequence of values.
    - If done is false, then the iterator is able to produce another value in its sequence of values.

Here’s the example from earlier, but instead we are using the array’s default iterator to step through the each value in the array.

```js
const digits = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
const arrayIterator = digits[Symbol.iterator]();

console.log(arrayIterator.next());
console.log(arrayIterator.next());
console.log(arrayIterator.next());
```

> Object {value: 0, done: false}<br>
> Object {value: 1, done: false}<br>
> Object {value: 2, done: false}

## 5. Sets
### A Set in Mathematics
If you think back to mathematics, a set is a collection of distinct items. For example, `{2, 4, 5, 6}` is a set because each number is unique and appears only once. However, `{1, 1, 2, 4}` is not a set because it _contains duplicate entries_ (the 1 is in there more than once!).

In JavaScript, we can already represent something similar to a mathematical set using an array.

```js
const nums = [2, 4, 5, 6];
```

However, arrays _do no enforce items to be unique_. If we try to add another `2` to `nums`, JavaScript won't complain and will add it without any issue.

```js
nums.push(2);
console.log(nums);
```

> `[2, 4, 5, 6, 2]`

…and now `nums` is no longer a set in the mathematical sense.

### Sets
In ES6, there’s a new built-in object that behaves like a mathematical set and works similarly to an array. This new object is conveniently called a "Set". The biggest differences between a set and an array are:

- Sets are not indexed-based - you do not refer to items in a set based on their position in the set
- items in a Set can’t be accessed individually

Basically, a Set is an object that lets you store unique items. You can add items to a Set, remove items from a Set, and loop over a Set. These items can be either primitive values or objects.

### How to Create a Set
There’s a couple of different ways to create a Set. The first way, is pretty straightforward:

```js
const games = new Set();
console.log(games);
```

> `Set {}`

This creates an empty Set `games` with no items.

If you want to create a Set from a list of values, you use an array:

```js
const games = new Set(['Super Mario Bros.', 'Banjo-Kazooie', 'Mario Kart', 'Super Mario Bros.']);
console.log(games);
```

> `Set {'Super Mario Bros.', 'Banjo-Kazooie', 'Mario Kart'}`

Notice the example above automatically removes the duplicate entry `"Super Mario Bros."` when the Set is created. Pretty neat!

#### Quiz Question
Select the collections below that represent a Set in JavaScript.

1. [ ] `{1, 'Basketball', true, false, '1'}`
1. [ ] `{}`
1. [ ] `{1, 1, 1, 1}`
1. [ ] `{false, '0', 0, 'Soccer', 3.14, 25, 0}`
1. [ ] `{'Gymnastics', 'Swimming', 2}`

#### Solution
A set is an object that has no repeating values.

1. [x] `{1, 'Basketball', true, false, '1'}`
1. [x] `{}`
1. [ ] `{1, 1, 1, 1}`
1. [ ] `{false, '0', 0, 'Soccer', 3.14, 25, 0}`
1. [x] `{'Gymnastics', 'Swimming', 2}`

## 6. Modifying Sets
After you’ve created a Set, you’ll probably want to add and delete items from the Set. So how do you that? You use the appropriately named, `.add()` and `.delete()` methods:

```js

const games = new Set(['Super Mario Bros.', 'Banjo-Kazooie', 'Mario Kart', 'Super Mario Bros.']);

games.add('Banjo-Tooie');
games.add('Age of Empires');
games.delete('Super Mario Bros.');

console.log(games);
```

> `Set {'Banjo-Kazooie', 'Mario Kart', 'Banjo-Tooie', 'Age of Empires'}`

On the other hand, if you want to delete all the items from a Set, you can use the `.clear()` method.

```js
games.clear()
console.log(games);
```

> `Set {}`

> **TIP:** If you attempt to `.add()` a duplicate item to a Set, you won’t receive an error, but the item will not be added to the Set. Also, if you try to `.delete() an item that is not in a Set, you won’t receive an error, and the Set will remain unchanged.
>
>`.add()` returns the `Set` if an item is successfully added. On the other hand, `.delete()` returns a Boolean (`true` or `false`) depending on successful deletion.

## 7. Working With Sets

### Checking The Length
Once you’ve constructed your Set, there are a couple of different properties and methods you can use to work with Sets.

Use the `.size` property to return the number of items in a Set:

```js
const days = new Set(['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']);
console.log(days.size);
```

> `7`

Remember, Sets can’t be accessed by their index like an array, so you use the `.size` property instead of `.length` property to get the size of the Set.

### Checking If An Item Exists
Use the `.has()` method to check if an item exists in a Set. If the item is in the Set, then `.has()` will return `true`. If the item doesn’t exist in the Set, then `.has()` will return `false`.

```js
console.log(days.has('Wed'));
```

> `true`

### Retrieving All Values
Finally, use the `.values()` method to return the values in a Set. The return value of the `.values()` method is a `SetIterator` object.

```js
console.log(days.values());
```

> `SetIterator {'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'}`

More on the `SetIterator` object in a second!

> **TIP:** The `.keys()` method will behave the exact same way as the `.values()` method by returning the values of a Set within a new Iterator Object. The `.keys()` method is an alias for the `.values()` method for similarity with maps. You’ll see the `.keys()` method later in this lesson during the Maps section.

## 8. Sets & Iterators
The last step to working with Sets is looping over them.

If you remember back to our discussion on the new _iterable_ and _iterator_ protocols in ES6, then you’ll recall that Sets are built-in iterables. This means two things in terms of looping:

1. You can use the Set’s default iterator to step through each item in a Set, one by one.
1. You can use the new `for..of` loop to loop through each item in a Set.

### Using the SetIterator
Because the `.values()` method returns a new iterator object (called `SetIterator`), you can store that iterator object in a variable and loop through each item in the Set using `.next()`.

```js
const iterator = months.values();
iterator.next();
```

> `Object {value: 'January', done: false}`

And if you run `.next()` again?

```js
iterator.next();
```

> `Object {value: 'February', done: false}`

And so on until `done` equals `true` which marks the end of the Set.

```js
const days = new Set(['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']);
const iterator = days.values();

iterator.next();  // {value: 'Mon', done: false}
iterator.next();  // {value: 'Tue', done: false}
iterator.next();  // {value: 'Wed', done: false}
iterator.next();  // {value: 'Thu', done: false}
iterator.next();  // {value: 'Fri', done: false}
iterator.next();  // {value: 'Sat', done: false}
iterator.next();  // {value: 'Mon', done: false}
iterator.next();  // {value: undefined, done: true}
```

### Using a `for..of` Loop
An easier method to loop through the items in a Set is the `for..of` loop.

```js
const colors = new Set(['red', 'orange', 'yellow', 'green', 'blue', 'violet');
for (const color of colors) {
  console.log(color);
}
```

> red<br>
> orange<br>
> yellow<br>
> green<br>
> blue<br>
> violet

## 9. Quiz: Using Sets
### Directions
Create a variable with the name `myFavoriteFlavors` and give it the value of an empty `Set` object. Then use the `.add()` method to add the following strings to it:

- "chocolate chip"
- "cookies and cream"
- "strawberry"
- "vanilla"

Then use the `.delete()` method to remove "strawberry" from the set.

#### Code

```js
/*
 * Programming Quiz: Using Sets (3-1)
 *
 * Create a Set object and store it in a variable named `myFavoriteFlavors`.
 * Add the following strings to the set:
 *     - chocolate chip
 *     - cookies and cream
 *     - strawberry
 *     - vanilla
 *
 * Then use the `.delete()` method to remove "strawberry" from the set.
 */
```

#### Solution
```js
/*
 * Programming Quiz: Using Sets (3-1)
 *
 * Create a Set object and store it in a variable named `myFavoriteFlavors`.
 * Add the following strings to the set:
 *     - chocolate chip
 *     - cookies and cream
 *     - strawberry
 *     - vanilla
 *
 * Then use the `.delete()` method to remove "strawberry" from the set.
 */
const myFavoriteFlavors = new Set();

myFavoriteFlavors.add('chocolate chip');
myFavoriteFlavors.add('cookies and cream');
myFavoriteFlavors.add('strawberry');
myFavoriteFlavors.add('vanilla');

myFavoriteFlavors.delete('strawberry');

console.log(myFavoriteFlavors);
```

> `Set { 'chocolate chip', 'cookies and cream', 'vanilla' }`

## 10. WeakSets
### What is a WeakSet?
A WeakSet is just like a normal Set with a few key differences:

1. a WeakSet can only contain objects
1. a WeakSet is not iterable which means it can’t be looped over
1. a WeakSet does not have a `.clear()` method

You can create a WeakSet just like you would a normal Set, except that you use the `WeakSet` constructor.

```js
const student1 = { name: 'James', age: 26, gender: 'male' };
const student2 = { name: 'Julia', age: 27, gender: 'female' };
const student3 = { name: 'Richard', age: 31, gender: 'male' };

const roster = new WeakSet([student1, student2, student3]);
console.log(roster);
```

> `WeakSet {Object {name: 'Julia', age: 27, gender: 'female'}, Object {name: 'Richard', age: 31, gender: 'male'}, Object {name: 'James', age: 26, gender: 'male'}}`

…but if you try to add something other than an object, you’ll get an error!

```js
roster.add('Amanda');
```

> `Uncaught TypeError: Invalid value used in weak set(…)`

This is expected behavior because WeakSets can only contain objects. But why should it only contain objects? Why would you even use a WeakSet if normal Sets can contain objects and other types of data? Well, the answer to that question has more to do with why WeakSets do not have a `.clear()` method...

### Garbage Collection
In JavaScript, memory is allocated when new values are created and is "automatically" freed up when those values are no longer needed. This process of freeing up memory after it is no longer needed is what is known as **garbage collection**.

WeakSets take advantage of this by exclusively working with objects. If you set an object to `null`, then you’re essentially deleting the object. And when JavaScript’s garbage collector runs, the memory that object previously occupied will be freed up to be used later in your program.

```js
let studentA = { name: 'Richard', age: 31 };
let studentB = { name: 'Alexis', age: 28 };
let studentC = { name: 'Jasmine', age: 29 };

let roster = new WeakSet([studentA, studentB, studentC]);

studentC = null;
console.log(roster);
```

> `WeakSet {Object {name: 'Julia', age: 27, gender: 'female'}, Object {name: 'James', age: 26, gender: 'male'}}`

What makes this so useful is you don’t have to worry about deleting references to deleted objects in your WeakSets, JavaScript does it for you! When an object is deleted, the object will also be deleted from the WeakSet when garbage collection runs. 

**This makes WeakSets useful in situations where you want an efficient, lightweight solution for creating groups of objects.**

The point in time when garbage collection happens depends on a lot of different factors. Check out [MDN’s documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Memory_Management#Garbage_collection) to learn more about the algorithms used to handle garbage collection in JavaScript.

## 11. Quiz: Working With WeakSets
### Directions
Create the following variables:

- `uniqueFlavors` and give it the value of an empty `WeakSet` object
- `flavor1`, and set it to the object `{ flavor: 'chocolate' }`
- `flavor2`, and set it to an object with a property of `flavor` and a value of your choice

Use the `.add()` method to add the objects `flavor1` and `flavor2` to `uniqueFlavors`.

Use the `.add()` method to add the `flavor1` object to the `uniqueFlavors` set, again.

#### Code

```js
/*
 * Programming Quiz: Using Sets (3-2)
 *
 * Create the following variables:
 *     - uniqueFlavors and set it to a new WeakSet object
 *     - flavor1 and set it equal to `{ flavor: 'chocolate' }`
 *     - flavor2 and set it equal to an object with property 'flavor'
 *       and value of your choice!
 *
 * Use the `.add()` method to add the objects `flavor1` and `flavor2`
 *    to `uniqueFlavors`
 * Use the `.add()` method to add the `flavor1` object (again!) to 
 *    the `uniqueFlavors` set
 */
```

#### Solution

```js
/*
 * Programming Quiz: Using Sets (3-2)
 *
 * Create the following variables:
 *     - uniqueFlavors and set it to a new WeakSet object
 *     - flavor1 and set it equal to `{ flavor: 'chocolate' }`
 *     - flavor2 and set it equal to an object with property 'flavor'
 *       and value of your choice!
 *
 * Use the `.add()` method to add the objects `flavor1` and `flavor2`
 *    to `uniqueFlavors`
 * Use the `.add()` method to add the `flavor1` object (again!) to 
 *    the `uniqueFlavors` set
 */

let uniqueFlavors = new WeakSet();
let flavor1 = { flavor: 'chocolate' }
let flavor2 = { flavor: 'vanilla' }

uniqueFlavors.add(flavor1);
uniqueFlavors.add(flavor2);
uniqueFlavors.add(flavor1);

console.log(uniqueFlavors)
```

> `WeakSet {Object {flavor: 'chocolate'}, Object {flavor: 'vanilla'}}`

## 12. Maps
So we just looked at Sets and WeakSets but I want to turn your attention towards Maps and WeakMaps.

Maps and WeakMaps share a lot of things in common with Sets and WeakSets. They both have similar properties and methods.

- Maps and Sets are both **iterable** which means you can loop over them
- WeakMaps and WeakSets **don't prevent objects from being garbage collected**.

However, Maps are unique because they are **collections of key value pairs**.

```js
{
  key1: value1
  richard: 'is awesome'
  james: 'is also cool'
}
```

Whereas Sets are **collections of unique values**.

```js
[val1, val2, val3]
```

You could say that Sets are to arrays as maps are to objects.

> Sets :: Arrays<br>
> Maps :: Objects

In this next section we'll look at how you can create and use Maps and WeakMaps.

## 13. Creating and Modifying Maps
### Maps
If Sets are similar to Arrays, then Maps are similar to Objects because Maps store key-value pairs similar to how objects contain named properties with values.

Essentially, a Map is an object that lets you store key-value pairs where both the keys and the values can be objects, primitive values, or a combination of the two.

### How to Create a Map
To create a Map, simply type:

```js
const employees = new Map();
console.log(employees);
```

> `Map {}`

This creates an empty Map `employee` with no key-value pairs.

### Modifying Maps
Unlike Sets, you can’t create Maps from a list of values; instead, you add key-values by using the Map’s `.set()` method.

```js
const employees = new Map();

employees.set('james.parkes@udacity.com', { 
    firstName: 'James',
    lastName: 'Parkes',
    role: 'Content Developer' 
});
employees.set('julia@udacity.com', {
    firstName: 'Julia',
    lastName: 'Van Cleve',
    role: 'Content Developer'
});
employees.set('richard@udacity.com', {
    firstName: 'Richard',
    lastName: 'Kalehoff',
    role: 'Content Developer'
});

console.log(employees);
```

> `Map {'james.parkes@udacity.com' => Object {...}, 'julia@udacity.com' => Object {...}, 'richard@udacity.com' => Object {...}}`

The `.set()` method takes two arguments. The first argument is the key, which is used to reference the second argument, the value.

To remove key-value pairs, simply use the `.delete()` method.

```js
employees.delete('julia@udacity.com');
employees.delete('richard@udacity.com');
console.log(employees);
```

> `Map {'james.parkes@udacity.com' => Object {firstName: 'James', lastName: 'Parkes', role: 'Course Developer'}}`

Again, similar to Sets, you can use the `.clear()` method to remove all key-value pairs from the Map.

```js
employees.clear()
console.log(employees);
```

> `Map {}`

**TIP:** If you `.set()` a key-value pair to a Map that already uses the same key, you won’t receive an error, but the key-value pair will overwrite what currently exists in the Map. Also, if you try to `.delete()` a key-value that is not in a Map, you won’t receive an error, and the Map will remain unchanged.

The `.delete()` method returns `true` if a key-value pair is successfully deleted from the `Map` object, and `false` if unsuccessful. The return value of `.set()` is the `Map` object itself if successful.

## 14. Working with Maps
After you’ve built your Map, you can use the `.has()` method to check if a key-value pair exists in your Map by passing it a key.

```js
const members = new Map();

members.set('Evelyn', 75.68);
members.set('Liam', 20.16);
members.set('Sophia', 0);
members.set('Marcus', 10.25);

console.log(members.has('Xavier'));
console.log(members.has('Marcus'));
```

> `false`<br>
> `true`

And you can also retrieve values from a Map, by passing a key to the `.get()` method.

```js
console.log(members.get('Evelyn'));
```

> `75.68`

## 15. Looping Through Maps
You’ve created a Map, added some key-value pairs, and now you want to loop through your Map. Thankfully, you’ve got three different options to choose from:

1. Step through each key or value using the Map’s default iterator
1. Loop through each key-value pair using the new `for..of` loop
1. Loop through each key-value pair using the Map’s `.forEach()` method

### 1. Using the MapIterator
Using both the `.keys()` and `.values()` methods on a Map will return a new iterator object called MapIterator. You can store that iterator object in a new variable and use `.next()` to loop through each key or value. Depending on which method you use, will determine if your iterator has access to the Map’s keys or the Map’s values.

```js
let iteratorObjForKeys = members.keys();
iteratorObjForKeys.next();
```

> `Object {value: 'Evelyn', done: false}`

Use `.next()` to the get the next key value.

```js
iteratorObjForKeys.next();
```

> `Object {value: 'Liam', done: false}`

And so on.

```js
iteratorObjForKeys.next();
```

> `Object {value: 'Sophia', done: false}`

On the flipside, use the `.values()` method to access the Map’s values, and then repeat the same process.

```js
let iteratorObjForValues = members.values();
iteratorObjForValues.next();
```

> `Object {value: 75.68, done: false}`

### 2. Using a for...of Loop
Your second option for looping through a Map is with a `for..of` loop.

```js
for (const member of members) {
  console.log(member);
}
```

> ['Evelyn', 75.68]<br>
> ['Liam', 20.16]<br>
> ['Sophia', 0]<br>
> ['Marcus', 10.25]

However, when you use a `for..of` loop with a Map, you don’t exactly get back a key or a value. Instead, the key-value pair is split up into an array where the first element is the key and the second element is the value. If only there were a way to fix this?

#### Question
```js
/*
 * Using array destructuring, fix the following code to print the
 * keys and values of the `members` Map to the console.
 */

const members = new Map();

members.set('Evelyn', 75.68);
members.set('Liam', 20.16);
members.set('Sophia', 0);
members.set('Marcus', 10.25);

for (const member of members) {
    // console.log(key, value);
}
```

#### Solution
```js
/*
 * Using array destructuring, fix the following code to print the
 * keys and values of the `members` Map to the console.
 */

const members = new Map();

members.set('Evelyn', 75.68);
members.set('Liam', 20.16);
members.set('Sophia', 0);
members.set('Marcus', 10.25);

for (const member of members) {
    const [key, value] = member;
    console.log(key, value);
}
```

> Evelyn 75.68<br>
> Liam 20.16<br>
> Sophia 0<br>
> Marcus 10.25

### 3. Using a forEach Loop
Your last option for looping through a Map is with the `.forEach()` method.

```js
members.forEach((key, value) => console.log(key, value));
```

> ['Evelyn', 75.68]<br>
> ['Liam', 20.16]<br>
> ['Sophia', 0]<br>
> ['Marcus', 10.25]

Notice how with the help of an arrow function, the `forEach` loop reads fairly straightforward. For each `value` and `key` in `members`, log the `value` and `key` to the console.

## 16. WeakMaps

> **TIP:** If you’ve gone through the WeakSets section, then this section should be somewhat of a review. WeakMaps exhibit the same behavior as a WeakSets, except WeakMaps work with key-values pairs instead of individual items.

### What is a WeakMap?

A WeakMap is just like a normal Map with a few key differences:

1. a WeakMap can only contain objects as keys,
1. a WeakMap is not iterable which means it can’t be looped and
1. a WeakMap does not have a `.clear()` method.

You can create a WeakMap just like you would a normal Map, except that you use the `WeakMap` constructor.

```js
let book1 = { title: 'Pride and Prejudice', author: 'Jane Austen' };
let book2 = { title: 'The Catcher in the Rye', author: 'J.D. Salinger' };
let book3 = { title: 'Gulliver’s Travels', author: 'Jonathan Swift' };

const library = new WeakMap();
library.set(book1, true);
library.set(book2, false);
library.set(book3, true);

console.log(library);
```

> `WeakMap {Object {title: 'Pride and Prejudice', author: 'Jane Austen'} => true, Object {title: 'The Catcher in the Rye', author: 'J.D. Salinger'} => false, Object {title: 'Gulliver’s Travels', author: 'Jonathan Swift'} => true}`

…but if you try to add something other than an object as a key, you’ll get an error!

```js
library.set('The Grapes of Wrath', false);
```

> `Uncaught TypeError: Invalid value used as weak map key(…)`

This is expected behavior because **WeakMap can only contain objects as keys**. Again, similar to WeakSets, WeakMaps leverage garbage collection for easier use and maintainability.

### Garbage Collection
In JavaScript, memory is allocated when new values are created and is "automatically" freed up when those values are no longer needed. This process of freeing up memory after it is no longer needed is what is known as garbage collection.

WeakMaps take advantage of this by exclusively working with objects as keys. If you set an object to null, then you’re essentially deleting the object. And when JavaScript’s garbage collector runs, the memory that object previously occupied will be freed up to be used later in your program.

```js
book1 = null;
console.log(library);
```

> `WeakMap {Object {title: 'The Catcher in the Rye', author: 'J.D. Salinger'} => false, Object {title: 'Gulliver’s Travels', author: 'Jonathan Swift'} => true}`

What makes this so useful is you don’t have to worry about deleting keys that are referencing deleted objects in your WeakMaps, JavaScript does it for you! When an object is deleted, the object key will also be deleted from the WeakMap when garbage collection runs.

**This makes WeakMaps useful in situations where you want an efficient, lightweight solution for creating groupings of objects with metadata.**

The point in time when garbage collection happens is dependent on a lot of different factors. Check out [MDN’s documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Memory_Management#Garbage_collection) to learn more about the algorithms used to handle garbage collection in JavaScript.