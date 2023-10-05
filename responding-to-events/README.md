# DOM Events - Responding to Events

![Hero image](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to create in-memory elements and add them to the DOM. 

## App overview

Add the following code to the boilerplate: 

```html
  <h3>Comments</h3>
  <ul>
    <li>Reading is what? Fundamental!</li>
  </ul>
  <input>
  <button>Add Comment</button>
```

When we click the **Add Comment** `button`, we want to create a new comment with the text entered in the input. We can add a `click` event listener to pretty much any element - not just buttons. However, buttons are pre-styled to look and act clickable, so you should use them when possible.

## Creating an in-memory element

If we want to add a new comment, we’re going to need to create a new <li> element. Here’s how we can do it using the [`document.createElement`](https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement) method:

```javascript
const btnElement = document.querySelector('button')

btnElement.addEventListener('click', function(event) {
  const liElement = document.createElement('li')
  console.log(liElement)
})
```

> 🧠 At this point, the element is in memory only and is not part of the DOM (yet).

## Setting text on the in-memory element

Okay, we have a new `<li>` element created and assigned to a variable named `li`, but it has no content. We want to get whatever text the user has typed into the `<input>` element.

As an exercise, find the property that holds the content of an `<input>`. Hint: Select the `<input>`, `console.dir` it out and explore! When you find the property - reply to my message in slack!

So, now we can set the `textContent` of the new `<li>`:

```javascript
const btnElement = document.querySelector('button')
// add the following: 
const inputElement = document.querySelector('input')

btnElement.addEventListener('click', function(event) {
  const liElement = document.createElement('li')
  // add the following: 
  liElement.textContent = inputElement.value
})
```

Now the new `<li>` is ready to be added to the DOM!

## Placing the in-memory element into the DOM

There are several ways to add DOM elements to the document using JavaScript. A common way to add new elements to another element is by using the `appendChild` method like this:

```javascript
const btnElement = document.querySelector('button')
const inputElement = document.querySelector('input')
// add the following: 
const ulElement = document.querySelector('ul')  

btnElement.addEventListener('click', function(event) {
  const liElement = document.createElement('li')
  liElement.textContent = inputElement.value
  // add the following: 
  ulElement.appendChild(liElement)
})
```

Note that the new element is appended as the last child. Test it out - nice!

## Clearing text from inputs

The new comment has been added, but if we want to improve the UX, we have one more task - clear out the `<input>`. 

```javascript
const btnElement = document.querySelector('button')
const inputElement = document.querySelector('input')
const ulElement = document.querySelector('ul')  

btnElement.addEventListener('click', function(event) {
  const liElement = document.createElement('li')
  liElement.textContent = inputElement.value
  ulElement.appendChild(liElement)
  // add the following: 
  inputElement.value = ''
})
```

We already have `ulElement` cached, so we can simply reassign the `value` property on it to an empty string. This effectively clears the input by resetting it to `''`. 
