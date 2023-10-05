# DOM Events - Level Up - Removing Event Listeners

![Hero image](./assets/hero.png)

It’s possible to remove an added event listener; however, only if a named function was used as the callback:

```javascript
btnElement.removeEventListener('click', handleClick)
```

This would remove the ‘click’ event listener (`handleClick`) that was registered on the `btnElement` element like this:

```javascript
btnElement.addEventListener('click', handleClick)
```
