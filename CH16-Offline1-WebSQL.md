---
title: Web SQL
description: Programming in HTML5 with JavaScript & CSS3 Training Guide
---
<!-- markdownlint-disable MD022 MD024 MD032 -->
# Chapter 16 - Offline Web Applications

Notes from [Programming in HTML5 with JavaScript & CSS3 Training Guide](https://www.amazon.com/Training-Guide-Programming-JavaScript-Microsoft/dp/0735674388) by Glenn Johnson.

This is part of my study material for passing Microsoft's [Exam 70-480: Programming in HTML5 with JavaScript & CSS3](https://www.microsoft.com/en-us/learning/exam-70-480.aspx) certification exam.

---
[<-- back to Chapter 16 Lesson TOC](CH16-Offline.html)

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

## 4. Adding a table
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

**Live Sample** - [Web SQL - Create database, add table, insert, update, delete](https://james-priest.github.io/node_samples/ch16-OfflineWeb/a-websql1.html)

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

## 5. Using transactions
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

## 6. Inserting a new record
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

**Live Sample** - [Web SQL - Create database, add table, insert, update, delete](https://james-priest.github.io/node_samples/ch16-OfflineWeb/a-websql1.html)

## 7. Updating an existing record
In the following example, the `lastName` of the author, which has an `id` of 1, is updated. Besides the SQL syntax differences, it's very similar to the code used for adding a new record.

```js
var db = openDatabase('Library', '2.0', 'My library', 5 * 1024 * 1024);
var authorId = 1;
var lastName = 'Smith';
db.transaction(function(t) {
    t.executeSql("UPDATE authors SET lastName = ? WHERE id = ?"
        , [lastName, authorId]);
});
```

**Live Sample** - [Web SQL - Create database, add table, insert, update, delete](https://james-priest.github.io/node_samples/ch16-OfflineWeb/a-websql1.html)

## 8. Deleting a record
Removing records is also fairly straightforward. The following example deletes the author record with an `id` of 1.

```js
var db = openDatabase('Library', '2.0', 'My library', 5 * 1024 * 1024);
var authorId = 1;
db.transaction(function(t) {
    t.executeSql("DELETE FROM authors WHERE id = ?", [authorId]);
});
```

**Live Sample** - [Web SQL - Create database, add table, insert, update, delete](https://james-priest.github.io/node_samples/ch16-OfflineWeb/a-websql1.html)

## 9. Reading values from the database
Now that you know how to add data to the database, you can read and display those records back to the user. Create a simple SELECT statement to read all values from the authors table. When `executeSql` is called this time, a callback method is passed that accepts a transaction object and a results set containing the rows returned from the SQL statement.

As the `displayResults` method iterates through the rows, it formats the person's name in a list item and adds it to an unordered list with an `id` of items. To access the individual column values within the row, use dot notation, which reads each as a property on the object.

```js
function displayResults(transaction, results) {
  for (var i = 0; i < results.rows.length; i++) {
    var item = results.rows.items(i);
    $('#items').append('<li>' + item.firstName + ' ' + item.lastName + '</li>');
  }
}

var db = openDatabase('library', '2.0', 'My library', 5 * 1024 * 1024);
db.transaction(function(t) {
    t.executeSql("SELECT * FROM authors", [], displayResults)
});
```

Because you are only retrieving data, you just as easily could have used the `readTransaction` method instead of the `transaction` method.

```js
db.readTransaction(function(t) {
    t.executeSql("SELECT * FROM  authors", [], displayResults);
})
```

> ### Quick check
> - The following statement has a syntax error in the second step of the transaction in this migration script (misspelled CREATE as CRATE). What do you expect will happen because of this migration script?

   ```js
   function migrateDB(transaction) {
       transaction.executeSql("CREATE TABLE authors(firstName TEXT)");
       transaction.executeSql("CREATE TABLE books(title TEXT)");
   }

   var db = openDatabase('Library', '1.0', 'My library', 5 * 1024 * 1024);
   db.changeVersion('1.0', '2.0', migrateDB);
   ```

> ### Answer
> - Neither table will be created.

## 10. Filtering results
You rarely want to read every row from a database table; most of the time, you need to limit those results to specific criteria. Because current implementations are based on SQLite, you have all the power of a mature database engine to help you.

For example, you can add a WHERE clause to return only records with a specific `lastName` value, as follows.

```js
var db = openDatabase('Library', '2.0', 'My library', 5 * 1024 * 1024);
var lastName = 'Priest';
db.transaction(function(t) {
    t.executeSql("SELECT * FROM authors WHERE lastName = ?"
    , [lastName], displayResults);
});
```

You might like to find all `authors` whose last name starts with the letter D. To do so, use the LIKE keyword along with the `%` wildcard.

```js
var lastName = 'D%';
db.transaction(function(t) {
    t.executeSql("SELECT * FROM authors WHERE lastName LIKE ?"
    , [lastName], displayResults);
});
```

## 11. Using JOIN commands
Web SQL includes support for traditional JOIN statements (such as INNER JOIN and LEFT JOIN), which can be used to include columns from multiple tables within a single SELECT statement.

Assume you added a `books` table to your library database and would now like to modify your earlier query to include the title of each book in the results.

```js
var db = openDatabase('Library', '1.0', 'My library', 5 * 1024 * 1024);
var lastName = 'D%';
db.transaction(function(t) {
    t.executeSql("SELECT a.firstName, a.lastName, b.title " +
        "FROM authors a " +
        "INNER JOIN books b on a.id = b.authorId " +
        "WHERE lastName LIKE ?"
        , [lastName], displayResults);
});
```

## 12. Aggregating functions
Another useful feature of Web SQL is the ability to group results, which enables the use of more advanced functions such as COUNT(x), MIN(x), MAX(x), and SUM(x) within your SELECT statements. For example, the following is a new query that finds the number of books written by each author.

```js
db.transaction(function(t) {
    t.executeSql("SELECT a.firstName, a.lastName, COUNT(b.id) as numOfBooks " +
        "FROM authors a " +
        "INNER JOIN books b on a.id = b.authorId " +
        "GROUP BY a.id"
        , [], displayResults);
});
```

## 13. Lesson summary
- The W3C has stated that the Web SQL specification is no longer on tit recommendation track. It may still be used when targeting specific platforms that have continued support, but other options such as **IndexedDB** and **web storage** should be considered when possible.
- Current browser implementations are based on SQLite, which gives you all the power of a full relational database.
- Database communication is started by calling the `openDatabase()` command. If the database does not exist, it will be created automatically.
- Schema migration support is available by using the `changeVersion()` method.
- Web SQL supports a common SQL syntax for create, retrieve, update, & delete (CRUD) operations
- If one statement in a transaction fails, all actions are rolled back.

## 14. Lesson review

1. Which of the following would be a good candidate for Web SQL?
    - [x] Mobile applications built specifically for Safari on the iOS platform
    - [ ] Mobile applications built for any mobile device
    - [ ] Public facing web applications
    - [ ] Mobile applications built specifically for Internet Explorer
2. You need to create a new database. Which of the following command should you use?
    - [ ] `var db = createDatabase('mydb', '1.0', 'My database', 'My database', 5 * 1024 * 1024);`
    - [ ] `var db = new Database('mydb');`
    - [ ] `var db = initDatabase('mydb', '1.0', 'My database', 'My database', 5 * 1024 * 1024);`
    - [x] `var db = openDatabase('mydb', '1.0', 'My database', 'My database', 5 * 1024 * 1024);`
3. Which of the following will correctly insert a new record, using values passed in as SQL arguments to an `executeSql() call?
    - [x] `t.executeSql("INSERT INTO books(title) VALUES(?)", ["Harry Potter"]);`
    - [ ] `t.executeSql("INSERT INTO books(title) VALUES([0])", ["Harry Potter"]);`
    - [ ] `t.executeSql("INSERT INTO books(title) VALUES([1])", ["Harry Potter"]);`
    - [ ] `t.executeSql("INSERT INTO books(title) VALUES({0})", ["Harry Potter"]);`