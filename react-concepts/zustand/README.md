# Zustand
---

Zustand is a small, fast, and easy state-management library for React.
It helps you store and manage global state (data shared across multiple components).

### What does Zustand give you?
✔ A global place to keep data
✔ A simple way to update that data
✔ A hook to use that data anywhere in your app
✔ No Provider wrapper (in most cases)
✔ Extremely small (1kb)

---



## Installation

```bash
npm install zustand
```

## Explanation of Zustand Syntax

### 1️⃣ `create()` is used to build the Zustand store

```javascript
create(...)
```

### 2️⃣ `create()` receives a callback function
That callback has one parameter: `set`

```javascript
create((set) => { ... })
```

### 3️⃣ This callback must return an object
This object contains:
* all the state values
* all the actions

```javascript
create((set) => ({
    state1: value,
    state2: value,
    action1: () => {},
    action2: () => {}
}))
```

### 4️⃣ Each action uses the `set()` function
Actions = functions that update the state.

Example:

```javascript
increment: () => set(...)
```

### 5️⃣ `set()` receives a callback
This callback gets the previous state.

```javascript
set((oldState) => { ... })
```

### 6️⃣ That callback must return an object
This returned object contains the updated state values.

```javascript
set((oldState) => ({
    count: oldState.count + 1
}))
```

---

Example

```js
const useStore = create((set) => ({
    count: 0,
    increase: () => set((state) => ({ count: state.count + 1 }))
}));
```

---

```jsx
const count = useStore((state) => state.count);
const increase = useStore((state) => state.increase);

<button onClick={increase}>Add</button>

```

---

## Summary

`create()` builds the store. It receives a callback with `set` as the parameter. This callback returns an object containing all the state and actions. Each action is a function that calls `set()`. `set()` also receives a callback that returns an object with the updated state.
