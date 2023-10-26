# ![DOM Events - Fundamentals](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to compose event listeners with appropriate syntax.

## Event listeners

An event listener is a function; specifically, a callback function called when an event fires. Event listeners may also be referred to as event handlers.

Here is the common syntax for registering an event listener for a given event:

```javascript
element.addEventListener(<event-name>, <callback>)
```
- **`event-name`** is the name of the event (string).
- **`callback`** is the function we want to be executed when the event happens. When called by the JS engine, it will be passed an *event object* as an argument.


> ♻️ Repeatable Pattern: In this unit, we will always use the addEventListener method to attach event listeners to elements.

## The 'click' event

An element receives a [click event](https://developer.mozilla.org/en-US/docs/Web/API/Element/click_event) when a mouse's primary mouse button is pressed and released. Other pointing device buttons can also trigger a click event, but we'll primarily be working with mouse clicks.

To listen for a 'click' event, you pass the string 'click' as the addEventListener's `event-name`: 

```javascript
addEventListener('click', (event) => {
  console.log(event)
});
```

## The 'event' object

Examining the **event object** provided as an argument to our event listener reveals lots of useful information about the event!

Of special interest are:

- Several `...X` and `...Y` properties that provide where the click occurred.
- The `target` property, which holds a reference to the DOM element that triggered (dispatched) the event.
- Note that JS’s `this` keyword within the listener function will be set to the DOM element that `addEventListener` was called on.