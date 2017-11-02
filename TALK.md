# PoI's

- VueX.
  - What is VueX.
  - Why would you use VueX. (to keep internal states).
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
- Server side rendering.
  - Pros
    - Better SEO, If your app starts with a spinner, bots will just move on and index the site with the spinner.
    - Faster time-to-content, no waiting for the javascript to load all the way.
  - Cons
    - Cant host on any server instance (static).
    - Thus must have a node.js server in the backend.
    - More server side load. (only important on high traffic spa's).
     
- States. (why you should stop using the local storage)
