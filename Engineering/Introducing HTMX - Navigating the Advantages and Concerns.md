---
tags: engineering, frontend, Htmx, Web
author: Bui Ngoc Nam Anh
github_id: tonible14012002
date: 2023-10-14
---

## What is HTMX
Htmx is a hypermedia-oriented Javscript library for creating dynamic website with minimal Javascript code. Specifically, it extend HTML as a hypermedia and address the issues with legacy HTML applications.
Giving user access to `AJAX`, `Websocket`, `Server Sent Event (SSE)`, `Css Transition`, ...

## Hypermedia-Oriented

`Hypermedia-Oriented` approach involves clients and servers sharing a common understanding of a set of hypermedia elements in data representations. Clients are anable to use elements to trigger requests, navigate states while Servers provide the necessary hypermedia options in the responses. 
In this way, any modification in server side wont break the client application as long as the client can recognise the defined hypermedia options.

## The Core Concept Of HTMX
### Extending HTML with Attributes
HTMX extend the core idea of HTML as a hypertext by adding additional anchor attributes for allowing more possibilities such as:

- Allow any element to send request, not just `form` element.
- Allow any HTTP method, not just `POST` and `GET` can be used.
- Allow more event, not just `click` or `form submit` can trigger requests.
- All other elements now can be the target for update by the request, not alway the entire `window`.
- Allow using `AJAX`, `Websocket`, `SSE` without writing Javascript.

### Let's see a simple example: Active search
```html
<input type="text" name="q"
    hx-get="/trigger_delay"
    hx-trigger="keyup changed delay:500ms"
    hx-target="#search-results"
    placeholder="Search..."
>
<div id="search-results"></div>
```
- `hx-get` attribute holding the api endpoint and HTTP method for sending request after triggered.
- `hx-trigger` define the condition for the event to be triggered. In this case, it will fire a GET request 500 miliseconds after key up event only if the input has been changed.
- `hx-target` attribute target the element that will be inserted into by server response data.

This example showcases how HTMX simplifies the creation of interactive user interfaces. It replaces the need for extensive Js (or ReactJs) code in various common UI techniques, including infinite scrolling, toasts, conditional rendering, loading indicators, error handling, paging, and Websocket and SSE integration. HTMX offers a more streamlined approach to web development. [Explore more examples](https://htmx.org/examples/)

### The role of Javascript in Htmx
While HTMX aims to minimize the need for JavaScript, it still provides a small set of APIs for interaction with HTMX.
For instance, these method are tailored to support htmx-styled AJAX requests:

```javascript
htmx.ajax('GET', '/example', '#myDiv')

htmx.ajax('GET', '/example', {target:'#myDiv', swap:'outerHTML'})

htmx.ajax('GET', '/example', '#myDiv').then(() => {
    // this code will be executed after the 'htmx:afterOnLoad' event,
    // and before the 'htmx:xhr:loadend' event
    console.log('Content inserted successfully!');
});
```
### Server Generate Events 
HTMX also facilitates the triggering of events on the client-side, based on server responses. For instance, a response containing the header `HX-Trigger: contacts-updated` will trigger the `contacts-updated` event at the specified HTML element, and the corresponding event listener will be activated.
```html
<table hx-get="/contacts/table" hx-trigger="contacts-updated from:body"> (2)
    ...
</table>

<script>
    document.body.addEventListener("contacts-updated", function(evt){
        alert("contacts-updated was triggered!");
    })
</script>
```
Or listen only to the status code of server responses
```javascript
document.body.addEventListener('htmx:beforeSwap', function(evt) { (1)
    if(evt.detail.xhr.status === 404){ (2)
    // If the response code is a 404, show the user a dialog
        showNotFoundError();
    }
});
```

[More about Htmx Usage](https://hypermedia.systems/book/contents/)

## The Advantages Of HTMX
### Minimal Of Javacsript - Reduce Development Complexity

HTMX reduces an amount of Javascript code needed to create a dynamic Web applications. This approach leads to a more cleaner and maintainable code base.

### Improved Performance

HTMX is lightweight, leading to faster initial page loads and reduced client-side processing. This results in a better user experience, especially for web applications with frequent UI updates. However, in large-scale applications with frequent UI updates, React is better in performance thank to its virtual DOM.

### Locality of Behaviour (Lob)

HTMX emphasizes the locality of behavior, enabling developers to understand code functionality within a small, self-contained portion. This enhances code transparency and maintainability while streamlining development efforts.

### Product Agility
HTMX do work and improve product agility alot as it has been proved by [a real-world transition from React to htmx](https://htmx.org/essays/a-real-world-react-to-htmx-port/).

## The Concerns With HTMX
### Violate Seperate of Concerns (SOC)

HTMX can blur the lines between data management and presentation, as backends must respond with HTMX content rather than traditional RESTful APIs with Json. As a result, some many different clients such as mobile app, browser, ... might not able to consume the API.

### Trade-Offs in Control
Using HTMX mean shifting in the balance of control between the client and server. The client is kept as *"slim"* as possible and do all the *"heavy lifting"* on the Backend. While, this might be a good thing for Backend Engineers but may require adjustments in development practices.

## When To Use ? 
HTMX is a game-changer in web development, streamlining your codebase and team dynamics. Consider HTMX when your website:
- Need rapid initial rendering and strong SEO.
- Primarily display Text and Images.
- Focus on CRUD operations.
- Employs well-defined UI blocks that update separately.

HTMX may not be the best fit when:
- Your UI has complex interdependencies.
- Offline functionality is essential.
- Frequent UI updates are the norm.
- Your team is not yet HTMX-savvy.

## Conclusion
Htmx offers a fresh approach to web development, enhancing product agility and simplifying the creation of dynamic, interactive web applications. While it comes with some considerations, it opens up new possibilities in web development and offers an appealing alternative to traditional JavaScript frameworks.

## References
- https://www.youtube.com/watch?v=3GObi93tjZI&t=1406s
- https://hypermedia.systems/
- https://www.reddit.com/r/htmx/comments/r13e9i/xtmx_limitations_and_pitfalls/
- https://www.builder.io/blog/htmx-vs-react
- https://htmx.org/examples/