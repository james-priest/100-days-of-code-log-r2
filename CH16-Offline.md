---
title: Offline Web Applications
description: Programming in HTML5 with JavaScript & CSS3 Training Guide
---
<!-- markdownlint-disable MD022 MD024 MD032 -->
# Chapter 16 - Offline Web Applications

Notes from [Programming in HTML5 with JavaScript & CSS3 Training Guide](https://www.amazon.com/Training-Guide-Programming-JavaScript-Microsoft/dp/0735674388) by Glenn Johnson.

This is part of my study material for passing Microsoft's [Exam 70-480: Programming in HTML5 with JavaScript & CSS3](https://www.microsoft.com/en-us/learning/exam-70-480.aspx) certification exam.

---

In the previous lesson we learned about web storage, but it's not always the best tool for the job. At times, you might need more advanced features such a asynchronous support, indexing for faster searching, or transactions.

This chapter begins by looking at one option that provides all the power of a relational database, **Web SQL** `(deprecated)`. *Supported by Chrome & Safari only*.

An alternative that's more of an object database is **IndexedDB**. It is supported by all major browser and gives you the power of indexing and transactions without the need to set up a formal relational structure.

Although both those solutions are good for typical data concerns, neither is designed for storage of files (such as images, docs, XML, & movies). For that need, this chapter discusses the **Filesystem API** `(deprecated)`. *Supported by Chrome only*.

Last, you see how you can make an entire website offline friendly with very little effort by using the offline **Application HTTP Cache (App Cache)** `(deprecated)`. *Supported by all major browsers but is flawed/limited in design. It has been abandoned in favor of **Service Worker***.

# Lesson 1: Web SQL
Web SQL is arguably one of the most powerful options available to you. It provides a full relational database that includes many of the features you've come to enjoy from server-side database offerings.

Most implementations are built on SQLite, which is one of the most widely used lightweight database engines. It's an open-source solution with a vibrant community backing it.

## 1. Applicability of Web SQL
Before starting with Web SQL, be aware that the W3C has stated that Web SQL is no longer on its recommendation track and that it does not intend to maintain the specification.

What this means depends on the browser you're targeting. While the spec is no longer being maintained, some browsers (Safari and Chrome) have continued their support.

Therefore, Web SQL might be a viable option if you're building specifically for a platform such as iOS for iPad or iPhone. Another common use is in building Google Chrome extensions.

If you need a browser-agnostic solution then you might be better off with IndexedDB instead.

## 2. Creating & opening the database
In the following sections, examine the syntax used to create or open a database, start a transaction, and execute a SQL command. Most of these command should look very familiar if you've used other relational databases.

To start communication with a database, use the `openDatabase` method, which returns a Database object. If you attempt to open a database that doesn't exist, it will be automatically created for you, so you won't need to execute any extra steps.

The following are the `openDatabase` parameters.

- **name** The database name, which is case-sensitive. Most characters are allowed; even an empty string is considered valid.
- **version** Expected version of the database. If an empty string is passed, it's implied that whatever version currently exists is fine.
- **displayName** Descriptive name of the database.
- **estimatedSize** Estimated size required for the database. The typical default value is 5 MB; the browser might prompt the user for permission, depending on the size you specify.
- **creationCallback** If the database does not yet exist and is being created, this callback will be invoked. It is optional and not needed for the database to be created and versioned correctly.

In the following example, a database named `Library` is created with an estimated size of 5 MB. It returns a Database object that supports transactional operations.

```js
var db = openDatabase('Library', '1.0', 'My library', 5 * 1024 *1024);
```

If you're familiar with traditional database connections, you might be expecting a need to close a connection. With Web SQL, however, that's automatically handled, so you don't have to close the connection manually.

## 3. Performing schema updates
As your application grows, your data requirements change. You might need to add new tables, drop existing ones, or even change particular columns. The Database object provides the following hooks for making those changes.

- **version** Property that gets the current schema version
- **changeVersion** Method for performing schema changes between one version and the next
  - **oldVersion** Schema version you are migrating from
  - **newVersion** Schema version you are migrating to
  - **callback** Callback method containing schema changes such as adding and dropping tables
  - **errorCallback** Optional; callback method is invoked if an error occurs while the transaction is being processed
  - **successCallback** Optional; callback method is invoked if all statements successfully execute within the transaction

## 3a. Adding a table
You can add an `authors` table to the `Library` created earlier. You need a callback method that accepts a transaction object, which executes the `CREATE TABLE` script.

The transaction object allows multiple actions within it, and it automatically rolls back all changes if any fail. For now, this example keeps the idea simple by adding just one table.

```js
function migrateDB(transaction) {
    transaction.executeSql("CREATE TABLE IF NOT EXISTS authors(" + 
        "id INTEGER PRIMARY KEY AUTOINCREMENT, " +
        "firstName TEXT, " +
        "lastName TEXT, " +
        "dateCreated TIMESTAMP DEFAULT(datetime('now', 'localtime')))"
    );
}
function onError(error) {
    console.log('Error Code:', error.code, 'Message: ', error.message );
}
function onSuccess() {
    console.log('Migration complete!');
}

var db = openDatabase('Library', '1.0', 'My  library', 5 * 1024 * 1024);
db.changeVersion('1.0', '2.0', migrateDB, onError, onSuccess);
```

Later in the chapter, you can read the version property of the Database object to determine the schema version with which you are working.

Note that version updates are applied asynchronously, so if the following line was placed immediately after the `db.changeVersion()` call in the preceding code, it would still display 1.0 because the `console.log()` method would fire before the migrations had a chance to complete.

```js
console.log("Current schema:", db.version);
```

Now that the migration has been applied, you have a new table in your database with the following columns.

- **id** Table identifier; new records are automatically assigned an `id` that is one greater than the id of the last record added.
- **firstName** Text field for storing a person's first name.
- **lastName** Text field for storing a person's last name.
- **dateCreated** Time stamp; when a record is first created, this column defaults to the current time with the help of the SQLite datetime method. Instead of using of using its default mode of GMT, you can indicate that it should use the local time zone.

## 4. Using transactions
Now that you have a schema in place, you can use transactions to execute SQL statements. To do this, the Database object provides the following two methods.

- **transaction** Starts a new transaction that executes SQL statements; allows both read and write command
- **readTransaction** Works similarly to the transaction method but allows read commands only

Both methods accept the same three parameters.
- **callback** Callback method containing the individual commands that are to be executed as part of the transaction
- **errorCallback** Optional callback method invoked if an error occurs while the transaction is being processed
- **successCallback** Optional callback method invoked if all statements successfully execute within the transaction

The callback method will receive a transaction object that includes an `executeSql` method for performing data changes. It has the following parameters.

- **sqlStatement** The SQL statement string to be executed
- **arguments** Array of object parameters to be used by the SQL command.
- **callback** Optional callback method invoked after the command is executed. When data is retrieved, this method includes the collection of selected rows.
- **errorCallback** Optional callback method invoked if an error occurs while the statement is being executed

In the next section, you see how you can use the transactions to execute some of the most commonly used SQL commands.

## 4a. Inserting a new record
Now that you have a database and table in place, add a new record. Like creating a new table, do this by using the `executeSql` method on the transaction instance.

```js
var db = openDatabase('Library', '2.0', 'My library', 5 * 1024 * 1024);

db.transaction(function(t) {
    t.executeSql("INSERT INTO authors (firstName, lastName) " +
        " VALUES ('James', 'Priest')");
});
```

However, in general, it's a good idea to useSQL parameters when working with dynamic SQL. The preceding statement can be rewritten to take advantage of an optional second parameter on the `executeSql` method, which accepts an array of field values.

Note the use of the question marks to indicate that the value will be populated from the array being passed in.

```js
var firstName = 'James';
var lastName = 'Priest';
db.transaction(function(t) {
    t.executeSql("INSERT INTO authors (firstName, lastName) VALUES(?, ?)",
        [firstName, lastName]);
});
```

You can go a step further by adding a callback to the `executeSql` method, which enables you to capture the `Id` of the newly created row.

```js
function itemInserted(transaction, results) {
    console.log("Id:", results.insertId);
}

var firstName = 'James';
var lastName = 'Priest';
db.transaction(function(t) {
    t.executeSql("INSERT INTO authors (firstName, lastName) VALUES(?, ?)",
        [firstName, lastName],
        itemInserted);
});
```
