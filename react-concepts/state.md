# 🧠 React State — Component's Memory

## 🔹 What is "State" in React?

State is a way for React components to remember information between renders. It stores data that can change over time — such as user input, counters, toggles, or anything dynamic.

**💬 Example ideas:**
- Typing in a text box (React remembers what you typed)
- Clicking "Next" in a gallery (React remembers the current image)
- Toggling "Show more" in a card (React remembers open/close)

## 🔹 Why not use normal variables?

If you use a regular variable (like `let index = 0;`), React won't "see" the changes because:
- Local variables don't persist between renders
- Changing local variables doesn't trigger re-render

React needs to both remember data and update the UI — that's where `useState()` comes in.

## 🔹 Introducing useState()

`useState()` is a React Hook that lets you add state to a functional component.

**✅ Syntax:**
```javascript
import { useState } from 'react';

const [stateVariable, setStateFunction] = useState(initialValue);
```

- `stateVariable` → stores the value (like memory)
- `setStateFunction` → updates the value and re-renders the component
- `initialValue` → the starting value

## 🧩 Example 1: Counter App

```javascript
import { useState } from "react";

export default function Counter() {
  const [count, setCount] = useState(0);

  function handleClick() {
    setCount(count + 1); // update the state
  }

  return (
    <>
      <h1>Count: {count}</h1>
      <button onClick={handleClick}>Increase</button>
    </>
  );
}
```

**🔍 Explanation:**
- `useState(0)` → initializes count with 0
- When you click the button → `setCount(count + 1)` runs
- React remembers new value and re-renders the UI with updated count

## 🔹 Destructuring Syntax

`useState()` returns an array with two elements:

```javascript
const [index, setIndex] = useState(0);
```

is same as:

```javascript
const result = useState(0);
const index = result[0];
const setIndex = result[1];
```

Array destructuring just makes it shorter and cleaner.

## 🧩 Example 2: Image Gallery

```javascript
import { useState } from "react";

export default function Gallery() {
  const pictures = ["img1.jpg", "img2.jpg", "img3.jpg"];
  const [index, setIndex] = useState(0);

  function nextImage() {
    setIndex(index + 1);
  }

  return (
    <>
      <button onClick={nextImage}>Next</button>
      <p>{index + 1} of {pictures.length}</p>
      <img src={pictures[index]} alt="Gallery" width="200" />
    </>
  );
}
```

**⚙️ What happens:**
- When you click Next, `setIndex()` updates index
- React re-renders with the next image
- The component remembers which image is showing

## 🔹 Multiple State Variables

You can use multiple `useState()` calls in one component.

## 🧩 Example 3: Show More / Hide Details

```javascript
import { useState } from "react";

export default function Sculpture() {
  const [index, setIndex] = useState(0);
  const [showMore, setShowMore] = useState(false);

  function handleNext() {
    setIndex(index + 1);
  }

  function toggleDetails() {
    setShowMore(!showMore);
  }

  return (
    <>
      <button onClick={handleNext}>Next</button>
      <button onClick={toggleDetails}>
        {showMore ? "Hide Details" : "Show Details"}
      </button>
      {showMore && <p>This is sculpture number {index + 1}</p>}
    </>
  );
}
```

**📘 Explanation:**
- `index` and `showMore` are independent state variables
- Clicking "Next" only affects index
- Clicking "Show Details" toggles showMore

## 🔹 Rules of Hooks (Important)

- ✅ Always call Hooks at the top of your component (not inside loops or conditions)
- ✅ Hooks must start with `use` (like useState, useEffect, etc.)
- ✅ Must be used inside functional components or custom hooks

🧠 Think of Hooks like "imports" — you always write them at the top level.

## 🔹 State is Private (Local to Each Component)

If you render a component twice, each copy has its own separate state.

## 🧩 Example 4:

```javascript
function Page() {
  return (
    <div>
      <Counter />
      <Counter />
    </div>
  );
}
```

Each `<Counter />` works independently — their states don't mix.

## 🔹 Common Naming Convention

When using useState, it's good practice to name like:

| State Value | Setter Function |
|-------------|----------------|
| count | setCount |
| name | setName |
| index | setIndex |
| showMore | setShowMore |

## 🔹 Recap Notes

| Concept | Description |
|---------|-------------|
| State | Memory for React components |
| useState() | Hook to create and manage state |
| Destructuring | `[value, setValue] = useState(initialValue)` |
| Re-render | Happens when setValue() is called |
| Multiple State | You can have many independent states |
| Private State | Each component has its own state |
| Rules of Hooks | Must call at top, not inside loops or conditions |

## 🧠 Simple Mental Model

When you call:

```javascript
const [x, setX] = useState(0);
```

React does:
- "Okay, I'll remember x for this component."
- "When setX() is called, I'll update x and re-render."

That's how your component gets memory!
