# ![DOM Events - Setup](./assets/hero.png)

Open your Terminal application and navigate to your `~/code/ga/lectures` directory:

```bash
cd ~/code/ga/lectures
```

Make a new directory called `dom-events`, then enter this directory:

```bash
mkdir dom-events
cd dom-events
```

When you're in this directory, create two directories inside it: `js` to hold your JavaScript files for this lecture and `css` to hold your CSS files for this lecture.

```bash
mkdir js css
```

Then, create an `index.html` file in your project directory, an `app.js` in your `js` directory, and a `style.css` file in your `css` directory. These files will hold your work for this lecture:

```bash
touch index.html ./js/app.js ./css/style.css
```

With the directories and files created, open the contents of the directory in VS Code:

```bash
code .
```

Open the `index.html` file and add HTML boilerplate by typing `!` and then hitting the `Tab` key. Then make use of the `app.js` file inside of the `js` directory by adding this line inside the `<head>` tag:

```html
<script defer src="./app.js"></script>
```

Hook up the `style.css` file inside of the `css` directory:

<link rel="stylesheet" href="./css/style.css">

And include a little bit of CSS inside of that `style.css` file:

```css
body {
  font-family: system-ui, sans-serif;
}

div {
  background-color: darkslategrey;
  /* This makes the width of the div the width required by its content! */
  width: fit-content;
  padding: 8px;
}

button {
  margin: 8px;
}

```

Finally, let's add an some starter HTML inside of the `<body>` in `index.html` as follows:

```html
  <h1 id="main-title">DOM Events Blog Post</h1>
  <p>DOM Events are the key to interactivity!</p>
  <div>
    <button id="like-button">Like this post!</button>
    <button id="dislike-button">Dislike this post!</button>
  </div>
```

Open the `index.html` file in your browser.
