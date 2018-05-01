---
title: IndexedDB
description: Programming in HTML5 with JavaScript & CSS3 Training Guide
---
<!-- markdownlint-disable MD022 MD024 MD032 -->
# Chapter 16 - Offline Web Applications

[<-- back to Chapter 16 - Offline Web Applications](CH16-Offline.html)

---

# Lesson 2: IndexedDB
So far, you've seen two extremes for client-side data storage. **Web storage** provides a simple key/value persistence model but lacks some of the features that are important when working with a database.

The other extreme, **Web SQL**, provides many of the features associated with a fully functional relational database but brings with it all the manual work required for setting up and maintaining the persistence structure.

**IndexedDB**  provides a compromise between the two alternatives. It's a key/value database in which values can range from simple strings to complex object structures. To provide for fast retrieval and searching, it includes an easy way to create indexes for each of your object stores.

Much like Web SQL, interfacing with the database is transaction-based and requires minimal effort.

**IndexedDB** is supported by every major browser.

## 1. Using browser-prefix code
It used to be that to work with IndexedDB, you needed to prefix methods with browser-specific code in order to ensure compatibility. This is not so much the case anymore according to [http://caniuse.com](http://caniuse.com). There is now 94.31% coverage with unprexfixed code.

If you still wish to ensure that you code is cross-browser-friendly, you can include the following fix at the top of your scripts.

```js
window.indexedDB = window.indexedDB || window.mozIndexedDB
    || window.webkitIndexedDB || window.msIndexedDB;
window.IDBTransaction = window.IDBTransaction || window.webkitIDBTransaction;
window.IDBCursor = window.IDBCursor || window.webkitIDBCursor;
window.IDBKeyRange = window.IDBKeyRange || window.webkitIDBKeyRange;
```

## 2. Creating and opening the database
The first step in working with IndexedDB is to create a database. You need to access the browser's indexedDB object, which, in the previous example, was assigned to a consistent variable.

```js
var indexedDB = window.indexedDB;
```

This `indexedDB` variable is an IDBFactory object that provides access to your databases through the open method, which has the following parameters.

- **name** The name of the object store
- **version** Optional; the version of the object store

This method returns an IDBRequest object and begins an asynchronous process of opening a connection. The IDBRequest object includes an `onsuccess` event that can be subscribed to, which provides notification when the connection is ready for use. It also includes an `onerror` event that can notify your application if an error occurs during an attempt to connect. The following example shows the open method.

```js
var indexedDB = window.indexedDB;
var openRequest = indexedDB.open('Library', 1);
var db;

openRequest.onsuccess = function(response) {
    db = openRequest.result;
};

openRequest.onerror = function(response) {
    console.log('Error code:' + response.target.errorCode);
};
```

In the example, the open method is called, and, within the `onsuccess` event handler, the `db` variable is assigned a reference to the database object for later use.