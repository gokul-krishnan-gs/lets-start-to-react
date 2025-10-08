# React Events Handling

## 🧩 1. What Are Events in React?

In the browser, events are actions that happen when users interact with the page — for example:

- Clicking a button
- Hovering over text
- Typing in an input field
- Submitting a form
- Pressing a key

React lets you respond to these actions by attaching event handlers to elements.

## ⚙️ 2. Adding Event Handlers

In React, you add an event handler like this:

1. Define a function inside your component.
2. Pass that function to an element using an event prop like `onClick`, `onChange`, etc.

**Example:**

```jsx
function Button() {
  function handleClick() {
    alert('You clicked me!');
  }

  return (
    <button onClick={handleClick}>Click me</button>
  );
}

export default Button;
```

**Explanation:**

- `handleClick` is your event handler function.
- `onClick={handleClick}` tells React to call your function only when the button is clicked.
- You're passing the function, not calling it directly (more on that below).

## ⚠️ 3. Passing vs Calling a Function

This is a very common beginner mistake, so pay close attention:

| ✅ Correct (Passing the function) | ❌ Incorrect (Calling the function) |
|---|---|
| `<button onClick={handleClick}>` | `<button onClick={handleClick()}>` |

**Why?**

- `onClick={handleClick}` → React remembers this function and calls it later when clicked.
- `onClick={handleClick()}` → The function runs immediately during rendering (before you click).

## 💡 4. Reading Props in Event Handlers

Since event handlers are defined inside components, they can access props passed to that component.

**Example:**

```jsx
function AlertButton({ message }) {
  function handleClick() {
    alert(message);
  }

  return (
    <button onClick={handleClick}>Show message</button>
  );
}

export default AlertButton;
```

**Usage:**

```jsx
<AlertButton message="Hello Gokul!" />
<AlertButton message="Welcome to React!" />
```

**Output:**

- When you click the first button → alert shows "Hello Gokul!"
- When you click the second → alert shows "Welcome to React!"

So, props can be used inside event handlers easily.

## 🔁 5. Passing Event Handlers as Props (Parent → Child)

Sometimes, the parent component decides what should happen when something occurs in the child.

**Example:**

```jsx
function Button({ onClick, children }) {
  return (
    <button onClick={onClick}>
      {children}
    </button>
  );
}

function Toolbar() {
  function handlePlay() {
    alert('Playing movie...');
  }

  function handleUpload() {
    alert('Uploading image...');
  }

  return (
    <div>
      <Button onClick={handlePlay}>Play Movie</Button>
      <Button onClick={handleUpload}>Upload Image</Button>
    </div>
  );
}

export default Toolbar;
```

**Explanation:**

- The Button component doesn't know what it will do — it just receives an `onClick` function as a prop.
- The Toolbar (parent) provides those functions.
- This makes the button reusable anywhere!

## ✍️ 6. Naming Event Handler Props (Custom Events)

For built-in HTML elements like `<button>`, React only accepts browser event names like:

- `onClick`
- `onChange`
- `onMouseEnter`
- `onSubmit`

But when you create your own components, you can use any name you like — though it's best practice to:

- Start the prop name with `on`
- Start the function name with `handle`

**Example:**

```jsx
function Button({ onSmash, children }) {
  return <button onClick={onSmash}>{children}</button>;
}

function App() {
  function handleSmash() {
    alert('Boom!');
  }

  return <Button onSmash={handleSmash}>Smash</Button>;
}
```

## 🌊 7. Event Propagation (Bubbling)

Events in React bubble up through the component tree.

That means:

When you click a child element, its parent's event handler will also fire.

**Example:**

```jsx
function Toolbar() {
  function handleToolbarClick() {
    alert('You clicked the toolbar!');
  }

  function handleButtonClick() {
    alert('You clicked the button!');
  }

  return (
    <div onClick={handleToolbarClick}>
      <button onClick={handleButtonClick}>Click Me</button>
    </div>
  );
}
```

**What happens:**

- Clicking the button → "You clicked the button!" → then "You clicked the toolbar!"
- Clicking the toolbar only → "You clicked the toolbar!"

## ✋ 8. Stopping Event Propagation

If you don't want an event to "bubble up" to parent components, you can use:

**`e.stopPropagation()`**

**Example:**

```jsx
function Button({ onClick }) {
  function handleClick(e) {
    e.stopPropagation(); // stops it from going to parent
    onClick();
  }

  return <button onClick={handleClick}>Click me</button>;
}

function Toolbar() {
  function handleToolbarClick() {
    alert('Toolbar clicked');
  }

  function handleButtonClick() {
    alert('Button clicked');
  }

  return (
    <div onClick={handleToolbarClick}>
      <Button onClick={handleButtonClick} />
    </div>
  );
}
```

**Now:**

- Clicking the button → only "Button clicked"
- Clicking the toolbar → only "Toolbar clicked"

The button event does not bubble up to the parent.

## 🧱 9. Preventing Default Browser Behavior

Some events have default browser actions. Example: Submitting a form reloads the page.

You can stop that using:

**`e.preventDefault()`**

**Example:**

```jsx
function Form() {
  function handleSubmit(e) {
    e.preventDefault(); // stop page reload
    alert('Form submitted!');
  }

  return (
    <form onSubmit={handleSubmit}>
      <input placeholder="Enter something" />
      <button type="submit">Submit</button>
    </form>
  );
}
```

Now the page doesn't reload when you submit.

## ⚖️ 10. stopPropagation() vs preventDefault()

| Method | What it does | Example use |
|--------|--------------|-------------|
| `e.stopPropagation()` | Stops the event from bubbling up to parent elements | When you don't want parent `<div>` clicks to trigger |
| `e.preventDefault()` | Stops the browser's default action | Prevent form from reloading, prevent link navigation |

They are different and often used in different situations.

## 🧠 11. Recap

| Concept | Description |
|---------|-------------|
| Add event handlers | Use props like `onClick={handleClick}` |
| Pass, don't call | Don't use `handleClick()` inside JSX |
| Use props in handlers | You can access component props inside your handler |
| Pass handler from parent | Parent can give child an event function |
| Custom event names | Start with `on`, like `onPlay`, `onClose` |
| Event propagation | Events bubble up to parents |
| `stopPropagation()` | Stop bubbling to parents |
| `preventDefault()` | Stop browser default behavior |
