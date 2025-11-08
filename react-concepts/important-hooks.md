# React Hooks: `useState`, `useEffect`, and `useRef`

## Quick Reference Table

| Hook | What it does | Does it trigger re-render? | When does it run/update? |
|------|--------------|---------------------------|--------------------------|
| `useState` | Stores reactive data (UI updates when changed) | ✅ Yes | Runs during render, triggers re-render when value changes |
| `useEffect` | Runs side effects (code that happens after render) | ❌ No (but it runs after a render) | Runs after React paints the UI |
| `useRef` | Stores mutable data (that survives re-renders) | ❌ No | Can be read/updated anytime without affecting render |

---

## 🔹 1. `useState` → Causes Re-render

Whenever you call its setter (`setState`), React re-renders the component with the new value.

```javascript
const [count, setCount] = useState(0);

setCount(count + 1); // ✅ triggers re-render
```

This is React's main way to update the UI.

---

## 🔹 2. `useEffect` → Runs after Render

`useEffect` never causes a render on its own. Instead, it runs after a render is completed.

```javascript
useEffect(() => {
  console.log("Runs after the component renders!");
}, []);
```

If the effect depends on a state/prop:

```javascript
useEffect(() => {
  console.log("Runs after 'count' changes!");
}, [count]);
```

…it runs again because `count` changed (which itself triggered a render).

**So** — `useEffect` reacts to renders, but doesn't cause them.

---

## 🔹 3. `useRef` → Doesn't Re-render at All

`useRef` stores a value that doesn't affect rendering. Updating `.current` won't cause React to re-run the component.

```javascript
const ref = useRef(0);
ref.current += 1; // ❌ no re-render
```

It's like a hidden variable inside the component — React doesn't track it for UI updates.

---

## 🔹 Visual Summary

```
useState → causes re-render
      ↓
render happens
      ↓
useEffect runs (after render)
      ↓
useRef stays same (through all renders)
```

---

## ✅ Final Summary

**React re-renders when a state changes. `useEffect` runs after a render, not before. `useRef` can store and change values but never causes a re-render.**
