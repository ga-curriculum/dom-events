# DOM Events - Level Up - Other methods to add Event Listeners 

![Hero image](./assets/hero.png)

There are two additional approaches for registering event listeners. The following examples demonstrate a 'click' event: 

1. In the HTML (inline):

```html
<button onclick="submit()">Add Comment</button>
```

Using the HTML approach (`onclick="reset()"`) is typically frowned upon because it requires that the function be in the global scope. In addition, this, like inline styling, somewhat breaks the separation of concerns design principle.

2. Assigning to DOM elements' properties: 

```javascript
btnElement.onclick = submit
```

The DOM element approach (`element.onclick`) is slightly better than the HTML approach because it does not require a globally scoped function.

Ultimately, the `addEventListener` approach is the best practice because it has the flexibility of adding multiple listener functions.