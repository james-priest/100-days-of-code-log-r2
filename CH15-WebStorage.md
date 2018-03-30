---
title: HTML5 Web Storage
description: Programming in HTML5 with JavaScript & CSS3 Training Guide
---
<!-- markdownlint-disable MD022 MD024 MD032 -->
# Chapter 15 - Web Storage

Notes from [Programming in HTML5 with JavaScript & CSS3 Training Guide](https://www.amazon.com/Training-Guide-Programming-JavaScript-Microsoft/dp/0735674388) by Glenn Johnson.

This is part of my study material for passing Microsoft's [Exam 70-480: Programming in HTML5 with JavaScript & CSS3](https://www.microsoft.com/en-us/learning/exam-70-480.aspx) certification exam.

---

Before Web Storage, the primary means of data storage was to send information back to the server, which requires the application to wait for a round-trip to occur.

To minimize the cost of relying entirely on server-side persistence, browsers now support web storage, a relatively new feature that enables storing small amounts of user data on the client machine.

This chapter begins with an overview of the two storage mechanisms (`localStorage` and `sessionStorage`) and how they can make dramatic improvements in how user data is retained. The chapter then examines how the use of storage events can combat complex problems such as race conditions and synchronization when the user has multiple tabs or browser instances open.

# Lesson 1
## 1. Introducing web storage
Most web applications rely on some method of data storage, which usually involves a server-side solution such as a SQL Server database. However, in many scenarios, that might be excessive, and the ability to store simple, non-sensitive data in you browser would easily meet you needs.

> ### After this lesson, you'll be able to
> - Understand web storage.
> - Implement the `localStorage` object

## 2. Understanding cookies
For years, storing data in the browser could be accomplished by using HTTP cookies, which have provided a convenient way to store small bits of information. Today, cookies are used mostly for storing basic user profile information. The following is an example of how cookies are used.

```js
function setCookie(cookieName, cookieValue, expirationDays) {
    var expirationDate = new Date();
    expirationDate.setDate(expirationDate.getDate() + expirationDays);
    cookieValue = cookieValue + '; expires=' + expirationDate.toUTCString();
    document.cookie = cookieName + '=' + cookieValue;
}

function getCookie(cookieName) {
    var cookies = document.cookie.split(';');

    for (let cookie of cookies) {
        let index = cookie.indexOf('=');
        let key = cookie.substr(0, index);
        let val = cookie.substr(index + 1);

        if (key.trim() === cookieName) { return val; }
    }
}

window.onload = function() {
    setCookie('firstName', 'James', 1);
    var firstName = getCookie('firstName');

    var div = document.getElementById('output');
    div.innerHTML = firstName; // James
};
```

**Live sample:** <a href="https://james-priest.github.io/node_samples/ch15-WebStorage/a-cookie-original.html" target="_blank">ch15-WebStorage/a-cookie-original.html</a>

<!--
## 3. Structuring code with Namespace patterns

While the code above illustrates how to set and retrieve cookie values at a basic level, it's not the best example of how to properly structure code.

It might be out of place here, but I decided to show four additional methods of structuring this code using four of Addy Osmani's [Essential JavaScript Namespacing Patterns](https://addyosmani.com/blog/essential-js-namespacing/#beginners).

1. **Functions in global namespace** - This is the code from above. It pollutes the global namespace and is prone to code collision. It is not one of the four examples but is included here for comparison.
    ```js
    var someValue = '';
    var anotherValue = '';
    thisFunction(/*...*/) { /*...*/ }
    thatFunction(/*...*/) { /*...*/ }
    ```

    ```js
    function setCookie(/*...*/) {
        /*...*/
    }

    function getCookie(/*...*/) {
        /*...*/
    }

    setCookie('firstName', 'James', 1);
    var firstName = getCookie('firstName');
    ```
    **Live sample:** <a href="https://james-priest.github.io/node_samples/ch15-WebStorage/a-cookie-original.html" target="_blank">ch15-WebStorage/a-cookie-original.html</a>
2. **Single global variable** - This uses a single global variable and assigns to it an Immediately Invoked Function Expression (IIFE).
    ```js
    var myApplication =  (function() {
        var myProp = '';
        var myFunc = function() {
            /*...*/
        };
        return{
            prop1: myProp,
            func1: myFunc
        }
    })();
    ```

    ```js
    var cookieApp = (function() {
        var _setCookie = function(/*...*/) {
            /*...*/
        };
        var _getCookie = function(/*...*/) {
            /*...*/
        };

        return {
            getCookie: _getCookie,
            setCookie: _setCookie
        };
    })();

    cookieApp.setCookie('firstName1', 'James 1!', 1);
    var firstName = cookieApp.getCookie('firstName1');
    ```
    **Live sample:** <a href="https://james-priest.github.io/node_samples/ch15-WebStorage/a-cookie1-global-var.html" target="_blank">ch15-WebStorage/a-cookie1-global-var.html</a>
3. **Object literal notation** - This can be thought of as an object containing a collection of key/value pairs. Object literals have the advantage of not polluting the global namespace and helping organize code and parameters logically.
    ```js
    var myApplication = {
        getInfo: function(){ /*...*/ },

        /* we can also populate our object literal to support
         * further object literal namespaces */
        models : {},
        views : {
            pages : {}
        },
        collections : {}
    };
    ```

    ```js
    var cookieApp = cookieApp || {};

    cookieApp = {
        setCookie: function(/*...*/) {
            /*...*/
        },
        getCookie: function(/*...*/) {
            /*...*/
        }
    };

    cookieApp.setCookie('firstName2', 'James 2!', 1);
    var firstName = cookieApp.getCookie('firstName2');
    ```
    **Live sample:** <a href="https://james-priest.github.io/node_samples/ch15-WebStorage/a-cookie2-literal-notation.html" target="_blank">ch15-WebStorage/a-cookie2-literal-notation.html</a>
4. **Nested namespace pattern** - An extension of the object literal pattern is nested namespacing. It allows further segmentation and organization of code beyond a single level.
    ```js
    var myApp =  myApp || {};

    /* perform a similar existence check when defining nested children */
    myApp.routers = myApp.routers || {};
    myApp.model = myApp.model || {};
    myApp.model.special = myApp.model.special || {};
    ```

    ```js
    var myApp = myApp || {};
    myApp.cookie = myApp.cookie || {};

    myApp.cookie= {
        setCookie: function(/*...*/) {
            /*...*/
        },
        getCookie: function(/*...*/) {
            /*...*/
        }
    };

    myApp.cookie.setCookie('firstName3', 'James 3!', 1);
    var firstName = myApp.cookie.getCookie('firstName3');
    ```
    **Live sample:** <a href="https://james-priest.github.io/node_samples/ch15-WebStorage/a-cookie3-nested-namespace.html" target="_blank">ch15-WebStorage/a-cookie3-nested-namespace.html</a>
5. **Immediately Invoked Function Expression** - An IIFE is effectively an unnamed function which is immediately invoked after it's been defined.
    ```js
    var namespace = namespace || {};

    /* here a namespace object is passed as a function parameter.
     * this allows us to assign public methods and properties to it. */
    (function( o ){
        o.foo = "foo";
        o.bar = function(){
            return "bar";
        };
    })(namespace);

    console.log(namespace);
    ```

    ```js
    var cookieApp = cookieApp || {};

    (function(o) {
        o.setCookie = function(/*...*/) {
            /*...*/
        };

        o.getCookie = function(/*...*/) {
            /*...*/
        };
    })(cookieApp);

    cookieApp.setCookie('firstName4', 'James 4!', 1);
    var firstNAme = cookieApp.getCookie('firstName4');
    ```
    **Live sample:** <a href="https://james-priest.github.io/node_samples/ch15-WebStorage/a-cookie4-iife-wrapped.html" target="_blank">ch15-WebStorage/a-cookie4-iife-wrapped.html</a>

Code samples in upcoming lessons will be written to the global namespace. This is done to keep things simple and not convolute the concepts with an extra layer of code.

Keep in mind though, the patterns discussed above should be used at all times to best organize, encapsulate, and protect your code from collision.

One additional point is that these patterns specifically relate to namespacing and are separate and distinct from the object-oriented design patterns that were covered last week. This includes such things as constructor functions, inheritance patterns, and object reflection code.

The last thing to keep in mind is that both namespacing and object-oriented patterns can be combined to provide protection, encapsulation, and organization of your code.

## 4. Using the jQuery cookie plug-in
The example demonstrates that working with cookies isn't complicated, but the interface for doing so leaves much to be desired. To simplify working with cookies, you can use the jQuery Cookie plug-in available at [https://github.com/carhartl/jquery-cookie](https://github.com/carhartl/jquery-cookie). Here is the modified code example when using the jQuery plug-in.

```js
$.cookie('firstName', 'James');
var firstName = $.cookie('firstName');
```

This example shows that the plug-in provides a much simpler interface.

## 5. Working with cookie limitations
Cookies will continue to be an effective tool for the foreseeable future, but they have some drawbacks.

- **Capacity limitations** Cookies are limited to about 4KB of data, which is not large, although you can create more than 30 cookies per site. (The actual maximum limit depends on the browser being used; the average is between 30 and 50.)
- **Overhead** Every cookie is sent with each HTTP request/response made, regardless of whether the values are needed. This is often true even for requests for static content (such as images, css files, and js files), which can create heavier-than-necessary HTTP messages.

## 6. Understanding HTML5 storage
Existing solutions leave a lot to be desired; HTML5 breaks new group with several innovative tools. Each is unique and carries its own set of pros and cons, which will be discussed individually.

- **Web Storage** Easily the simplest new form of storage, web storage provides a way to store key/value pairs of data in a manner that rivals cookies in ease of use. It is currently the most widely supported option and consists of both `localStorage` and `sessionStorage`.
- **Web SQL** `(deprecated)` For more complex applications, this was a good alternative to web storage. It provides the power of a full relational database, including support for SQL commands, transactions, and performance tuning. It is currently supported by Chrome and Safari. It is not supported by IE, Firefox or Edge.
- **IndexedDB** This option is a non-relational (NoSQL) database. It provides simplicity that's similar to web storage while still accommodating common needs such as indexing and transactions.
- **Filesystem API** `(deprecated)` This tool is useful for storing larger data types such as text files, images, and movies. However, it suffers from a lack of adoption. It is currently only supported by Chrome.

-->