# ![DOM Events - The event Object](./assets/tktkhero.png)

**Learning objective:** By the end of this lesson, students will understand the utility of the `event` object, and how it can help us reuse some functionality. 

## The dislike button

Let's begin with a quick refactor. So far, the  `handleLike` function only handles likes (as its name accurately implies). In this lesson we're going to rewrite it so that this single function handles both likes and dislikes. 

### 🧠 You Do

Accomplish the following:

- Rename the `handleLike` function to `handleReaction`.
  - Don't forget to change the `likeButtonElement`'s event handler to use this renamed function instead of the old `handleLike` function. 
- Select the dislike button out of the DOM. Assign it to a varible called `dislikeButtonElement`.
- Add an event listener to the `dislikeButtonElement`. It should call the newly renamed `handleReaction` function when the `'click'` event is triggered.

After you've completed the above tasks when you click either the like or dislike button the like count will be incremented. The text inside of the like button will also be updated. We'll fix this next!

## Like/dislike functionality overview



So far when we've used callback functions they've typically been anonymous, or unnamed. Take the function we're using for the like button on our page:

```javascript
likeButtonElement.addEventListener('click', () => {
  console.log('You clicked me!');
});
```

This:

```javascript
() => {
  console.log('You clicked me!');
}
```

is the anonymous function we've provided to this event listener. It has no name. However, here is nothing stopping us from giving it a name and calling that function in the event listener. Check it out, and write this function ***above*** your event listeners:

```javascript
const handleLike = () => {
  console.log('You clicked me!');
}
```

These functions are commonly called event handlers, so the function names we choose will typically reflect this by including the word handle in their name, as in `handleLike` above. Now we can rewrite our event listener to use this function:

```javascript
likeButtonElement.addEventListener('click', handleLike);
```

Notice how we do not invoke this function when we've provided it as a callback! Doing so would immediately invoke the function on page load rather than waiting for the event to trigger it.

## Like functionality

Let's implement some rudamentary like functionality. This will essentially just count the number of times a user has clicked the like button, but it's a good start to managing some data in this application.

We're going to need the ability to count the number of times the user has clicked the like button, which sounds like a great use for a variable:

```javascript
let likesCount = 0;
```

When the user clicks the like button, we should increment the number of likes by one:

```javascript
const handleLike = () => {
  likesCount = likesCount + 1;
  console.log(likesCount);
}
```

Clicking the like button results in the `likes` being incremented by one. Let's display that data on the page, using the like button's `textContent` property:

```javascript
const handleLike = () => {
  likesCount = likesCount + 1;
  likeButtonElement.textContent = `${likesCount} like(s). Like this post!`;
}
```

Very nice!
