---
title: Mobile Web Track
description: Grow with Google Scholarship Challenge
---
<!-- markdownlint-disable MD022 MD032 -->
# Lesson 3: Introducing the Service Worker
## 1. An Overview of the Service Worker

The **Service Worker** is:
- a JavaScript file that sits between you and network requests.
- a type of **Web Worker** meaning it runs separately from your page
- It's invisible to the user
- It can't access the DOM

But, it does control pages by intercepting requests as the browser makes them.

[![service worker](assets/images/sm_lesson3-service-worker1.jpg)](assets/images/full-size/lesson3-service-worker1.png)

You register for a service worker like this (giving the location of you service worker script).

```javascript
navigator.serviceWorker.register('/sw.js');
```

It returns a **Promise** so you get callbacks for success and failure.

```javascript
navigator.serviceWorker.register('/sw.js').then(function(reg) {
    console.log('Yay!');
}).catch(function(err) {
    console.log('Boo!');
});
```

If we provide a scope, the service worker will control a page at that level and deeper.

```javascript
navigator.serviceWorker.register('/sw.js', {
    scope: '/my-app/'
});
/*
/my-app/                yes
/my-app/hello/world/    yes
/                       no
/another-app            no
/my-app                 no (does not have the trailing slash)
*/
```

We can have multiple service workers with multiple scopes which is really handy for things like GitHub pages where multiple projects share the same origin. Scopes let you have a different service worker for each project.
- https://jakearchibald.gitub.io/svgomg/
- https://jakearchibald.gitub.io/trained-to-thrill/
- https://jakearchibald.gitub.io/isserviceworkerready/

Default scope is determined by the location of the service worker script. It's basically the path the script sits in.

| SW URL | Default scope |
| --- | --- |
| /foo/sw.js | /foo/ |
| /foo/bar/sw.js | /foo/bar/ |
| /sw.js | / |

Usually, you don't need to set the scope. Just put the service worker in the right place.

What happens in the service worker? Well, we listen for particular events.

```javascript
self.addEventListener('install', function(event) {
    // ...
});

self.addEventListener('activate', function(event) {
    // ...
});

self.addEventListener('fetch', function(event) {
    // ...
});

```

In order to make sure the browser supports serviceWorker just wrap the registration in a simple feature detect.

```javascript
if (navigator.serviceWorker) {
    navigator.serviceWorker.register('/sw.js');
}
```

## 2. Scoping Quiz
Given this registration code, which page URLs wll this service worker control?

```javascript
navigator.serviceWorker.register('/sw.js', {scope: '/foo/'});
```

- [ ] /
- [ ] /sw.js
- [ ] /foo
- [ ] /foo.html
- [x] /foo/
- [x] /foo/bar/index.html
- [x] /foo/bar

## 3. Adding a Service Worker To the Project
As mentioned before, the service worker receives events.

Let's add a `fetch` listener for one of these.
sw.js

```javascript
self.addEventListener( 'fetch', function() {
    console.log(event.request);
} );
```

This code inspects the request event.

When the user navigates to a page within your service worker's scope, the service worker controls it. The network request for its html goes to the service worker and triggers a fetch event.

[![service worker](assets/images/sm_lesson2-service-worker.jpg)](assets/images/full-size/lesson2-service-worker.png)

But not only that, you also get a `fetch` event for every request triggered by that page - css, javascript, images.  You get a _fetch_ request for each - **even if there are requests to another origin**.

[![service worker](assets/images/sm_lesson3-service-worker2.jpg)](assets/images/full-size/lesson3-service-worker2.png)