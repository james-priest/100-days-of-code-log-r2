---
title: Introducing the Service Worker
description: Grow with Google Scholarship Challenge - Mobile Web Track
---
<!-- markdownlint-disable MD022 MD024 MD032 -->
# Introducing the Service Worker
Notes from _Introducing the Service Worker_ by Jake Archibald. This class is part of the Udacity course [Offline Web Applications by Google](https://www.udacity.com/course/offline-web-applications--ud899)

This is an Intermediate skill level course which takes approximately 3 weeks to complete and is offered for **FREE**!

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

## 2. Quiz: Scoping Quiz
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

## 4. Quiz: Registering a Service Worker

```javascript
IndexController.prototype._registerServiceWorker = function() {
    if ( !navigator.serviceWorker ) return;

    navigator.serviceWorker.register( '/sw.js' ).then( function() {
        console.log( 'Registration worked!' );
    } ).catch( function() {
        console.log( 'Registration failed!' );
    } );
};
```

## 5. The Service Worker Lifecycle
We have already experienced an oddity of the Service Worker lifecycle. When we first created the Service Worker, it took two page refreshes to see the result. In addition, when we changed the Service Worker the browser didn't seem to pick up that change. The lifecycle of the Service Worker is one of the most complex parts; once you get this bit the rest is easy!

### The Lifecycle
Just to recap, we had a window with the Wittr app open already, then we added new code to register a Service Worker, then we hit refresh in the browser.

[![screenshot 3](assets/images/sm_lesson3-service-worker3.jpg)](assets/images/full-size/lesson3-service-worker3.png)

Hitting refresh the first time spawned a new window client. Then the request went off to the network. We received a response back, and the old window client went away. It might not seem like there's an overlap between the old page and the new page when you hit refresh, but there is! For example, if the response came back indicating that the browser should save the resource to disk via a download dialogue then the old window would've stayed around. But in this case, the response was a page so we got rid of the old one.

[![screenshot 4](assets/images/sm_lesson3-service-worker4.jpg)](assets/images/full-size/lesson3-service-worker4.png)

From our page, requests went out for our CSS, images, but also our javascript which registered the Service Worker. **We didn't see requests log from this page, because the Service Worker only takes control of pages when they're loaded;** and this page was loaded before the Service Worker existed.That means, **any additional requests this page makes will bypass the Service Worker**.

[![screenshot 5](assets/images/sm_lesson3-service-worker5.jpg)](assets/images/full-size/lesson3-service-worker5.png)
But then we refreshed the page once more, creating a new window client. And because our Service Worker was up and running, it took control of the page. Therefore, the request went to the Service Worker, as did all of the sub-resources.

So that explains why it took two refreshes to see logged requests, but if you make a change to the Service Worker and refresh the page nothing happens. How can we get the updated Service Worker recognized when the page is reloaded?

[![screenshot 6](assets/images/sm_lesson3-service-worker6.jpg)](assets/images/full-size/lesson3-service-worker6.png)

If a page loads via a Service Worker, it will check for an update to the Service Worker in the background. If it finds it has changed, the changed Service Worker becomes the next version. **But the next version doesn't take control yet, it waits. It won't take over until all pages using the current version are gone.** This ensures there is only one version of your site running at a given time.

[![screenshot 7](assets/images/sm_lesson3-service-worker7.jpg)](assets/images/full-size/lesson3-service-worker7.png)

Unfortunately, a refresh doesn't let the new version of the Service Worker take over. This is due to the overlap between window clients, which means there isn't actually a moment when the current active Service Worker is not in use. **For that to happen, the page needs to close or navigate to a page that isn't controlled by the Service Worker. When it does that, the new Service Worker takes over and future page loads will go to the new one.**

[![screenshot 8](assets/images/sm_lesson3-service-worker8.jpg)](assets/images/full-size/lesson3-service-worker8.png)

The update process for Service Workers may sound complicated, but if you think about it this is actually the same process that normal software uses. Take Chrome for example: When there is an update to the browser, it will be downloaded in the background, but will not take affect until the browser is closed and reopened again.

### Cache Time
When the browser refetches the Service Worker, looking for updates, it will go through the browser cache - as pretty much all requests do. Because of this, it is recommended keeping the cache time on your Service Worker short. In fact, a cache time of 0 is recommended.

As a safety precaution, if you set the Service Worker script to cache for more than one day the browser will ignore that and set the cache to 24 hours.

That doesn't mean your Service Worker will stop working after 24 hours, it just means that update checks will bypass the browser cache if the Service Worker it has is over a day old.

## 6. Quiz: Enable Service Worker Dev Tools
Do this by  downloading and running [Chrome Canary](https://www.google.com/chrome/browser/canary.html).

Chrome Canary is the most current nightly build of Chrome with the newest features available. It is designed for developers and early adopters and can be run side-by-side with **Chrome Stable**.

The current version of Chrome Stable already has the necessary Dev Tools if you don't want to download Canary.

## 7. Quiz: Service Worker Dev Tools
Verify new Service Worker installs and goes into a "waiting  to active" state.

[![dev tools](assets/images/sm_chrome-dev-tools1.jpg)](assets/images/full-size/chrome-dev-tools1.png)

1. Navigate to Application tab in DevTools.
1. Make a change to sw.js.
1. Verify that the new Service Worker has installed and is "waiting to activate".

## 8. Quiz: Service Worker Dev Tools 2
Activate the new Service Worker.

1. Navigate to a new website.
1. Navigate back.
1. Ensure the new Service Worker is active and that there is no Service Worker "waiting to activate".

## 9. Service Worker DevTools Continued
Reloading the page while holding `SHIFT` reloads the page but bypasses the Service Worker. This is part of the Service Worker spec, so it should work in any browser that implements the spec. This is handy for two reasons:

1. It's a quick way to test changes that are unrelated to the Service Worker, such as minor CSS changes.
1. Because the tab is no longer controlled by the Service Worker, it lets the waiting Service Worker take over.

If you refresh normally now, the request will go through the new Service Worker.

This way of bypassing the Service Worker and then refreshing is easier than navigating away from the origin or closing the tab, but Chrome's developer tools offer an even easier way:

In the Application tab of Chrome developer tools, there is an option called **Update on reload**. This changes the Service Worker lifecycle to be developer friendly. In this mode, when you hit refresh, rather than refreshing the page it fetches a Service Worker and treats it as a new version whether it has changed or not and lets it become active immediately. With this option active, you do not have to hold SHIFT and refresh or navigate away from the page.

## 10. Hijacking Requests
So far, we have:

- [X] Setup the Service Worker
- [X] Learned the Service Worker lifecycle
- [X] Explored Chrome Developer Tools

But we haven't really used the Service Worker to do anything useful yet. We have seen requests go from the page, through the Service Worker fetch event, and onto the network through the HTTP Cache.

[![screenshot 9](assets/images/sm_lesson3-service-worker9.jpg)](assets/images/full-size/lesson3-service-worker9.png)

Now, we're going to catch the request as it hits the Service Worker and respond ourselves so nothing goes to the network. **This is an important step in going offline first**.

```javascript
self.addEventListener('fetch', function(evetn) {
    event.respondWith(..);
});
```

The `respondWith` method takes a Response object or a Promise that resolves with a Response. One way to create a Response is to create a new Response instance:

```javascript
self.addEventListener('fetch', function(event) {
    event.respondWith(
        new Response('Hello <b>World</b>!')
    )
});
```

No matter what URL is entered into the URL bar, I get the same response because I'm intercepting **ALL** fetches.

[![screenshot 10](assets/images/sm_lesson3-service-worker10.jpg)](assets/images/full-size/lesson3-service-worker10.png)

Looks the html is being output ast text. That's because the default content-type is `text/plain`. Fortunately, we can set headers as part of the response.

```javascript
self.addEventListener('fetch', function(event) {
    event.respondWith(
        new Response('Hello <b>World</b>!', {
            headers: { 'foo': 'bar', 'Content-Type': 'text/html' }
        })
    )
});
```

Refresh the page and look at the _Network_ tab in Chrome developer tools, take a look at the _Response Headers_ and you will see that `foo: bar` and `Content-Type: text/html` was returned as part of the _Response Headers_.

[![screenshot 11](assets/images/sm_lesson3-service-worker11.jpg)](assets/images/full-size/lesson3-service-worker11.png)

## 11. Quiz: HijackingRequests 1 Quiz
In the Service Worker script file ('public/js/sw/index.js'), alter the Service Worker so it responds with some HTML. It can be whatever HTML you want as long as it includes the class name, 'a-winner-is-me'.

Make sure the _Update on reload_ option is selected in the Chrome developer tools on the _Application_ tab so you can see your changes to the Service Worker upon page refresh.

Set `'Content-Type': 'text/html'` in the headers object.

```javascript
self.addEventListener('fetch', function(event) {
    event.respondWith(
        new Response('Hello <b class="a-winner-is-me">Winner!</b>', {
            headers: {
                'Content-Type': 'text/html'
            }
        })
    );
});
```

## 12. Hijacking Requests 2
Now that we know how to hijack a request and respond with basic HTML, let's do something cooler...

Let's go to the network for the Response, but not for the thing that was requested. There is an API to achieve this: fetch.

You might be thinking: "Isn't this what XMLHttpRequest is for?" No, just... no! Much of the XHR API is 15 years old! Even from the outset, it wasn't particularly well thought out.

As an example, here's the code to fetch some JSON from the URL /foo:

```javascript
// Nope. This is Waaaay old school!
var client = new XMLHttpRequest();

client.addEventListener('load', function() {
    console.log(client.response);
});

client.addEventListener('error', function() {
    console.log('It failed');
});

client.responseType = 'json';
client.open('GET', '/foo');
client.send();
```

Everything just feels like it is in the wrong order. The URL is at the bottom, you have to open before you send for some reason, it makes you declare how the response is read before you make the request, and it doesn't support lower-level things like streams. But worst of all the event system gets you into 'callback hell.'

Here's the fetch code for the same operation:

```javascript
// Yup.
fetch('/foo').then(function(response) {
    return response.json();
}).then(function(data) {
    console.log(data);
}).catch(function() {
    console.log('It failed');
});
```

fetch returns a Promise that resolves to the Response. Then we can read the Response as JSON, and then do something with the results. We can catch errors from either the request, or reading the Response. DONE!

As it turns out, back in our Service Worker, `event.respondWith()` takes either a Response or a Promise that resolves to a Response. Since fetch returns a Promise that resolves to a Response, they compose together really well.

Let's respond with a fetch for a .gif file:

```javascript
self.addEventListener('fetch', function(event) {
    event.respondWith(
        fetch('/imgs/dr-evil.gif')
    )
});
```

We've just served up different content using the network!

The Fetch API performs a normal browser fetch, so the results may come from the cache. That is a benefit in this case as we want the .gif to cache as usual.

## 13. Quiz: Hijacking Requests 2 Quiz
Take a look at the code below. As you can see, your task is to only respond with a .gif if the request URL ends with .jpg. How you determine that is up to you, but remember that event.request gives you information about the request.

```javascript
self.addEventListener('fetch', function(event) {
  // TODO: only respond to requests with a url ending in ".jpg"
  
});
```

### Solution

```javascript
self.addEventListener('fetch', function(event) {
  // TODO: only respond to requests with a url ending in ".jpg"
  if ( event.request.url.endsWith( '.jpg' ) ) {
    event.respondWith(
      fetch( '/imgs/dr-evil.gif' )
    );
  }
});
```

We've already seen `event.request`. But what other properties does it have? One way to find out is to go to Google and search for MDN request.

MDN is a great place for documentation and in there there's a result about the _Fetch API_. In there it tells me that `request.url` is the URL of the request. Kind of obvious now we see it.

Alternatively, I could have added a `console.log()` and logged out event.request, as we were before, and then refresh the page. But because the console is cleared when the page navigates, we're losing the log for the page request. If I click 'preserve the log' in Dev Tools and refresh again, there it is. And inside the request object there are loads of details in there,one of which is the URL, and it's a string.

So with this knowledge back in the code I can use an if statement. So `respondWith()` is only called if the URL ends with .jpg. `endsWith()` is a relatively new string method, but it's really useful. Since service worker is only run in modern browsers, we can make use of some of the more modern JavaScript features. Back in the browser with force update enabled, I hit refresh and the page loads as normal, but all the images have been intercepted. So now we're handling requests dynamically depending on URL.

## 14. Hijacking Request 3
We've started handling requests dynamically depending on the URL, but there's a lot more we can do here. In the real world, we need to be a bit more dynamic than this.

The page can send a request, which we intercept and then send to the network. But rather than just sending a `Response` back, we can look at it and then do something else. For example, let's respond with a network `fetch()` for the request just as the browser would do. The fetch method will take a full request object as well as a URL. `fetch()` returns a `Promise`; with Promises you can attach a `.then` callback to get the results if the operation was successful. Whatever we return in this callback becomes the eventual value for the `Promise`.

```js
self.addEventListener('fetch', function(event) {
  event.respondWith(
    fetch( event.request ).then( function( response ) {
      if ( response.status === 404 ) {
        return new Response( 'Whoops, not found' );
      }
      return response;
    }).catch( function( error ) {
      return new Response( 'Uh oh, that totally failed:', error );
    })
  );
});
```

So we can look at the `Response` ourselves and if the `response.status` is 404 (not found) then we can respond with our own message. Otherwise, we return the Response we received.

`.catch` is similar to `.then`, but `.then` is for success and `.catch` is for failure. `fetch` will fail if can't make a connection to the server at all, which includes offline. When that happens, we can respond with our own message.

Now if we go to a page that doesn't exist we get the custom message for 404 errors. And if you take the server down and go offline, you get a custom message for that too!

We can create complex rules for requests, trying to get responses from multiple sources and reacting to the results. You can do this on a request by request basis using JavaScript. You can even go to the network and if that fails, get something else from the network.

## 15 Quiz: Hijacking Requests 3 Quiz

What if you wanted to serve a gif instead of a message for a 404?

```js
self.addEventListener('fetch', function(event) {
  event.respondWith(
    fetch(event.request).then(function(response) {
      if (response.status === 404) {
        // TODO: instead, respond with the gif at
        // /imgs/dr-evil.gif
        // using a network request
        return new Response("Whoops, not found");
      }
      return response;
    }).catch(function() {
      return new Response("Uh oh, that totally failed!");
    })
  );
});
```

### Solution
Over in the code, now if you return a promise within a promise, it passes the eventual value to the outer promise. So, rather than return a response I'm going to return a fetch for the gif's URL and that's it.

```js
self.addEventListener('fetch', function(event) {
  event.respondWith(
    fetch(event.request).then(function(response) {
      if (response.status === 404) {
        // TODO: respond with /imgs/dr-evil.gif using a network request
        return fetch( '/imgs/dr-evil.gif' );
      }
      return response;
    }).catch(function() {
      return new Response("Uh oh, that totally failed!");
    })
  );
});
```