# PoI's

- VueX.
  - What is VueX.
    - VueX is a statemanagement pattern and library.
    - It serves as a centralized store for all the components in an application, with rules ensuring that the state can only be mutated       in a predictable fashion.
    - And, it also doesn't break (so does work) with Vue.js it's reactivity.
  - Why would you use VueX over a global window object.
- JWT / oAuth.
- XSRF.
- Using the correct lifecycle hooks.
- Dynamically watching deep properties.
- How to handle states.

# Hickups

- Storing the JWT.
- Component refreshing.
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
