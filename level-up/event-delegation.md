# ![DOM Events - Level Up - Event Delegation](./assets/hero-event-delegation.png)

Imagine a web app, like a game with many elements that need to respond to a click. There could be tens, hundreds, or more of these elements.

That would be a lot of listeners, wouldn't it - not very efficient at all. Plus, every time a new element is added, the event listener would also have to be registered!

Event bubbling allows us to implement what's known as **event delegation**. Event delegation allows us to register a **single** event listener that can respond to events triggered by any of its **descendants**. Much more efficient!

Let's register a listener (this time for kicks we'll use a named function) on the `<ul>` that can respond to clicks on any of its `<li>`s:

```javascript
ulElement.addEventListener('click', handleClick)

function handleClick(evt) {
  console.log(evt)
}
```

Notably, the event object's `target` property is set to the **actual** element that was clicked!

Not only is event delegation more efficient by its very design, but it's also dynamic - as descendants are added, they too will be listened to! Without event delegation, you would have to register a listener every time a new element, such as when the comment `<li>` is added.

## You Do 💪

**Practice: Write the code to change the color of the text of a clicked comment.**

Hint: DOM elements have a `style` property that's an object with the CSS properties (named using camel-casing), e.g., `liElement.style.fontSize`.