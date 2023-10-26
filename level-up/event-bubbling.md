# ![DOM Events - Level Up - Event Bubbling](./assets/hero-event-bubbling.png)

When an event occurs on an element, that event, whether it is listened to on that element or not, bubbles up through the DOM until it reaches the `document` object.

<img src="./assets/bubbling.png" alt="event bubbling" width="100%">

1. `<button>` Event triggered on the innermost element.
2. `<div>` Event bubbles up to the parent element.
3. `<body>` Event continues bubbling up to outer elements.

All event listeners registered for the same event, such as `click`, will be invoked along the path to the `document` element - unless one of those listeners calls the event object’s `stopPropagation` method. 

Let’s see some bubbling in action. Add the following to your `index.html`:

```html
<form>This is the form
  <div>This is the div
    <p>This is the p</p>
  </div>
</form>
```

Next, in `js/app.js`, attach a 'click' listener to each element: 

```javascript
const formElement = document.querySelector('form')
const divElement = document.querySelector('div')
const pElement = document.querySelector('p')

formElement.addEventListener('click', () => {
  console.log('form')
})

divElement.addEventListener('click', () => {
  console.log('div')
})

pElement.addEventListener('click', () => {
  console.log('p')
})
```

To make the elements more visible, add the following CSS to `css/style.css`: 

```css
form {
  background-color: cornflowerblue;
  padding: 15px;
}

div {
  background-color: darkcyan;
  width: 75%;
  padding: 10px;
}

p {
  background-color: darkkhaki;
  width: 50%;
  padding: 10px;
}
```

Then link to the style.css file from your HTML by adding this line to your HTML head:

```html
  <link rel="stylesheet" href="./css/style.css">
```

In your browser, click on each element and examine the console to see event bubbling in action! 

