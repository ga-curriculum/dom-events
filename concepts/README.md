# ![DOM Events - Concepts ](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to clearly define the concept and significance of DOM events.

## What are DOM events?

Similar to how we use the term outside of programming, events are things that happen in a system which we can react to. 

DOM events are actions that produce a signal that something has happened on the DOM, and they provide the ability to automatically react to that event. 

As a result, DOM events are the bedrock of web page interactivity. 

## Why do we use DOM events? 

As programmers, we can write code which reacts to events that happen in the DOM - this allows us to implement *event-driven programming*. In event-driven programming, the majority of the code reacts to events triggered by users.

We can make web pages dynamic and respond to user action by manipulating the DOM using JavaScript.

For example, imagine a user is interacting with a small to-do application that looks like this:

![To-Do App One](./assets/todo-app-one.png)

To interact with this app, the user might want to:

- Type the text of the new to-do into an `<input>`
- Click an `<button>` labeled **Add to-do**

![To-Do App Two](./assets/todo-app-two.png)

So what happens next? This is where events come into play. For the app to function as the user expects when the button is clicked, the click would trigger a function that performs the following: 

1. Create a new element.
2. Access the text entered into the `<input>` element.
3. Set the content of the new element to that text.
4. Place the new element on the page so that it's visible to the user.
5. Finally, for a better user experience (UX), reset the input by clearing out the current text.

The above steps require our JavaScript app to interact with the DOM.

![To-Do App Three](./assets/todo-app-three.png)

Lots of events are generated within the browser, for example, all of these actions can trigger an event:

- A user moves or clicks the mouse.
- A user presses a key.
- A form is submitted.
- The page has finished loading or has been resized.
- And so on.

Take a quick peek at the [MDN documentation for events](https://developer.mozilla.org/en-US/docs/Web/Events) to see the sheer number of events we can respond to.

Without DOM events, the code we write cannot interact with browser events.
