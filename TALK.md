# PoI's

- VueX.
  - What is VueX.
    - VueX is a statemanagement pattern and library.
    - It serves as a centralized store for all the components in an application, with rules ensuring that the state can only be mutated       in a predictable fashion.
    - And, it also doesn't break (so does work) with Vue.js it's reactivity.
- JWT / oAuth.
  - JWT Seems like the logical option, it allows the client's to talk to the server directly, instead of doing handshakes and giving the     the user the idea they are logging into a third party website and granting our client access to that third party website's
    information.
  - Don't even think about oAuth, oAuth was not meant to be used for SPA's (at least not if you're always the "first party client").
- XSRF.
- Using the correct lifecycle hooks.
- Dynamically watching deep properties.
- How to handle states.
- Storing the JWT (/ token), There is three options in storing the Token, these are:
  - Cookie (server side)
    - The http only cookie is a rather secure way of storing the token
      When using a http only cookie + ssl (if you dont use ssl you're a nut xoxo), there is practically no way to have
      It snooped, not by xss (http only), and not by mitm (man in the middle).
  - Cookie (client side)
    - //
  - LocalStorage (client side)
    - //
- Splitting components and views (/ pages)
  - It is a best practice to separate the components and the views, this gives a clear indication on what the router may  
    target, and it keeps your directory clean.
  - Refreshing
    This also prevents "refresh issues", lets say one component is used for 2 routes, this means that when we go from 
    `/a` to `/b` the actual component will not change, thus giving us the issue that our view isn't refreshed,
- Permissions.
- XSRF.
- SEO.
  - SEO works as is, but if your SPA is gonna open as a spinner you'll have a bad time.
- Pre-rendering vs Server side rendering
  - If you only want rendering for SEO you might be best off with prerendering, prerendering generates the static files per request.
  - SSR renders the landing page for the given request (and thus removes the need for a spinner).
- Pre-rendering
  - Pros
    - Good for SEO but also less complex than SSR.
  - Cons 
    - Not useable for views that update alot like leaderboards.
- Server side rendering.
  - Pros
    - Better SEO, If your app starts with a spinner, bots will just move on and index the site with the spinner.
    - Faster time-to-content, no waiting for the javascript to load all the way.
  - Cons
    - Cant host on any server instance (static).
    - Thus must have a node.js server in the backend.
    - More server side load. (only important on high traffic spa's).
    - Increased complexity.
     
- States. (why you should stop using the local storage)
