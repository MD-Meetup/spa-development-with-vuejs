# Single Page Application Development with Vue.js
> Koen Hoeijmakers, MD-Meetup 2017-12-08

## What is SPA, and why should i use it?
The world of web development is quickly shifting into a new era, more and more traffic is mobile,
and most sites will be developed "mobile first", yet we would still use our ancient techniques.

Of course older techniques are not bad by default, as MVC is still really valid for creating vast applications,
yet if you want to increase the user friendliness and application flow while also decreasing the amount
of bandwidth used, SPA might be your way to go.

## Pros and Cons of SPA
SPA development brings some Pros and Cons in contrary to MPA development.

### Pros
- Better UX and more control over UX.
    - You really get to choose what happens when a new "page" is being loaded.
- Lighter request load.
    - Requests don't have to render a shit-ton on html, therefore being lighter.
- Less server side load.
    - The API will only have to deal with incoming data requests, same reason as lighter request load.
- Ability to use existing API's.
    - If you're gonna have to build an app (or expect to build one in the future), the API will be shared and this eliminates a lot of work.

### Cons
- Tricky SEO implementation.
    - SEO is rather tricky as bots don't wait for the whole content load.
- Memory leaks.
    - It's not hard to create memory leaks in javascript, thus not testing properly will probably result in a memory leak of some sorts,
      Especially if the user is on the page for a long time (think of games, sales environment, etc.).

## Our SPA
Our SPA will always consist of 3 base packages, these are:

1. Vue.js (obviously).
2. VueRouter, this will handle our routes.
3. VueX (optional, but i'd say you always want to use it).

### Vue.js
Vue.js is a FAFFF (fancy as fuck front-end framework) that is mostly used to handle the view layer of your application,
but has proven to be a very powerful tool for SPA development.

### VueRouter
VueRouter is the official routing 

## Problems we've encountered

### API Routing
How are you going to tackle routing, we thought we'd be the smart ones, create an api endpoint that gives the front-end all routes by name and method.
But did it work out?

No, this resulted in the application having to wait on this particular call and forcing a "synchronous" or somewhat "synchronous" request cycle.

Even though it was only once per "page load", this was a real kicker for our application, don't do this, just write the routes out (and thus communicate thoroughly between front- and back-end)

### State management
