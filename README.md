<!-- markdownlint-disable MD022 MD032 -->
# James Priest

## 100 Days Of Code Log R2

**Commitment:** ***I will code daily for the next 100 days.***

This is part of Alexander Kallaway's [100DaysOfCode](https://github.com/Kallaway/100-days-of-code "the official repo") challenge. More details about the challenge can be found here: [100daysofcode.com](http://100daysofcode.com/ "100daysofcode.com").

|  Start Date   | End Date     |
| ------------- | ------------ |
| January 28, 2018 | --- |

## Goals

- [x] Code daily
- [x] Complete the Intermediate Mobile Web track of the [#GoogleUdacityScholars](https://twitter.com/search?q=%23GoogleUdacityScholars&src=tyah) program.
- [ ] Pass my Microsoft Programming in HTML5 with JavaScript & CSS3 Cert - [Exam 70-480](https://www.microsoft.com/en-us/learning/exam-70-480.aspx "Exam 70-480: Programming in HTML5 with JavaScript and CSS3")

# Log
<!--

## 1.
### Day 1: January,10 2018 - Saturday

**Project:** Mobile Web trackS

**Progress:**

**Thoughts:**

**Link to Work:**

-->
---

## 49. VSCode from Scratch
### Day 49: March 16, 2018 - Friday

**Project:** Study for MS 70-480 Cert Exam (Programming in HTML5 with JavaScript & CSS3)

[![vscode plugins](assets/images/sm_vscode-plugins.jpg)](assets/images/full-size/chap14-6.png)

**Progress:** Today I decided to wipe clean my Visual Studio Code installation and start fresh. I had many plug-ins installed that were using resources and keeping me from a streamlined coding experience.

I also had quite a few modifications to my user settings, including linting, code formatting, themes, icons, plugin settings, etc.

I did a number of things before a fresh install:

1. Made a list of all currently used plugins (so I could reinstall the ones I wanted)
2. Uninstalled Visual Studio Code
3. Renamed the `extensions` directory (to clear out old extensions)
4. Renamed the `Code` directory within %UserDir%/AppData/Roaming  (to start with a fresh user settings)
5. Installed fresh copy

Once this was done, I proceeded to install the extensions I wanted along with some new ones. Everything runs clean and smooth now.

---

## 48. Geolocation Pt3
### Day 48: March 15, 2018 - Thursday

**Project:** Study for MS 70-480 Cert Exam (Programming in HTML5 with JavaScript & CSS3)

[![14-6](assets/images/sm_chap14-6.jpg)](assets/images/full-size/chap14-6.png)

**Progress:** This last lesson covered the use of Geolocation API with Google Maps API.

This lesson detailed the following.

- Properly referencing the Google Maps API
- Setting the `options` object for use with the Google Maps API
- Creating and setting a Map and Marker object

The live sample can be viewed here: [Position Mapper](https://james-priest.github.io/node_samples/ch14-Geolocation/c-position-mapper1.html)

**Links:**
- Course Notes - [Chapter 14 - Geolocation](CH14-Geolocation.html)
- Geolocation sample 1- [Latitude, longitude, & timestamp output](https://james-priest.github.io/node_samples/ch14-Geolocation/a-geolocation2.html)
- Geolocation sample 2- [GPS Watch Position](https://james-priest.github.io/node_samples/ch14-Geolocation/b-watchPosition2.html)
- Geolocation sample 3- [Position Mapper](https://james-priest.github.io/node_samples/ch14-Geolocation/c-position-mapper1.html)
- GitHub Repo - [Geolocation GitHub Repo](https://github.com/james-priest/node_samples/tree/master/ch14-Geolocation)

---

## 47. Geolocation Pt2
### Day 47: March 14, 2018 - Wednesday

**Project:** Study for MS 70-480 Cert Exam (Programming in HTML5 with JavaScript & CSS3)

[![14-5](assets/images/sm_chap14-5.jpg)](assets/images/full-size/chap14-5.png)

**Progress:** This lesson covered the use of the `watchPosition()` method to continuously monitor changes in GPS positioning and call a success function in order to respond to the changes.

This lesson detailed the following.

- `navigator.geolocation.watchPosition()` method.
- Use of `watchPosition()`'s return value `watchId` with the `clearWatch()` method.
- Various methods to calculate distance between two points over a curved surface (earth).
- Calculation of distance traveled using the _haversine_ formula.

The live sample can be viewed here: [GPS Watch Position](https://james-priest.github.io/node_samples/ch14-Geolocation/b-watchPosition2.html)

**Links:**
- Course Notes - [Chapter 14 - Geolocation](CH14-Geolocation.html)
- Geolocation sample 1- [Latitude, longitude, & timestamp output](https://james-priest.github.io/node_samples/ch14-Geolocation/a-geolocation2.html)
- Geolocation sample 2- [GPS Watch Position](https://james-priest.github.io/node_samples/ch14-Geolocation/b-watchPosition2.html)
- GitHub Repo - [Geolocation GitHub Repo](https://github.com/james-priest/node_samples/tree/master/ch14-Geolocation)

---

## 46. Geolocation Pt1
### Day 46: March 13, 2018 - Tuesday

**Project:** Study for MS 70-480 Cert Exam (Programming in HTML5 with JavaScript & CSS3)

```js
$(document).ready(function() {
    getLocation();
});
function supportsGeolocation() {
    return 'geolocation' in navigator;
}
function getLocation() {
    if (supportsGeolocation()) {
        navigator.geolocation.getCurrentPosition(showPosition, showError);
    } else {
        showMessage("Geolocation isn't supported by your browser");
    }
}
function showPosition(position) {
    var datetime = new Date(position.timestamp).toLocaleString();

    showMessage('Latitude: ' + position.coords.latitude + '<br>' +
        'Longitude: ' + position.coords.longitude + '<br>' +
        'Timestamp: ' + datetime);
}
```

[![14-1](assets/images/sm_chap14-1.jpg)](assets/images/full-size/chap14-1.png)

**Progress:** This lesson covers the basics of the Geolocation API which at its most basic returns latitude and longitude positions from which to use with multiple third-party apps and services.

This lesson detailed the following.

- `navigator.geolocation.getCurrentPosition()` method
- Position object which is returned from `getCurrentPosition()` method. It contains the `coords` and `timestamp` properties
- Coordinates object which contains properties for `latitude`, `longitude`, `altitude`, `accuracy`, `altitudeAccuracy`, `heading`, & `speed`.

**Links:**
- Course Notes - [Chapter 14 - Geolocation](CH14-Geolocation.html)
- Geolocation sample- [Latitude, longitude, & timestamp output](https://james-priest.github.io/node_samples/ch14-Geolocation/a-geolocation2.html)
- GitHub Repo - [Geolocation GitHub Repo](https://github.com/james-priest/node_samples/tree/master/ch14-Geolocation)

---

## 45. Scramble Game Pt3
### Day 45: March 12, 2018 - Monday

**Project:** Study for MS 70-480 Cert Exam (Programming in HTML5 with JavaScript & CSS3)

[![13-12](assets/images/sm_chap13-14.jpg)](assets/images/full-size/chap13-14.png)

**Progress:** We finish part 3 of the HTML5 Drag & Drop number scramble game by adding keyboard controls and wrapping up some game functions.

This includes:

- Allowing tile movement with arrow keys
- Creating a key press animation to show the user what key was pressed
- Creating a `scramble()` tile function
- Building a `checkForWinner()` function

Here's the completed game: [Scramble Game](https://james-priest.github.io/node_samples/ch13-Drag-Drop/d-scramble3.html)

**Links:**
- Course Notes - [Chapter 13 - Drag and Drop](CH13-Drag-Drop.html)
- Drag & Drop sample 1- [Numbers](https://james-priest.github.io/node_samples/ch13-Drag-Drop/a-scramble4.html)
- Drag & Drop sample 2- [List](https://james-priest.github.io/node_samples/ch13-Drag-Drop/b-cars1.html)
- Drag & Drop sample 3- [Files](https://james-priest.github.io/node_samples/ch13-Drag-Drop/c-files2.html)
- Drag & Drop sample 4- [Scramble Game](https://james-priest.github.io/node_samples/ch13-Drag-Drop/d-scramble3.html)
- GitHub Repo - [Drag and Drop GitHub Repo](https://github.com/james-priest/node_samples/tree/master/ch13-Drag-Drop)

---

## 44. Scramble Game Pt2
### Day 44: March 11, 2018 - Sunday

**Project:** Study for MS 70-480 Cert Exam (Programming in HTML5 with JavaScript & CSS3)

[![13-12](assets/images/sm_chap13-12.jpg)](assets/images/full-size/chap13-12.png)

**Progress:** In part 2 of the HTML5 Drag & Drop number scramble game we actually write the bulk of the actual drag and drop code

This includes:

- Wiring up drag and drop events
- Using the DataTransfer object to send data from the drag source to the drop destination
- Logic to evaluate which drops are allowed and to carry those out

Here's the work in progress: [WIP - Scramble Game v2](https://james-priest.github.io/node_samples/ch13-Drag-Drop/d-scramble2.html)

**Links:**
- Course Notes - [Chapter 13 - Drag and Drop](CH13-Drag-Drop.html)
- Drag & Drop sample 1- [Numbers](https://james-priest.github.io/node_samples/ch13-Drag-Drop/a-scramble4.html)
- Drag & Drop sample 2- [List](https://james-priest.github.io/node_samples/ch13-Drag-Drop/b-cars1.html)
- Drag & Drop sample 3- [Files](https://james-priest.github.io/node_samples/ch13-Drag-Drop/c-files2.html)
- Drag & Drop sample 4- [Scramble Game](https://james-priest.github.io/node_samples/ch13-Drag-Drop/d-scramble3.html)
- GitHub Repo - [Drag and Drop GitHub Repo](https://github.com/james-priest/node_samples/tree/master/ch13-Drag-Drop)

---

## 43. Scramble Game Pt1
### Day 43: March 10, 2018 - Saturday

**Project:** Study for MS 70-480 Cert Exam (Programming in HTML5 with JavaScript & CSS3)

[![13-11](assets/images/sm_chap13-11.jpg)](assets/images/full-size/chap13-11.png)

**Progress:** Here we gain experience implementing HTML5 Drag & Drop by building a number scramble game.

The first section covers:

- Basic layout and structure of the game
- Starting point for HTML, CSS, JavaScript, & jQuery

The work in progress page is here : [Scramble Game v1](https://james-priest.github.io/node_samples/ch13-Drag-Drop/d-scramble1.html)

**Links:**
- Course Notes - [Chapter 13 - Drag and Drop](CH13-Drag-Drop.html)
- Drag & Drop sample 1- [Numbers](https://james-priest.github.io/node_samples/ch13-Drag-Drop/a-scramble4.html)
- Drag & Drop sample 2- [List](https://james-priest.github.io/node_samples/ch13-Drag-Drop/b-cars1.html)
- Drag & Drop sample 3- [Files](https://james-priest.github.io/node_samples/ch13-Drag-Drop/c-files2.html)
- Drag & Drop sample 4- [Scramble Game](https://james-priest.github.io/node_samples/ch13-Drag-Drop/d-scramble3.html)
- GitHub Repo - [Drag and Drop GitHub Repo](https://github.com/james-priest/node_samples/tree/master/ch13-Drag-Drop)

---

## 42. HTML5 Drag & Drop Pt2
### Day 42: March 9, 2018 - Friday

**Project:** Study for MS 70-480 Cert Exam (Programming in HTML5 with JavaScript & CSS3)

[![13-7](assets/images/sm_chap13-7.jpg)](assets/images/full-size/chap13-7.png)

**Progress:** This lesson got into the DataTransfer object and how to use it to effectively move data from the drag location to the drop location.

This covered:

- Using DataTransfer with jQuery
- Using DataTransfer methods `getData()`, `setData()`, & `clearData()`
- Using DataTransfer properties `dropeffect`, `effectAllowed`, `files`, and `types`
- Working with the `drop` event
- Dragging and dropping files with FileList and the Files API object

[![13-9](assets/images/sm_chap13-9.jpg)](assets/images/full-size/chap13-9.png)

**Links:**
- Course Notes - [Chapter 13 - Drag and Drop](CH13-Drag-Drop.html)
- Drag & Drop sample 1- [Numbers](https://james-priest.github.io/node_samples/ch13-Drag-Drop/a-scramble4.html)
- Drag & Drop sample 2- [List](https://james-priest.github.io/node_samples/ch13-Drag-Drop/b-cars1.html)
- Drag & Drop sample 3- [Files](https://james-priest.github.io/node_samples/ch13-Drag-Drop/c-files2.html)
- GitHub Repo - [Drag and Drop GitHub Repo](https://github.com/james-priest/node_samples/tree/master/ch13-Drag-Drop)

---

## 41. HTML5 Drag & Drop Pt1
### Day 41: March 8, 2018 - Thursday

**Project:** Study for MS 70-480 Cert Exam (Programming in HTML5 with JavaScript & CSS3)

[![13-6](assets/images/sm_chap13-6.jpg)](assets/images/full-size/chap13-6.png)

**Progress:** This lesson covered some of the basics behind of Drag and Drop with HTML5. This includes:

- HTML5 `draggable` attribute
- CSS autoprefixing ([https://autoprefixer.github.io/](https://autoprefixer.github.io/)) and [https://caniuse.com/](https://caniuse.com/)
- Drag events (`dragstart`, `drag`, and `dragend`)
- Drop events (`dragenter`, `dragover`, `dragleave`, and `drop`)
- Moving the dropped node from one part of the DOM to another

**Links:**
- Course Notes - [Chapter 13 - Drag and Drop](CH13-Drag-Drop.html)
- Drag & Drop sample - [Scramble](https://james-priest.github.io/node_samples/ch13-Drag-Drop/a-scramble4.html)
- GitHub Repo - [Drag and Drop GitHub Repo](https://github.com/james-priest/node_samples/tree/master/ch13-Drag-Drop)

---

## 40. HTML5 SVG
### Day 40: March 7, 2018 - Wednesday

**Project:** Study for MS 70-480 Cert Exam (Programming in HTML5 with JavaScript & CSS3)

[![12-26](assets/images/sm_chap12-29.jpg)](assets/images/full-size/chap12-26.png)

**Progress:** This lesson covered some of the basics behind SVG. This included:

- Use of `<svg>`, `<path>`, and `<circle>` elements
- Various path commands to create complex shapes
- Assigning an `.svg` file to an `<img>` element
- Making SVG's scalable

**Links:**
- Course Notes - [Chapter 12 - SVG](CH12-SVG.html)
- Online SVG Editor - [SVG-edit](https://svg-edit.github.io/svgedit/releases/svg-edit-2.8.1/svg-editor.html)
- GitHub Repo - [SVG GitHub Repo](https://github.com/james-priest/node_samples/tree/master/ch12-SVG)

---

## 39. HTML5 Canvas Pt4
### Day 39: March 6, 2018 - Tuesday

**Project:** Study for MS 70-480 Cert Exam (Programming in HTML5 with JavaScript & CSS3)

[![12-26](assets/images/sm_chap12-26.jpg)](assets/images/full-size/chap12-26.png)

**Progress:** This completes the lesson on HTML5 `<canvas>` element. In the last section we covered:

- Using the `arc()` method to create circles and circle fragments
- Setting text with the `font` property
- Drawing text on the canvas with `fillText()` and `strokeText()` methods
- Including images on the canvas with `drawImage()`
- Tying it all together by including text, lines, and images.

[![12-22](assets/images/sm_chap12-22.jpg)](assets/images/full-size/chap12-22.png)

**Links:**
- Course Notes - [Chapter 12 - HTML5 Canvas](CH12-Canvas.html)
- Code samples - [Index page of code samples](https://james-priest.github.io/node_samples/ch12-Canvas/samples.html)
- GitHub Repo - [HTML5 Canvas GitHub Repo](https://github.com/james-priest/node_samples/tree/master/ch12-Canvas)

---

## 38. HTML5 Canvas Pt3
### Day 38: March 5, 2018 - Monday

**Project:** Study for MS 70-480 Cert Exam (Programming in HTML5 with JavaScript & CSS3)

[![12-17](assets/images/sm_chap12-17.jpg)](assets/images/full-size/chap12-17.png)

**Progress:** This lesson covered lots of areas, including:

- Setting lineWidth, lineJoin, & strokeStyle
- Saving and restoring drawing state
- Drawing with paths
- Creating lines & rectangles
- Using fill & stroke methods
- Order of method calls
- Creating arcs using arcTo method

[![12-18](assets/images/sm_chap12-18.jpg)](assets/images/full-size/chap12-18.png)

**Links:**
- Course Notes - [Chapter 12 - HTML5 Canvas](CH12-Canvas.html)
- Code samples - [Index page of code samples](https://james-priest.github.io/node_samples/ch12-Canvas/samples.html)
- GitHub Repo - [HTML5 Canvas GitHub Repo](https://github.com/james-priest/node_samples/tree/master/ch12-Canvas)

---

## 37. HTML5 Canvas Pt2
### Day 37: March 4, 2018 - Sunday

**Project:** Study for MS 70-480 Cert Exam (Programming in HTML5 with JavaScript & CSS3)

[![12-4](assets/images/sm_chap12-4.jpg)](assets/images/full-size/chap12-4.png)

**Progress:** This lesson got into combining `fillStyle` with `fillRect()` for some interesting drawings.

Specifically covered:

- Using CSS color with `fillStyle`
- Using gradients with `fillStyle`
- Using patterns with `fillStyle`

[![12-3](assets/images/sm_chap12-3.jpg)](assets/images/full-size/chap12-3.png)

**Links:**
- Course Notes - [Chapter 12 - HTML5 Canvas](CH12-Canvas.html)
- Code samples - [Index page of code samples](https://james-priest.github.io/node_samples/ch12-Canvas/samples.html)
- GitHub Repo - [HTML5 Canvas GitHub Repo](https://github.com/james-priest/node_samples/tree/master/ch12-Canvas)

---

## 36. HTML5 Canvas Pt1
### Day 36: March 3, 2018 - Saturday

**Project:** Study for MS 70-480 Cert Exam (Programming in HTML5 with JavaScript & CSS3)

[![12-2](assets/images/sm_chap12-2.jpg)](assets/images/full-size/chap12-2.png)

**Progress:** This lesson covered the use of the `<canvas>` element as well as the `CanvasRenderingContext2D` object and API.

Also covered:

- Properties and methods of context object for drawing with JavaScript
- Implementing the canvas
- Basic rectangle methods: `fillRect()`, `strokeRect()`, & `clearRect()`

**Links:**
- Course Notes - [Chapter 12 - HTML5 Canvas](CH12-Canvas.html)
- Code samples - [Index page of code samples](https://james-priest.github.io/node_samples/ch12-Canvas/samples.html)
- GitHub Repo - [HTML5 Canvas GitHub Repo](https://github.com/james-priest/node_samples/tree/master/ch12-Canvas)

---

## 35. HTML5 Media
### Day 35: March 2, 2018 - Friday

**Project:** Study for MS 70-480 Cert Exam (Programming in HTML5 with JavaScript & CSS3)

[![11-1](assets/images/sm_chap11-1.jpg)](assets/images/full-size/chap11-1.png)

**Progress:** This lesson covered the use of the `<video>` and `<audio>` HTML elements as well as the `HTMLMediaElement` object and API.

Also covered:

- `<source>` &  `<track>` elements
- Video formats
- Closed captioning and subtitles
- HTMLMediaElement properties, methods, & events
- Controlling media playback through code

[![11-2](assets/images/sm_chap11-2.jpg)](assets/images/full-size/chap11-2.png)

**Links:**
- Course Notes - [Chapter 11 - HTML5 Media](CH11-HTML5-Media.html)
- [HTML5 Media code on GitHub](https://github.com/james-priest/node_samples/tree/master/ch11-HTML5-Media) - Sample code showing how to embed video and audio elements in page.

---

## 34. WebSocket API
### Day 34: March 1, 2018 - Thursday

**Project:** Study for MS 70-480 Cert Exam (Programming in HTML5 with JavaScript & CSS3)

[![10-2](assets/images/sm_chap10-2.jpg)](assets/images/full-size/chap10-2.png)

**Progress:** This lesson covered the use of the WebSocket protocol which establishes a two-way, bidirectional connection between the browser and the web server.

This is done with little overhead (2 bytes) and no headers. The light weight structure of the WebSocket protocol makes is an easy choice for any real-time applications such as chat, gaming, and live content.

Here's a quick bullet list of take-away's:

- The WebSocket protocol provides a standardized way to establish a two-way (bi-directional) connection between the browser and the web server while keeping the connection open.
- The WebSocket object contains methods to open connections, send data, & close connections
- It contains the following events: `onclose`, `onmessage`, `onerror`, and `onopen`.
- You can check the `readyState` property on the WebSocket object to obtain the state of the connection.
- Use `ws://` for WebSocket protocol or `wss://` for secure WebSocket protocol.
- Timeouts, dropped connections, web farm implementations, and browser incompatibility are problems you must resolve when implementing WebSocket or you can use a pre-built library such as SignalR or Socket.IO.

**Links:**
- Course Notes - [Chapter 10 - WebSocket Communications](CH10-WebSocket.html)
- [WebSocket example on GitHub](https://github.com/james-priest/node_samples/tree/master/ch10-WebSocket) - A basic WebSocket proof-of-concept app that calls the WebSocket.org echo server and returns a message sent to it.

---

## 33. Web Workers
### Day 33: February 28, 2018 - Wednesday

**Project:** Study for MS 70-480 Cert Exam (Programming in HTML5 with JavaScript & CSS3)

[![9-2](assets/images/sm_chap9-2.jpg)](assets/images/full-size/chap9-2.png)

**Progress:** This lesson covered the use of Web Workers as a non-blocking (async) way of performing work. The worker can send messages back to the spawning task by posting  messages to an event handler specified by the creator (calling script). Messages can be any object that can be serialized.

When messages are posted to and from the web worker, the message object is serialized. This **creates a copy** of the message, so the web worker and the creator never reference the same object.

Web workers also don't have access to the DOM. If something needs to be posted to the DOM then that has to happen in the form of a message sent back to the creator, and the creator must access the DOM as needed.

Here's a quick bullet list of take-away's:

- A web worker provides asynchronous code execution.
- Communication to and from the web worker is accomplished by using the `postMessage()` method.
- The `postMessage()` method accepts a serializable object.
- The web worker and the creator cannot access the same object since a copy is made.
- The web worker does not have access to DOM elements.

**Links:**
- [Web Worker example on GitHub](https://github.com/james-priest/node_samples/tree/master/ch09-WebWorker) - A very basic set of scripts that converts a string to uppercase.
- [Demystifying Web Workers and Service Workers](https://nolanlawson.github.io/cascadia-2016/#) - Awesome slide deck with a big picture overview of Web Workers and Service Workers.
- [Web Workers vs Service Workers in JavaScript](http://tech.ovoenergy.com/web-workers-vs-service-workers/) - Great article with sample code.

---

## 32. jQuery Ajax & Promises
### Day 32: February 27, 2018 - Tuesday

**Project:** Study for MS 70-480 Cert Exam (Programming in HTML5 with JavaScript & CSS3)

[![9-1](assets/images/sm_chap9-1.jpg)](assets/images/full-size/chap9-1.png)

**Progress:** This lesson went into various asynchronous operations using jQuery ajax and jQuery promises. These are still in use as part of the jQuery library but not as modern an implementation as using ES6 Promises with the Fetch API.

Nonetheless, it's still helpful to know these patterns since a huge majority of code-bases are using jQuery's implementation. What was covered is the following:

- $.Deferred() object as a wrapper to the jquery promise() object
- jQuery .pipe() method for serialized(chained) async operations
- $.when() method for parallel async operations
- conditional async operations based on the result of prior async calls for both parallel and chained patterns

**Links:**
- [Asynchronous operations examples on GitHub](https://github.com/james-priest/node_samples/tree/master/ch09-Async) - These are some jQuery $.ajax() $.Deferred object and .promise() method examples
- [Ajax - Async, Callback & Promise](https://medium.com/front-end-hacking/ajax-async-callback-promise-e98f8074ebd7) - Great Medium article on XMLHttpRequest, jQuery Ajax, & Promises

---

## 31. XMLHttpRequest & Ajax
### Day 31: February 26, 2018 - Monday

**Project:** Study for MS 70-480 Cert Exam (Programming in HTML5 with JavaScript & CSS3)

[![8-1](assets/images/sm_chap8-1.jpg)](assets/images/full-size/chap8-1.png)

**Progress:** Covered using Ajax to access Web Services created with node.js. The web services were created to use Representational State Transfer (REST) and are also known as RESTful services.

REST attempts to use standard operations of HTTP by mapping _create_, _retrieve_, _update_, & _delete (CRUD) operations to HTTP methods.

The object that makes this call from the browser DOM is the XMLHttpRequest object. It is either invoked directly, or through one of jQuery's many wrapper methods. The ones I used were the following:

- Async XMLHttpRequest (for old-school backwards compatability)
- $.ajax()
- $.get()
- $.getJSON()
- $.post()

**Links:** [AJAX examples on GitHub](https://github.com/james-priest/node_samples/tree/master/math_service) - These are some XMLHttpRequests() & jQuery $.ajax() methods

---

## 30. ES6 Transpiling & Babel
### Day 30: February 25, 2018 - Sunday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

[![9-5](assets/images/sm_lesson9-5.jpg)](assets/images/full-size/lesson9-5.png)

**Progress:** Completed [ES6 JavaScript Improved](https://www.udacity.com/course/es6-javascript-improved--ud356) Google Udacity course.

This completes the Google Udacity Scholarship challenge! It took 30 days from start to finish and was exactly the push I needed to stay on track with my 100DaysOfCode challenge.

Now I wait until April 17th to see if I'm selected to complete the remainder of the Mobile Web Nanodegree program!

The lessons covered:

1. Transpiling defined
1. babel-cli & babel-preset-es2015
1. package.json & build scripts

My notes on [ES6 JavaScript Improved (4) - Professional Developer-fu](ES6-Professional-Developer-fu.html).

**Links:**
- Course Notes - [Offline First (1) - Introducing the Service Worker](Introducing-the-Service-Worker.html)
- Course Notes - [Offline First (2) - IndexedDB and Caching](IndexedDB-and-Caching.html)
- Course Notes - [ES6 JavaScript Improved (1) - Syntax](ES6-Syntax.html)
- Course Notes - [ES6 JavaScript Improved (2) - Functions](ES6-Functions.html)
- Course Notes - [ES6 JavaScript Improved (2.5) - Classes](ES6-Classes.html)
- Course Notes - [ES6 JavaScript Improved (3) - Built-ins](ES6-Built-ins.html)
- Course Notes - [ES6 JavaScript Improved (3.5) - Built-ins-Pt2](ES6-Built-ins-Pt2.html)
- Course Notes - [ES6 JavaScript Improved (4) - Professional Developer-fu](ES6-Professional-Developer-fu.html).

- [ES6 JavaScript Improved](https://www.udacity.com/course/es6-javascript-improved--ud356) (free 4 week course) on Udacity

---

## 29. ES6 Polyfills
### Day 29: February 24, 2018 - Saturday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

[![9-3](assets/images/sm_lesson9-3.jpg)](assets/images/full-size/lesson9-3.png)

**Progress:** Continued with my [ES6 JavaScript Improved](https://www.udacity.com/course/es6-javascript-improved--ud356) Google Udacity course.

The lessons covered:

1. Overview of browser support for ES6
1. Feature testing
1. Polyfills to patch missing JS features
1. Polyfills for areas other than JavaScript core. Includes the following
  - SVG, Canvas, Accessibility
  - WebStorage (local / session), Web Sockets
  - HTML5 elements & more...

My notes on [ES6 JavaScript Improved (4) - Professional Developer-fu](ES6-Professional-Developer-fu.html).

**Links:**
- Course Notes - [Offline First (1) - Introducing the Service Worker](Introducing-the-Service-Worker.html)
- Course Notes - [Offline First (2) - IndexedDB and Caching](IndexedDB-and-Caching.html)
- Course Notes - [ES6 JavaScript Improved (1) - Syntax](ES6-Syntax.html)
- Course Notes - [ES6 JavaScript Improved (2) - Functions](ES6-Functions.html)
- Course Notes - [ES6 JavaScript Improved (2.5) - Classes](ES6-Classes.html)
- Course Notes - [ES6 JavaScript Improved (3) - Built-ins](ES6-Built-ins.html)
- Course Notes - [ES6 JavaScript Improved (3.5) - Built-ins-Pt2](ES6-Built-ins-Pt2.html)
- Course Notes - [ES6 JavaScript Improved (4) - Professional Developer-fu](ES6-Professional-Developer-fu.html).

- [ES6 JavaScript Improved](https://www.udacity.com/course/es6-javascript-improved--ud356) (free 4 week course) on Udacity

---

## 28. ES6 Promises, Proxies, & Generators
### Day 28: February 23, 2018 - Friday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

```js
// Proxy code
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

**Progress:** Continued with my [ES6 JavaScript Improved](https://www.udacity.com/course/es6-javascript-improved--ud356) Google Udacity course.

The lessons covered:

1. Promises, Successful & Failed requests, Async operations
1. Proxies, handlers, & traps
1. Generators, Iterators, & yield

My notes on [ES6 JavaScript Improved (3.5) - Built-ins-Pt2](ES6-Built-ins-Pt2.html).

**Links:**
- Course Notes - [Offline First (1) - Introducing the Service Worker](Introducing-the-Service-Worker.html)
- Course Notes - [Offline First (2) - IndexedDB and Caching](IndexedDB-and-Caching.html)
- Course Notes - [ES6 JavaScript Improved (1) - Syntax](ES6-Syntax.html)
- Course Notes - [ES6 JavaScript Improved (2) - Functions](ES6-Functions.html)
- Course Notes - [ES6 JavaScript Improved (2.5) - Classes](ES6-Classes.html)
- Course Notes - [ES6 JavaScript Improved (3) - Built-ins](ES6-Built-ins.html)
- Course Notes - [ES6 JavaScript Improved (3.5) - Built-ins-Pt2](ES6-Built-ins-Pt2.html)
- [ES6 JavaScript Improved](https://www.udacity.com/course/es6-javascript-improved--ud356) (free 4 week course) on Udacity

---

## 27. ES6 Maps & WeakMaps
### Day 27: February 22, 2018 - Thursday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

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

**Progress:** Continued with my [ES6 JavaScript Improved](https://www.udacity.com/course/es6-javascript-improved--ud356) Google Udacity course.

The lessons covered:

1. Maps & WeakMaps
1. Iteration & Looping
1. Creating & modifying Map objects

My notes on [ES6 JavaScript Improved (3) - Built-ins](ES6-Built-ins.html).

**Links:**
- Course Notes - [Offline First (1) - Introducing the Service Worker](Introducing-the-Service-Worker.html)
- Course Notes - [Offline First (2) - IndexedDB and Caching](IndexedDB-and-Caching.html)
- Course Notes - [ES6 JavaScript Improved (1) - Syntax](ES6-Syntax.html)
- Course Notes - [ES6 JavaScript Improved (2) - Functions](ES6-Functions.html)
- Course Notes - [ES6 JavaScript Improved (2.5) - Classes](ES6-Classes.html)
- Course Notes - [ES6 JavaScript Improved (3) - Built-ins](ES6-Built-ins.html)
- [ES6 JavaScript Improved](https://www.udacity.com/course/es6-javascript-improved--ud356) (free 4 week course) on Udacity

---

## 26. ES6 Built-ins, Symbols, Sets & WeakSets
### Day 26: February 21, 2018 - Wednesday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

```js
const bowl = {
  [Symbol('apple')]: { color: 'red', weight: 136.078 },
  [Symbol('banana')]: { color: 'yellow', weight: 183.15 },
  [Symbol('orange')]: { color: 'orange', weight: 170.097 },
  [Symbol('banana')]: { color: 'yellow', weight: 176.845 }
};
console.log(bowl);
```

**Progress:** Continued with my [ES6 JavaScript Improved](https://www.udacity.com/course/es6-javascript-improved--ud356) Google Udacity course.

The lessons covered:

1. Symbols
1. Iteration & Iterable protocols
1. Sets & Weak Sets

My notes on [ES6 JavaScript Improved (3) - Built-ins](ES6-Built-ins.html).

**Links:**
- Course Notes - [Offline First (1) - Introducing the Service Worker](Introducing-the-Service-Worker.html)
- Course Notes - [Offline First (2) - IndexedDB and Caching](IndexedDB-and-Caching.html)
- Course Notes - [ES6 JavaScript Improved (1) - Syntax](ES6-Syntax.html)
- Course Notes - [ES6 JavaScript Improved (2) - Functions](ES6-Functions.html)
- Course Notes - [ES6 JavaScript Improved (2.5) - Classes](ES6-Classes.html)
- Course Notes - [ES6 JavaScript Improved (3) - Built-ins](ES6-Built-ins.html)
- [ES6 JavaScript Improved](https://www.udacity.com/course/es6-javascript-improved--ud356) (free 4 week course) on Udacity

---

## 25. ES6 Classes, Subclasses, & Prototypal Inheritance
### Day 25: February 20, 2018 - Tuesday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

[![Class 3](assets/images/sm_lesson6-class3.jpg)](assets/images/full-size/lesson6-class3.png)

**Progress:** Continued with my [ES6 JavaScript Improved](https://www.udacity.com/course/es6-javascript-improved--ud356) Google Udacity course.

The lessons covered:

1. JavaScript prototypal inheritance
1. ES5 vs. ES6 Classes
1. `class`, `super`, and `extends` keywords
1. Working with subclasses

My notes on [ES6 JavaScript Improved (2.5) - Classes](ES6-Classes.html).

**Links:**
- Course Notes - [Offline First (1) - Introducing the Service Worker](Introducing-the-Service-Worker.html)
- Course Notes - [Offline First (2) - IndexedDB and Caching](IndexedDB-and-Caching.html)
- Course Notes - [ES6 JavaScript Improved (1) - Syntax](ES6-Syntax.html)
- Course Notes - [ES6 JavaScript Improved (2) - Functions](ES6-Functions.html)
- Course Notes - [ES6 JavaScript Improved (2.5) - Classes](ES6-Classes.html)
- [ES6 JavaScript Improved](https://www.udacity.com/course/es6-javascript-improved--ud356) (free 4 week course) on Udacity

---

## 24. ES6 'this' Keyword & Default Parameters
### Day 24: February 19, 2018 - Monday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

```js
// object defaults with object destructuring
function buildHouse({floors = 1, color = 'red', walls = 'brick'} = {}) {
    return `Your house has ${floors} floor(s) with ${color} ${walls} walls.`;
}

// tests
console.log(buildHouse());
console.log(buildHouse({}));
console.log(buildHouse({floors: 3, color: 'yellow'}));

// Your house has 1 floor(s) with red brick walls.
// Your house has 1 floor(s) with red brick walls.
// Your house has 3 floor(s) with yellow brick walls.
```

**Progress:** Continued with my [ES6 JavaScript Improved](https://www.udacity.com/course/es6-javascript-improved--ud356) Google Udacity course.

The lessons covered:

1. `this` keyword with standard functions
1. `this` keyword with arrow functions
1. Default function parameters using arrays
1. Default function parameters using objects
1. Array defaults with array destructuring
1. Object defaults with object destructuring

My notes on [ES6 JavaScript Improved (2) - Functions](ES6-Functions.html).

**Links:**
- Course Notes - [Offline First (1) - Introducing the Service Worker](Introducing-the-Service-Worker.html)
- Course Notes - [Offline First (2) - IndexedDB and Caching](IndexedDB-and-Caching.html)
- Course Notes - [ES6 JavaScript Improved (1) - Syntax](ES6-Syntax.html)
- Course Notes - [ES6 JavaScript Improved (2) - Functions](ES6-Functions.html)
- [ES6 JavaScript Improved](https://www.udacity.com/course/es6-javascript-improved--ud356) (free 4 week course) on Udacity

---

## 23. ES6 Arrow Functions
### Day 23: February 18, 2018 - Sunday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

#### Before

```js
// convert to an arrow function
const squares = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10].map(function(square) {
  return square * square;
});

let output = '';
squares.forEach(function(square){
  output += ` ${square}`;
});
console.log(output.trim());
```

#### After

```js
const squares = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10].map(square => square * square);
console.log(...squares);
```

> **Output:** 1 4 9 16 25 36 49 64 81 100

**Progress:** Continued with my [ES6 JavaScript Improved](https://www.udacity.com/course/es6-javascript-improved--ud356) Google Udacity course.

The lessons covered:

1. Spread (`...`) operator
1. (`...`) Rest parameter
1. Arrow functions
1. Syntactic variations of arrow functions
    - Parens / no parens / empty parens / underscore
1. _"Concise body syntax"_  vs. _"block body syntax"_


**Links:**
- [ES6 JavaScript Improved](https://www.udacity.com/course/es6-javascript-improved--ud356) (free 4 week course) on Udacity
- Course Notes - [Offline First (1) - Introducing the Service Worker](Introducing-the-Service-Worker.html)
- Course Notes - [Offline First (2) - IndexedDB and Caching](IndexedDB-and-Caching.html)
- Course Notes - [ES6 JavaScript Improved (1) - Syntax](ES6-Syntax.html)
- Course Notes - [ES6 JavaScript Improved (2) - Functions](ES6-Functions.html)

---

## 22. ES6 Object Literal Shorthand & For..of Loops
### Day 22: February 17, 2018 - Saturday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

```js
// Object Literal shorthand
let type = 'quartz';
let color = 'rose';
let carat = 21.29;

let gemstone = { type, color, carat };

console.log(gemstone);

// for..of loop
const digits = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

for (const digit of digits) {
  console.log(digit);
}
```

**Progress:** Continued with my [ES6 JavaScript Improved](https://www.udacity.com/course/es6-javascript-improved--ud356) Google Udacity course.

The lessons covered:

1. Object literal shorthand
1. Iteration
1. Family of For loops
1. For..of loop

**Links:**
- [ES6 JavaScript Improved](https://www.udacity.com/course/es6-javascript-improved--ud356) (free 4 week course) on Udacity
- Course Notes - [Offline First (1) - Introducing the Service Worker](Introducing-the-Service-Worker.html)
- Course Notes - [Offline First (2) - IndexedDB and Caching](IndexedDB-and-Caching.html)
- Course Notes - [ES6 JavaScript Improved (1) - Syntax](ES6-Syntax.html)

---

## 21. ES6 Template Literals & Destructuring Arrays
### Day 21: February 16, 2018 - Friday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

```js
// Template Literal syntax
var note = `${teacher.name},

  Please excuse ${student.name}.
  He is recovering from the flu.

  Thank you,
  ${student.guardian}`;
```

**Progress:** Continued with my [ES6 JavaScript Improved](https://www.udacity.com/course/es6-javascript-improved--ud356) Google Udacity course.

The lesson covered:

1. `let` and `const` syntax and when to use each
1. Use of Template Literals for true string interpolation
1. Destructuring of arrays & objects with simpler ES6 syntax

You can read more here: [My notes - ES6 JavaScript Improved - Syntax](ES6-Syntax.html).

**Link to Work:**
- [Full Course Notes - ES6 JavaScript Improved - Syntax](ES6-Syntax.html)
- 4-part Udacity course [ES6 JavaScript Improved](https://www.udacity.com/course/es6-javascript-improved--ud356) (free 4 week course)

---

## 20. ES6 JavaScript Improved
### Day 20: February 15, 2018 - Thursday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

[![Syntax 1](assets/images/sm_lesson6-syntax1.jpg)](assets/images/full-size/lesson6-syntax1.png)

**Progress:** Started my new Google Udacity course called [ES6 JavaScript Improved](https://www.udacity.com/course/es6-javascript-improved--ud356).

The course is broken down into the following lessons:

1. **Syntax** - let, const, destructuring, for..of loops
1. **Functions** - arrow functions, `this` keyword, classes & subclasses
1. **Built-ins** - Sets, Maps, WeakSets, & WeakMaps, Promises, generators
1. **Polyfills & transpilers** - This lets you convert from ES6 to ES5

You can read more here: [My notes - ES6 JavaScript Improved - Syntax](ES6-Syntax.html).

**Link to Work:**
- [Full Course Notes - ES6 JavaScript Improved - Syntax](ES6-Syntax.html)
- 4-part Udacity course [ES6 JavaScript Improved](https://www.udacity.com/course/es6-javascript-improved--ud356) (free 4 week course)

---

## 19. Cache Avatars
### Day 19: February 14, 2018 - Wednesday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

[![IDB 34](assets/images/sm_lesson4-idb34.jpg)](assets/images/full-size/lesson4-idb34.png)

**Progress:** The final few sections of this course combined all three of the following:

- Service Workers
- IndexedDB
- Cache Storage with Cache API.

You can read more here: [My notes - IndexedDB and Caching - Cache Avatars](IndexedDB-and-Caching.html#13-caching-avatars).

**Link to Work:**
- [Full Course Notes - IndexedDB and Caching](IndexedDB-and-Caching.html)
- Jake's IDB Promised Library [https://github.com/jakearchibald/idb](https://github.com/jakearchibald/idb)
- 3-part Udacity course [Offline Web Applications by Google](https://www.udacity.com/course/offline-web-applications--ud899) (free 3 week course)

---

## 18. Cache Photos
### Day 18: February 13, 2018 - Tuesday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

[![IDB 31](assets/images/sm_lesson4-idb31.jpg)](assets/images/full-size/lesson4-idb31.png)

**Progress:** This section deals with retrieving requested images from local Cache Storage. If the images do not exists locally then a fetch request is made to the network.

Once the image is retrieved, it is displayed to the screen and and saved to cache for future use.

You can read more here: [My notes - IndexedDB and Caching - Cache Photos](IndexedDB-and-Caching.html#9-cache-photos).

**Link to Work:**
- [Full Course Notes - IndexedDB and Caching](IndexedDB-and-Caching.html)
- Jake's IDB Promised Library [https://github.com/jakearchibald/idb](https://github.com/jakearchibald/idb)
- 3-part Udacity course [Offline Web Applications by Google](https://www.udacity.com/course/offline-web-applications--ud899) (free 3 week course)

---

## 17. Display Data & Clean Database
### Day 17: February 12, 2018 - Monday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

[![IDB 27](assets/images/sm_lesson4-idb27.jpg)](assets/images/full-size/lesson4-idb27.png)

**Progress:** In this section of the course we take the data from the IndexedDB Object Store and write code to display it on the page.

At the same time we create an index and cursor through it to remove any old and stale posts from our database. This makes room for new data that we stream in through web sockets.

You can read more here: [My notes - IndexedDB and Caching - Display IDB Data on Page](IndexedDB-and-Caching.html#7-display-idb-data-on-page).

**Link to Work:**
- [Full Course Notes - IndexedDB and Caching](IndexedDB-and-Caching.html)
- Jake's IDB Promised Library [https://github.com/jakearchibald/idb](https://github.com/jakearchibald/idb)
- 3-part Udacity course [Offline Web Applications by Google](https://www.udacity.com/course/offline-web-applications--ud899) (free 3 week course)

---

## 16. Populate the IDB Database
### Day 16: February 11, 2018 - Sunday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

[![IDB 25](assets/images/sm_lesson4-idb25.jpg)](assets/images/full-size/lesson4-idb25.png)

**Progress:** This section consisted of creating an IDB database (wittr) and then writing data to the IDB object store (wittrs).

Once the database was created and populated an index was also created to sort by date.

You can click the link below to read about the process and see the code required to produce the IDB results.

You can read more here: [My notes - IndexedDB and Caching - IDB Cache & Display Entries](IndexedDB-and-Caching.html#6-writing-idb-cache-data).

**Link to Work:**
- [Full Course Notes - IndexedDB and Caching](IndexedDB-and-Caching.html)
- Jake's IDB Promised Library [https://github.com/jakearchibald/idb](https://github.com/jakearchibald/idb)
- 3-part Udacity course [Offline Web Applications by Google](https://www.udacity.com/course/offline-web-applications--ud899) (free 3 week course)

---

## 15. IDB Cache & Display Entries
### Day 15: February 10, 2018 - Saturday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

[![IDB 20](assets/images/sm_lesson4-idb20.jpg)](assets/images/full-size/lesson4-idb20.png)

**Progress:** This section of the lesson covered the data that will be save to the IndexedDB Object Store as well as the structure of data.

The process of retrieving existing posts from local storage and then using web sockets to update the feed is also discussed.

Lastly, specifics such as unique index and keys for the data are discussed.

You can read more here: [My notes - IndexedDB and Caching - IDB Cache & Display Entries](IndexedDB-and-Caching.html#5-idb-cache--display-entries).

**Link to Work:**
- [Full Course Notes - IndexedDB and Caching](IndexedDB-and-Caching.html)
- Jake's IDB Promised Library [https://github.com/jakearchibald/idb](https://github.com/jakearchibald/idb)
- 3-part Udacity course [Offline Web Applications by Google](https://www.udacity.com/course/offline-web-applications--ud899) (free 3 week course)

---

## 14. IDB Cursors and Indexes
### Day 14: February 9, 2018 - Friday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

[![IDB 17](assets/images/sm_lesson4-idb17.jpg)](assets/images/full-size/lesson4-idb17.png)

**Progress:** This is the third and final deep dive into IndexedDB fundamentals. Here we cover using cursors and the syntax required to wrap these in Promises rather than nested callback hell.  This includes:

- openCursor()
- cursor.value
- cursor.continue()
- cursor.advance()
- cursor.update()
- cursor.delete()

You can read more here: [My notes - IndexedDB and Caching - IDB Cursors and Indexes](IndexedDB-and-Caching.html#4-idb-cursors-and-indexes).

**Link to Work:**
- [Full Course Notes - IndexedDB and Caching](IndexedDB-and-Caching.html)
- Jake's IDB Promised Library [https://github.com/jakearchibald/idb](https://github.com/jakearchibald/idb)
- 3-part Udacity course [Offline Web Applications by Google](https://www.udacity.com/course/offline-web-applications--ud899) (free 3 week course)

---

## 13. Diving Deeper into IDB
### Day 13: February 8, 2018 - Thursday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

[![IDB 10](assets/images/sm_lesson4-idb10.jpg)](assets/images/full-size/lesson4-idb10.png)

**Progress:** This section got into deeper into the IDB API. Some of the items covered were:

- Creating, updating, and accessing multiple object stores
- Database versioning with multiple instances
- Transactions with multiple operations
- Creation and use of indexes
- Filtering data on index

Lots of sample code and screen shots for reference.

You can read more here: [My notes - IndexedDB and Caching - Diving Deeper with IDB](IndexedDB-and-Caching.html#3-diving-deeper-with-idb).

**Link to Work:**
- [Full Course Notes - IndexedDB and Caching](IndexedDB-and-Caching.html)
- Jake's IDB Promised Library [https://github.com/jakearchibald/idb](https://github.com/jakearchibald/idb)
- 3-part Udacity course [Offline Web Applications by Google](https://www.udacity.com/course/offline-web-applications--ud899) (free 3 week course)

---

## 12. Getting Started with IDB
### Day 12: February 7, 2018 - Wednesday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

[![IDB 8](assets/images/sm_lesson4-idb8.jpg)](assets/images/full-size/lesson4-idb8.png)

**Progress:** Here we got into the code behind IndexedDB. We quickly covered each of the following:

- Opening a database
- Creating an object store
- Writing data to the object store
- Reading data
- Using transactions
- Inspecting IDB in DevTools

You can read more here: [My notes - IndexedDB and Caching](IndexedDB-and-Caching.html).

**Link to Work:**
- [Full Course Notes - IndexedDB and Caching](IndexedDB-and-Caching.html)
- Jake's IDB Promised Library [https://github.com/jakearchibald/idb](https://github.com/jakearchibald/idb)
- 3-part Udacity course [Offline Web Applications by Google](https://www.udacity.com/course/offline-web-applications--ud899) (free 3 week course)

---

## 11. IndexedDB Promised Library
### Day 11: February 6, 2018 - Tuesday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

[![IDB 7](assets/images/sm_lesson4-idb7.jpg)](assets/images/full-size/lesson4-idb7.png)

**Progress:** Learned about IndexedDB and how it can be used by all the major browsers to provide database capabilities. This is a NoSQL rather than relational database and is perfectly suited to persist data related to a site.

This lesson also covers some of the deficiencies inherent in the asynchronous implementations of IndexedDB. It was created before Promises and therefore uses a messy callback architecture.

We look at using a tiny wrapper library written by Jake Archibald which allows us to use Promises rather than events.

You can read more here: [My notes - IndexedDB and Caching](IndexedDB-and-Caching.html).

**Link to Work:**
- [Full Course Notes - IndexedDB and Caching](IndexedDB-and-Caching.html)
- Jake's IDB Promised Library [https://github.com/jakearchibald/idb](https://github.com/jakearchibald/idb)
- 3-part Udacity course [Offline Web Applications by Google](https://www.udacity.com/course/offline-web-applications--ud899) (free 3 week course)

---

## 10. Triggering a Service Worker Update
### Day 10: February 5, 2018 - Monday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

[![service worker 19](assets/images/sm_lesson3-service-worker19.jpg)](assets/images/full-size/lesson3-service-worker19.png)

**Progress:** Learned how to trigger a cache and Service Worker update for versioned web content. This provides the user with a notification and creates a new cache store instance separate from the existing cache store.

The versioning of caches stores ensures that the current Service Worker does not experience any interruptions servicing it's pages when new content arrives.

The user is given the option of updating immediately or dismissing the notification and updating with the normal Service Worker lifecycle. This occurs when the old Service Worker is released.

You can read more here: [My notes - Triggering an Update](Introducing-the-Service-Worker.html#24-triggering-an-update).

**Link to Work:**
- [Full Course Notes - Introducing the Service Worker](Introducing-the-Service-Worker.html)
- 3-part Udacity course [Offline Web Applications by Google](https://www.udacity.com/course/offline-web-applications--ud899) (free 3 week course)

---

## 9. Update Notification with Service Workers
### Day 9: February 4, 2018 - Sunday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

[![service worker 18](assets/images/sm_lesson3-service-worker18.jpg)](assets/images/full-size/lesson3-service-worker18.png)

**Progress:** Learned how to provide the user with an update notification when new content is available through a new Service Worker instance.

When a new Service Worker instance is installed it remains in a 'waiting' state until the current Service Worker is done servicing all pages in its scope and is released. This usually requires navigating off site and back again.

These changes alert the user to new content so they may update with a button click.

You can read more here: [My notes - Adding UX to the Update Process](Introducing-the-Service-Worker.html#22-adding-ux-to-the-update-process).

**Link to Work:**
- [Full Course Notes - Introducing the Service Worker](Introducing-the-Service-Worker.html)
- 3-part Udacity course [Offline Web Applications by Google](https://www.udacity.com/course/offline-web-applications--ud899) (free 3 week course)

---

## 8. Updating Static Cache
### Day 8: February 3, 2018 - Saturday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

[![service worker 15](assets/images/sm_lesson3-service-worker15.jpg)](assets/images/full-size/lesson3-service-worker15.png)

**Progress:** Learned how to update static cache for a site by creating versioned cache stores.

By changing the name of a cache store from say 'my-app-v1' to 'my-app-v2' we are causing the service worker to spin up a new instance. The new service worker instance gets installed but not activated until the old service worker is released.

We create a separate cache store because we don't want to disrupt the cache that's already being used by the old service worker and the pages it controls.

Once the old service worker is released, we delete the old cache store so the next page load gets the latest resources from the new cache.

You can read more here: [My notes - Updating the Static Cache](Introducing-the-Service-Worker.html#19-updating-the-static-cache).

**Link to Work:**
- [Full Course Notes - Introducing the Service Worker](Introducing-the-Service-Worker.html)
- 3-part Udacity course [Offline Web Applications by Google](https://www.udacity.com/course/offline-web-applications--ud899) (free 3 week course)

---

## 7. Cache API
### Day 7: February 2, 2018 - Friday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

[![service worker](assets/images/sm_lesson3-service-worker13.jpg)](assets/images/full-size/lesson3-service-worker13.png)

**Progress:** Learned the basics of the [Cache API](https://developer.mozilla.org/en-US/docs/Web/API/Cache) for storing offline versions of a site. This includes the use of:

- [CacheStorage.open()](https://developer.mozilla.org/en-US/docs/Web/API/CacheStorage/open)<br>
  Returns a Promise that resolves to the Cache object matching the cacheName (a new cache is created if it doesn't already exist.)
- [Cache.put(request, response)](https://developer.mozilla.org/en-US/docs/Web/API/Cache/put)<br>
  Takes both a request and its response and adds it to the given cache.
- [Cache.add(request)](https://developer.mozilla.org/en-US/docs/Web/API/Cache/add)<br>
  Takes a URL, retrieves it and adds the resulting response object to the given cache. This is functionally equivalent to calling fetch(), then using Cache.put() to add the results to the cache.
- [Cache.match(request, options)](https://developer.mozilla.org/en-US/docs/Web/API/Cache/match)<br>
  Returns a Promise that resolves to the response associated with the first matching request in the Cache object.
- [Cache.addAll(requests)](https://developer.mozilla.org/en-US/docs/Web/API/Cache/addAll)<br>
  Takes an array of URLs, retrieves them, and adds the resulting response objects to the given cache.
- [Cache.matchAll(request, options)](https://developer.mozilla.org/en-US/docs/Web/API/Cache/matchAll)<br>
  Returns a Promise that resolves to an array of all matching requests in the Cache object.

Also learned about the [install](https://developer.mozilla.org/en-US/docs/Web/API/InstallEvent) and [activate](https://developer.mozilla.org/en-US/docs/Web/API/ExtendableEvent/waitUntil) events of a Service Worker.

Full examples can be found in [my notes under - Caching and Serving Assets](Introducing-the-Service-Worker.html#16-caching-and-serving-assets).

**Link to Work:**
- [Introducing the Service Worker - Notes](Introducing-the-Service-Worker.html)
- 3-part Udacity course [Offline Web Applications by Google](https://www.udacity.com/course/offline-web-applications--ud899) (free 3 week course)

---

## 6. Hijacking Requests
### Day 6: February 1, 2018 - Thursday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

[![dev tools](assets/images/sm_hijacking-requests1.jpg)](assets/images/full-size/hijacking-requests1.png)

**Progress:** Learned about the following.
1. How to listen for and capture `fetch` events
1. How to use the `fetchEvent.respondWith()` method
1. Using `Fetch API` as a better and modern alternative to XMLHttpRequest.

Here's an example of this kind of event handling.

```js
self.addEventListener('fetch', function(event) {
  // TODO: only respond to requests with a url ending in ".jpg"
  if ( event.request.url.endsWith( '.jpg' ) ) {
    event.respondWith(
      fetch( '/imgs/dr-evil.gif' )
    );
  }
});
```

Full examples can be found in [my notes](Introducing-the-Service-Worker.html).

**Link to Work:**
- [Introducing the Service Worker - Notes](Introducing-the-Service-Worker.html)
- 3-part Udacity course [Offline Web Applications by Google](https://www.udacity.com/course/offline-web-applications--ud899) (free 3 week course)

---

## 5. Service Worker Dev Tools
### Day 5: January,31 2018 - Wednesday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

[![dev tools](assets/images/sm_chrome-dev-tools1.jpg)](assets/images/full-size/chrome-dev-tools1.png)

**Progress:** Learned about [Chrome Canary](https://www.google.com/chrome/browser/canary.html), the nightly build of Chrome with bleeding edge features. It can be run along side **Chrome Stable** but can often break as well. It receives a new feature push almost daily.

Chrome Stable has the Service Worker features already baked in and might be a better choice to test with since it is less likely to crash. That is what I have pictured above.

**Link to Work:**
- [Introducing the Service Worker - Notes](Introducing-the-Service-Worker.html)
- 3-part Udacity course [Offline Web Applications by Google](https://www.udacity.com/course/offline-web-applications--ud899) (free 3 week course)
- [Chrome Canary](https://www.google.com/chrome/browser/canary.html) - Nightly build of latest Chrome bits.

---

## 4. The Service Worker Lifecycle
### Day 4: January,30 2018 - Tuesday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

[![service worker](assets/images/sm_lesson3-service-worker5.jpg)](assets/images/full-size/lesson3-service-worker5.png)

**Progress:** Learned about the Service Worker Lifecycle.

This is part of a larger, 3-part Udacity series called [Offline Web Applications by Google](https://www.udacity.com/course/offline-web-applications--ud899). It contains the following lessons and is **FREE**!

1. The Benefits of Offline First
1. Introducing the Service Worker
1. IndexedDB and Caching

**Link to Work:**
- [Introducing the Service Worker - Notes](Introducing-the-Service-Worker.html)
- 3-part Udacity course [Offline Web Applications by Google](https://www.udacity.com/course/offline-web-applications--ud899) (free 3 week course)

---

## 3. An Overview of the Service Worker
### Day 3: January,29 2018 - Monday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

[![service worker](assets/images/sm_lesson3-service-worker1.jpg)](assets/images/full-size/lesson3-service-worker1.png)

**Progress:** Learned what the **Service Worker** is:
- a JavaScript file that sits between you and network requests.
- a type of **Web Worker** meaning it runs separately from your page.
- a process that is invisible to the user and that can't access the DOM.

But, it does control pages by intercepting requests as the browser makes them.

To see full notes along with screen captures click the link below.

**Link to Work:** [My notes on: Introducing the Service Worker](Introducing-the-Service-Worker.html)

---

## 2. The Benefits of Offline First
### Day 2: January,28 2018 - Sunday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

**Progress:** Lesson 2: The Benefits of Offline First - Jake Archibald

The _Benefits of Offline First_ course was broken down into 13 segments. It discussed the use of **HTTP Cache** and laid out a new paradigm which loads content from cache first rather than relying on network connectivity to determine if content gets displayed.

This solves for all three of the following use case scenarios:
1. Great connectivity
1. Poor connectivity
1. Offline

_Offline First_ delivers the page (header and/or content) from cache FIRST, and THEN attempts to fetch content from the network.

Lastly, it introduces the **Service Worker**.

[![service worker](assets/images/sm_lesson2-service-worker.jpg)](assets/images/full-size/lesson2-service-worker.png)

It's billed as a new browser feature and a total game changer- the greatest paradigm shift since asynchronous operations and one that allows **you to control the network rather than the network control you**.

---

## 1. Grow With Google - Mobile Web - Getting Started
### Day 1: January,27 2018 - Saturday

**Project:** [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

**Progress:** Lesson 1: Welcome video.

Welcome video got us set up on the discussion forums, Slack, and basically gave a Scholarship Overview.

Looks like the program is broken up into 10 courses.  These are:
1. Welcome! Important Details on your Scholarship
1. The Benefits of Offline First
1. Introducing the Service Worker
1. IndexedDB and Caching
1. Next Up
1. JavaScript Syntax Updates
1. JavaScript ES6 Functions
1. JavaScript Built-ins
1. Professional Developer-fu - polyfills & transpiling ES6
1. Challenge Course Wrap Up

Looks like some nice coverage of things I want to dive into deeper!

---

## Round 2 Preflight Checklist
### Day 0: January 26, 2018 - Friday

**Project:**
- Create 100 Days of Code Round 2 Log
- [Grow with Google Scholarship Challenge](https://www.udacity.com/grow-with-google): Mobile Web track

**Progress:** Today was about getting ready to start Round 2!  I have created a new R2 repo and log on GitHub and have gone through the Welcome video for my Grow with [Google Scholarship: Mobile Web](https://www.udacity.com/course/mobile-web-specialist-nanodegree--nd024) course.

I am excited and ready to jump in with both feet!

**Link to work:**
- [Google/Udacity Mobile Web Specialist](https://www.udacity.com/course/mobile-web-specialist-nanodegree--nd024)
- [Google Web and Android Scholarship Program](https://www.udacity.com/google-scholarships)