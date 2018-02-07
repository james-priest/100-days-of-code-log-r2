<!-- markdownlint-disable MD022 MD032 -->
# James Priest

## 100 Days Of Code Log R2

**Commitment:** ***I will code daily for the next 100 days.***

This is part of Alexander Kallaway's [100DaysOfCode](https://github.com/Kallaway/100-days-of-code "the official repo") challenge. More details about the challenge can be found here: [100daysofcode.com](http://100daysofcode.com/ "100daysofcode.com").

|  Start Date   | End Date     |
| ------------- | ------------ |
| January 28, 2018 | --- |

## Goals

- [ ] Code daily
- [ ] Complete the Intermediate Mobile Web track of the [#GoogleUdacityScholars](https://twitter.com/search?q=%23GoogleUdacityScholars&src=tyah) program.
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