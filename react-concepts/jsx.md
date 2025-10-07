# Writing Markup with JSX
- JSX (JavaScript XML) is a syntax extension for JavaScript that lets you write HTML-like markup directly inside a JavaScript file.
- In React, components combine rendering logic and markup together in one place. Each component is a JavaScript function that can contain markup which React renders to the browser.
- JSX looks like HTML but is stricter and can display dynamic information.
---
### JSX and React are separate things:

- JSX → Syntax extension for JavaScript

- React → JavaScript library

#### They’re often used together, but JSX can be used without React.

---

# 🧩 Rules of JSX

### 1️⃣ Return a Single Root Element

- Every component must return one parent element.
```jsx
  export function App() {
  return (
    <div>
      <h1>Hello React!</h1>
      <p>Welcome to JSX.</p>
    </div>
  );
 }
 ```
- Note : If you don’t want to add an extra "div", use a Fragment (<>...</>) instead
### 2️⃣ Close All Tags
- JSX requires all tags to be properly closed.
```jsx
// Correct
<img src="logo.png" alt="React Logo" />
<li>Orange</li>

// Incorrect
<img src="logo.png">
<li>Orange
```

### 3️⃣ Use camelCase for Most Things

- JSX attributes become JavaScript object keys, so they follow camelCase naming.
```jsx
// HTML
<div class="container"></div>

// JSX
<div className="container"></div>

// HTML
<button onclick="handleClick()"></button>

// JSX
<button onClick={handleClick}></button>
 ```

### 🧠 Note:

- class → className (because class is a reserved keyword in JavaScript)

- Event handlers like onclick → onClick
---

### Key Learning Summary

- React components group markup and logic together.

- JSX is similar to HTML but not identical.

- You can use an HTML-to-JSX converter if needed.

- React’s error messages often help you fix JSX syntax issues.
