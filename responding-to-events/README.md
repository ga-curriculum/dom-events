# ![DOM Events - Responding to Events](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to respond to DOM events by interacting with the DOM. 

## App overview

We're going to build out the rest of this application so that users are able to add a comment to a list by typing their comment in an input and clicking a button to submit their comment.

Add the following code below the existing `<div>` element inside of the `<body>`: 

```html
  <h2>Comments</h2>
  <ul>
    <li>Reading is what? Fundamental!</li>
  </ul>
  <h3>Add a comment</h3>
  <input>
  <button id="comment-button">Add comment</button>
```

When we click the **Add comment** `button`, a new comment should be created using the text entered in the input.

Event listeners can be added to any element in the DOM, even elements that you wouldn't typically expect to be able to interact with as a user - such as an `<h1>` element. However, interactive elements like buttons are pre-styled to look and act clickable. Users everywhere also understand how to use interactive elements such as buttons. Therefore, you should use event listeners on these more interactive elements to guide user behaviors whenever possible.

## Set up the button event listener

As we already established, the event we want to respond to is the user clicking the **Add comment** button, so we're going to need to start by selecting that element in the DOM:

```javascript
const commentButtonElement = document.querySelector('#comment-button');
console.dir(commentButtonElement);
```

Check the console to confirm you selected the correct element. With that work done, we'll attach an event listener to it:

```javascript
commentButtonElement.addEventListener('click', () => {
  console.log("I work!");
});
```

Return to the browser, then click on the button. If everything goes well, then you will see the string "I work!" in the console when you click on the **Add comment** button.

> ♻ **Repeatable pattern**: Use console dir/log to check your work when writing event listeners. Small steps are the path to success. It's easier to troubleshoot small things along the way than to backtrack later through large chunks of code.

## Create an `<li>` element and add it to the page

We will start small in the event listener, working our way up to the intended functionality. Remove the `console.log()` we added to confirm the event listener works and replace it with a line to create a new `<li>` element. To do this, you'll use the `document` object's [`createElement()` method](https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement):

```javascript
commentButtonElement.addEventListener('click', () => {
  const commentElement = document.createElement('li');
});
```

We've called this a `commentElement` because that's what it will be - a single comment that is part of our larger comment list. It's important to remember that just because we created the element doesn't mean it's visible on the page yet - we haven't told it where to go! We should handle that next by selecting the `<ul>` element in the DOM so that we can add the new comment inside of the list:

```javascript
const commentListElement = document.querySelector('ul');
console.dir(commentListElement);
```

Confirm you selected the correct element from the DOM. Feel free to remove the `console.dir()` afterwords. With that work done, we can display the element we've created by appending it to the `commentListElement`.

```javascript
commentButtonElement.addEventListener('click', () => {
  const commentElement = document.createElement('li');
  commentListElement.appendChild(commentElement);
});
```

Every time you click, an empty list item will be added to the comment list. We have not added any text to the element, so none is visible. We'll do that soon. 

Before that, take a moment to notice how our variables have been named and how it helps our code read a little less like code and a little more like English. When the user clicks on the comment button, a new comment is created and is appended to the comment list. All of these things are elements in the DOM, which is immediately apparent by the variable names.

Naming things in code is challenging, but taking the time to think through what variables represent and naming them to match that can be invaluable to help yourself and others understand what exactly is happening in your code, especially when things start getting more complex.

## Setting text on the `commentElement`

Let's add some text to the `commentElement` before we place it in the DOM!

Although our ultimate goal is to set the text currently written in the `<input>` element as the text in the `commentElement`, we'll start by just adding some generic text:

```javascript
commentButtonElement.addEventListener('click', () => {
  const commentElement = document.createElement('li');
  commentElement.textContent = 'Can you hear me?';
  commentListElement.appendChild(commentElement);
});
```

When you click the **Add comment** button, a new list item is created with `"Can you hear me?"` as the text content. But instead of this placeholder text, we want to display whatever text the user has typed into the `<input>` element.

## 🧠 You Do

Select the `<input>` element out of the DOM. Assign it to a variable called `inputElement`.

Don't forget to `console.dir()` the `inputElement` to be sure you're set up for success in future steps! Don't get rid of this for now; we'll use it again momentarily.

## Setting text on the `commentElement` to the value of `inputElement`

It's time for the moment we've all been waiting for. The `<input>` element has a special property called `value` that holds whatever the user has typed inside the `<input>` element. You can inspect the `console.dir()` of the `inputElement` to confirm this!

We can use this property to set the `textContent` of the new `commentElement`:

```javascript
commentButtonElement.addEventListener('click', () => {
  const commentElement = document.createElement('li');
  commentElement.textContent = inputElement.value;
  commentListElement.appendChild(commentElement);
});
```

Write some text in the input and click the button. Success!

## 🧠 You Do

There are two things we can do to improve the user experience of this application:

- If the input has no content, a new `<li>` should not be created in the comment list.
- Remove the text from the `<input>` when the user submits a new comment after their comment has been added to the comment list.

Try to tackle these on your own. You won't need to use any properties we haven't already discussed to accomplish these tasks.

## Knowledge Checks

- True or false: manipulating the DOM in response to an event is just like manipulating the DOM normally
- What is the key of the property on input elements for getting the value of whatever the user has entered?
- Is it better to write code in small chunks, checking along the way, or to write it all at once and test to see if it works once you're done?