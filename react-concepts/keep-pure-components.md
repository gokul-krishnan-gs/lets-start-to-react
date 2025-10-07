# 📘 Keeping Components Pure

A pure function is one that behaves predictably and does not affect anything outside its scope. React expects all of your components to be pure so that rendering stays predictable and efficient.

## ⚙️ Characteristics of a Pure Function

### 1️⃣ It minds its own business

- It doesn't change (mutate) any external variables or objects that existed before it was called.
- It only works with its own inputs and returns a result.

### 2️⃣ Same inputs, same output

- Given the same inputs, it always returns the same result.
- There are no random values, API calls, or mutations inside it.

### ✅ Example of a pure function:

```javascript
function double(num) {
  return num * 2;
}
```

### ❌ Example of an impure function:

```javascript
let count = 0;
function addToCount(num) {
  count += num; // changes external variable!
  return count;
}
```

## 🔹 React Components Must Be Pure

React assumes every component is pure. This means:

- The same props should always produce the same JSX.
- A component should not modify external variables, props, or state directly.

### ✅ Pure Component Example:

```javascript
function Greeting({ name }) {
  return <h1>Hello, {name}!</h1>;
}
```

### ❌ Impure Component Example:

```javascript
let message = "Hi";
function Greeting({ name }) {
  message = "Hello"; // ❌ modifies external variable
  return <h1>{message}, {name}!</h1>;
}
```

## 🧠 Why Does React Care About Purity?

Because React can render your components anytime—even multiple times—without warning.

- If components are pure, React can re-render freely without side effects.
- If components are impure, React may display incorrect data or behave unpredictably.

**Rendering is like a school exam** — each component should "solve" its own JSX independently, without copying or changing someone else's answers.

## ⚡ Important Rules for Pure Components

- Do not mutate props, state, or context directly.
- Use `setState` (or its hook equivalent) to update values instead of mutating them.
- Keep side effects (like logging, API calls, timers, etc.) out of the render phase — use event handlers or useEffect instead.
- Always return JSX based solely on current props and state.

## 💡 Recap

A React component must be pure, meaning:

- It doesn't modify anything outside itself.
- It returns the same JSX for the same inputs.
- React may re-render at any time, so your component's output must not depend on external mutations.
- To update the UI, use state setters, not direct mutations.
- Logic belongs in JSX; "changes" belong in event handlers or useEffect.
