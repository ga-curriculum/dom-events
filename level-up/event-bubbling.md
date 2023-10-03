# DOM Events - Level Up - Event Bubbling

![Hero image](./assets/hero.png)

When an event occurs on an element, that event, whether it is listened to on that element or not, bubbles up through the DOM until it reaches the `document` object.

[tktk better asset from Hunter]

<img src="./assets/bubbling.png" alt="event bubbling" width="100%">

All event listeners registered for the same event, such as `click`, will be invoked along the path to the `document` element - unless one of those listeners calls the event object’s `stopPropagation` method. 

