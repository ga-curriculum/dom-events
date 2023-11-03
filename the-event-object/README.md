# ![DOM Events - The event Object](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will understand the utility of the `event` object and how it can help us reuse some functionality. 

## The dislike button

Let's begin with a quick refactor. So far, the  `handleLike` function only handles likes (as its name accurately implies). In this lesson, we will rewrite it so that this single function handles both likes and dislikes. 

### 🧠 You Do

Accomplish the following:

- Rename the `handleLike` function to `handleReaction`.
  - Don't forget to change the `likeButtonElement`'s event handler to use this renamed function instead of the old `handleLike` function. 
- Select the dislike button out of the DOM. Assign it to a variable called `dislikeButtonElement`.
- Add an event listener to the `dislikeButtonElement`. It should call the newly renamed `handleReaction` function when the `'click'` event is triggered.

After you've completed the above tasks, when you click either the like or dislike button, the like count will be incremented. The text inside of the like button will also be updated. We'll fix this next!

## Like/dislike functionality overview

We're going to change up the `handleReaction` function so that it will work for both the like button and the dislike button. To do this, we must figure out which button the user clicked on. We don't currently have a mechanism to do this, but we do have access to one - the `event` object. 

The `event` object is passed to the callback function as the first argument and holds details about the event that triggered the event listener. Let's make use of it and see what it holds:

```javascript
// make the handleReaction function receive an event and console.dir it.
const handleReaction = (event) => {
  console.dir(event);
  likesCount = likesCount + 1;
  likeButtonElement.textContent = `${likesCount} like(s). Like this post!`;
}
```

Note that `event` will often be abbreviated as `evt` or even `e` (although we won't go that far). Inspecting the `event` object, you'll find many properties, but the most important for us is the `target` property. 

`event.target` represents the element in the DOM that triggered the event. We can confirm this. Change up the console.dir in the `handleReaction` function to log `event.target`, and add another to log the `likeButtonElement`:

```javascript
const handleReaction = (event) => {
  console.dir(event.target);
  console.dir(likeButtonElement);
  likesCount = likesCount + 1;
  likeButtonElement.textContent = `${likesCount} like(s). Like this post!`;
}
```

If you click the like button, you'll see two identical elements printed to the console. That's because they're the same thing!

So we've established that `event.target` is the HTML element that we clicked on, so what we need to figure out next is how to tell the like button and the dislike button apart. Once we've done that, we can carry out logic based on which button the user clicked on. 

Luckily, we've attached something unique to each button that makes it different from every other element on the page - the value of the `id` attribute. We can access the value assigned to this attribute using the `event.target`'s `id` property. Let's confirm that while removing the `console.dir(likeButtonElement)`:

```javascript
const handleReaction = (event) => {
  console.dir(event.target.id);
  likesCount = likesCount + 1;
  likeButtonElement.textContent = `${likesCount} like(s). Like this post!`;
}
```

If you click the like button, `'like-button'` will appear in the console. If you click the dislike button, `'dislike-button'` will appear in the console. This is a reliable way for us to uniquely identify elements and make decisions based on what a user has clicked! With that knowledge in hand, let's start implementing some branching logic based on the element the user has clicked:

```javascript
const handleReaction = (event) => {
  if (event.target.id === 'like-button') {
    likesCount = likesCount + 1;
    likeButtonElement.textContent = `${likesCount} like(s). Like this post!`;
  }
}
```

Now, when you click the like button, the counter increments, and when you click the dislike button, nothing happens. So, let's make something happen!

```javascript
// add a new dislikesCount variable next to the existing likesCount
let dislikesCount = 0; 

// then make use of it in the event handler
const handleReaction = (event) => {
  if (event.target.id === 'like-button') {
    likesCount = likesCount + 1;
    likeButtonElement.textContent = `${likesCount} like(s). Like this post!`;
  } else {
    dislikesCount = dislikesCount + 1;
    dislikeButtonElement.textContent = `${dislikesCount} dislike(s). Dislike this post!`;
  }
};
```

Now you can click on both buttons, and each only updates the data related to that button.
