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

## Our Vue.js SPA
Our SPA will always consist of 3 base packages, these are:

1. Vue.js (obviously).
2. VueRouter, this will handle our routes.
3. VueX (optional, but i'd say you always want to use it).

### Vue.js
Vue.js is a FAFFF (fancy as fuck front-end framework) that is mostly used to handle the view layer of your application,
but has proven to be a very powerful tool for SPA development.

### VueRouter
VueRouter is the official routing engine of Vue, it is maintained by the vue core team and well built.
If you're used to Laravel routing, VueRouter is a piece of cake.

### VueX
VueX is the official state management pattern for Vue.js.

And i can hear you think "wtf is state management", let me explain.

State-management is what we typically use to keep things stored on the client, you could use the local storage for this,
but this is not recommended, the local storage allows for states to go stale, let's say you're storing the user in the local storage
and the user does not come back until after 3 minor deployments, the user will now still be "logged in" due to the token being there,
and some other mandatory things, yet the user misses a few fields, which you've added in one of the 3 deployments, 
the application breaks and the user will be sad.

Therefore VueX is way better, the state will be "alive" until the page is closed (or reloaded) and wont become stale,
Just eager load things on the first page load (which will probably only be: your user, and some additional information about the user).

VueX also allows itself to be a sort of event bus, therefore handling every single request to the backend, 
and therefore centralizing how data has to be gotten. (nobody likes to have requests in every component every damn time).

And yes, creating your own object and hooking this to the window also works
```js
window.app = new State();
```
But the thing that you now lack is reactivity, VueX is by default reactive with any other Vue instance and component, and your own `State` object probably isn't.

## How to handle the authentication?
For authentication you have multiple options, oAuth and JWT are the most common, but which one should you use?

Well, that is pretty much up to you, they're both easy to setup (compose require and we good), and pretty good at what they do.

But keep in mind that if you're going to have to open up your api to other applications that oAuth might be the best.

## How to handle the authorization?
### In views
First of all, there is no "real" authorization in an SPA, the back-end implements it and the front-end only hides things for the user.

We'll take the simplest type of authorization as an example: checking if the user is an admin.

On page load you verify if your user is logged in, then in this call you retrieve if the user is an admin, and on basis of that you hide some things for the user, it's that easy.

### In the router
Routing sounds a bit trickier, but it is handled well in the VueRouter, because the VueRouter implements route guards,
almost like Laravel guards, you can do some checks before each route and decide if the user is allowed to visit, its that simple.

## Problems we've encountered

### Reactivity
You're going to bash your head against a wall because you've fucked up the reactivity, no doubt, just know it happens, 
and its party of the Vue.js learning curve, read the [documentation](https://vuejs.org/v2/guide/reactivity.html) thoroughly.

### API Routing
How are you going to tackle routing, we thought we'd be the smart ones, create an api endpoint that gives the front-end all routes by name and method.
But did it work out?

No, this resulted in the application having to wait on this particular call and forcing a "synchronous" or somewhat "synchronous" request cycle.

Even though it was only once per "page load", this was a real kicker for our application, don't do this, just write the routes out (and thus communicate thoroughly between front- and back-end)

### Hard linking components (instead of a dedicated views folder)
We somehow managed to let our router target components from our `components` folder, this seemed to make things a bit intrusive,
Therefore we decided to either keep a `views` or `pages` (whatever you like) folder that is dedicated for the actual views.

This also prevents "refresh issues", lets say one component is used for 2 routes, 
this means that when we go from `/a` to `/b` the actual component will not change, 
thus giving us the issue that our view isn't refreshed (as the lifecycle hooks are not triggered as expected).
