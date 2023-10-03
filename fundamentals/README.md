# DOM Events - Fundamentals

![Hero image](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to tktk


## Event listeners

An event listener is a function; specifically, a callback function called when an event fires. Event listeners may also be referred to as event handlers.

Here is the common syntax for registering an event listener for a given event:

```javascript
element.addEventListener(<event-name>, <callback>, <use-capture>)
```
- **`event-name`** is the name of the event (string)
- **`callback`** is the function we want to be executed when the event happens. When called by the JS engine, it will be passed an *event object* as an argument.
- **`use-capture`** is a boolean and is optional. It has to do with *event phases*. We won’t need to worry about it in SEI but read the [**Event Phases section of this article](https://www.smashingmagazine.com/2013/11/an-introduction-to-dom-events/)** to learn more.

> Repeatable Pattern: In this unit, we will always use the addEventListener method to attach event listeners to elements.

There are two additional approaches for registering event listeners which we will discuss briefly: 

1. In the HTML (inline):

```html
<button onclick="submit()">Add Comment</button>
```

Using the HTML approach (onclick="reset()") is typically frowned upon because it requires that the function be in the global scope. In addition, this, like inline styling, somewhat breaks the separation of concerns design principle.

2. Assigning to DOM elements' properties: 

```javascript
btnElement.onclick = submit
```

## The 'click' event



## App 'event' object

Examining the **event object** provided as an argument to our event listener reveals lots of useful information about the event!

Of special interest are:

- Several `...X` and `...Y` properties that provide where the click occurred.
- The `target` property, which holds a reference to the DOM element that triggered (dispatched) the event.
- Note that JS’s `this` keyword within the listener function will be set to the DOM element that `addEventListener` was called on.