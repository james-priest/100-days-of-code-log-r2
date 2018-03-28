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
    var cookies = document.cookie.split('; ');

    for (let cookie of cookies) {
        let index = cookie.indexOf('=');
        let key = cookie.substr(0, index);
        let val = cookie.substr(index + 1);

        if (key === cookieName) { return val; }
    }
}

window.onload = function() {
    setCookie('firstName', 'James', 1);
    var firstName = getCookie('firstName');

    var div = document.getElementById('cookie');
    div.innerHTML = firstName;  // "James"
};
```