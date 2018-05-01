---
title: Offline Web Applications
description: Programming in HTML5 with JavaScript & CSS3 Training Guide
---
<!-- markdownlint-disable MD022 MD024 MD032 -->
# Chapter 16 - Offline Web Applications

Notes from [Programming in HTML5 with JavaScript & CSS3 Training Guide](https://www.amazon.com/Training-Guide-Programming-JavaScript-Microsoft/dp/0735674388) by Glenn Johnson.

This is part of my study material for passing Microsoft's [Exam 70-480: Programming in HTML5 with JavaScript & CSS3](https://www.microsoft.com/en-us/learning/exam-70-480.aspx) certification exam.

| Lesson 1 | Lesson 2 | Lesson 3 | Lesson 4 |
| ---      | ---      | ---      | ---      |
| [Web SQL](CH16-Offline1-WebSQL.html) | [IndexedDB](CH16-Offline2-IndexedDB.html) | Filesystem API | App Cache |

---

In the previous lesson we learned about web storage, but it's not always the best tool for the job. At times, you might need more advanced features such a *asynchronous* support, *indexing* for faster searching, or *transactions*.

This chapter begins by looking at one option that provides all the power of a relational database, **Web SQL** `(deprecated)`. *Supported by Chrome & Safari only*.

An alternative that's more of an object database is **IndexedDB**. It is supported by all major browser and gives you the power of *indexing* and *transactions* without the need to set up a formal relational structure.

Although both those solutions are good for typical data concerns, neither is designed for storage of files (such as images, docs, XML, & movies). For that need, this chapter discusses the **Filesystem API** `(deprecated)`. *Supported by Chrome only*.

Last, you see how you can make an entire website offline friendly with very little effort by using the offline **Application HTTP Cache (App Cache)** `(deprecated)`. *Supported by all major browsers but is flawed/limited in design. It has been abandoned in favor of **Service Worker***.

## Lesson 1: Web SQL

- [Offline Web Applications - Lesson 1: Web SQL](CH16-Offline1-WebSQL.html)

## Lesson 2: Indexed DB

- [Offline Web Applications - Lesson 2: IndexedDB](CH16-Offline2-IndexedDB.html)

## Lesson 3: Filesystem API

- Offline Web Applications - Lesson 3: Filesystem API

## Lesson 4: Application Cache

- Offline Web Applications - Lesson 4: Application Cache
