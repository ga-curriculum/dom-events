# ![DOM Events - Named Callbacks](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to construct an event listener that calls a named function. 

## Named callbacks

So far, when we've used callback functions, they've typically been anonymous or unnamed. Take the function we're using for the like button on our page:

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

is the ***anonymous*** function we've provided to this event listener. It has no name. However, nothing stops us from naming it and calling that function in the event listener. Check it out, and write this function ***above*** your event listeners:

```javascript
const handleLike = () => {
  console.log('You clicked me!');
}
```

Functions passed into `addEventListener` as the second argument are commonly called event handlers. The function names we choose should typically reflect this by including the word handle in their name, as in `handleLike` above. Now, we can rewrite our event listener to use this function:

```javascript
likeButtonElement.addEventListener('click', handleLike);
```

Notice how we do not invoke this function when we've provided it as a callback! Doing so would immediately invoke the function on page load rather than waiting for the event to trigger it. Try the following ***incorrect*** code:

```javascript
likeButtonElement.addEventListener('click', handleLike());
```

Notice how the `console.log` is run as soon as the page is refreshed? Also, when you click the like button, nothing will happen. Always pass just the variable into `addEventListener` without the parentheses. This way, `addEventListener` has a reference to the function that it can itself invoke later.

## Like functionality

Let's implement some rudimentary like functionality. This functionality will count the times a user has clicked the like button. It's a good start to managing some data in this application.

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

## ❓ Review Questions

- Which of the following is correct syntax for passing a named callback to `addEventListener`:
	- `likeButtonElement.addEventListener('click', handleLike());`
	- `likeButtonElement.addEventListener('click', handleLike);`
- True or false: when you assign a function to a variable, it becomes a named function
- True or false: the following code passes `addEventListener` an anonymous function:

  ```javascript
  likeButtonElement.addEventListener('click', () => {
    console.log('You clicked me!');
  });
  ```
