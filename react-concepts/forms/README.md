# React Form Best Practices

## ✅ 1. Always use controlled components

Each input should get value from state and update state on change.

```jsx
<input
  value={formData.username}
  onChange={handleChange}
/>
```

**Why?**
- ✔ React controls the data
- ✔ Easy validation
- ✔ Easy reset
- ✔ Predictable behaviour

---

## ✅ 2. Use a single `useState` object for multiple fields

Instead of using many states:

❌ **Bad**
```jsx
const [username, setUsername] = useState("");
const [password, setPassword] = useState("");
```

✔ **Good**
```jsx
const [formData, setFormData] = useState({
  username: "",
  password: "",
});
```

Cleaner, scalable, real-world friendly.

---

## ✅ 3. Use one generic `handleChange` function

Avoid writing separate `onChange` for every input.

❌ **Bad**
```jsx
onChange={(e) => setUsername(e.target.value)}
onChange={(e) => setPassword(e.target.value)}
```

✔ **Good**
```jsx
function handleChange(e) {
  const { name, value } = e.target;

  setFormData({
    ...formData,
    [name]: value,
  });
}
```

This allows unlimited inputs.

---

## ✅ 4. Always call `event.preventDefault()` inside onSubmit

Prevents page reload and lets React control the logic.

```jsx
function handleSubmit(e) {
  e.preventDefault();
}
```

---

## ✅ 5. Do not perform logic inside `onChange`

Only update state there. Validation should be done in `onSubmit` or separate function.

❌ **Bad**
```jsx
onChange={(e) => {
  setFormData(e.target.value);
  validatePassword();
}}
```

✔ **Good**
```jsx
onChange={handleChange}
```

Validation inside submit or blur event.

---

## ✅ 6. Show errors inline

This is standard UX.

```jsx
{errors.email && <p className="error">{errors.email}</p>}
```

---

## ✅ 7. Reset the form using the initial state

```jsx
setFormData(initialState);
```

---

## ✅ 8. Use `<form>` tag instead of buttons outside

**Because:**
- ✔ Enter key works
- ✔ Readable
- ✔ Semantic HTML
- ✔ Better accessibility

---

## ✅ 9. Keep form UI + form logic separate

Real-world practice:
- UI component (inputs, labels)
- Logic component (validation, state)

Simple separation improves reusability.

---

# Real-World Form Structure

## 1️⃣ UI Component → "Dumb" Component

- Only shows inputs, labels, buttons
- No logic
- No state
- No validation
- Fully controlled by props

## 2️⃣ Logic Component → "Smart" Component

- Handles state (`useState`)
- Handles validation
- Handles `onChange`
- Handles `onSubmit`
- Sends data + handlers to UI component as props

## 🎯 Why do this?

- ✔ Clean and readable
- ✔ Reusable UI
- ✔ Easy to test
- ✔ Scales for real applications
- ✔ Used in companies and large projects

---

## ✅ Example: Login Mimic (Real-World Structure)

### 📘 LoginFormUI.jsx (UI Only)

```jsx
function LoginFormUI({ formData, onChange, onSubmit }) {
  return (
    <form onSubmit={onSubmit} style={{ display: "flex", flexDirection: "column", gap: "10px" }}>
      <input
        type="text"
        name="username"
        placeholder="Username"
        value={formData.username}
        onChange={onChange}
      />

      <input
        type="password"
        name="password"
        placeholder="Password"
        value={formData.password}
        onChange={onChange}
      />

      <button type="submit">Login</button>
    </form>
  );
}

export default LoginFormUI;
```

📌 **This file has NO state, NO validation — only UI.**

---

### 📙 LoginLogic.jsx (Logic Only)

```jsx
import { useState } from "react";
import LoginFormUI from "./LoginFormUI";

function LoginLogic() {
  const [formData, setFormData] = useState({
    username: "",
    password: "",
  });

  const [message, setMessage] = useState("");

  function handleChange(e) {
    const { name, value } = e.target;

    setFormData({
      ...formData,
      [name]: value,
    });
  }

  function handleSubmit(e) {
    e.preventDefault();

    if (formData.username.trim() && formData.password.trim()) {
      setMessage(`Welcome, ${formData.username}!`);
    } else {
      setMessage("Please fill all fields.");
    }

    setFormData({
      username: "",
      password: "",
    });
  }

  return (
    <div>
      <LoginFormUI
        formData={formData}
        onChange={handleChange}
        onSubmit={handleSubmit}
      />

      {message && <p>{message}</p>}
    </div>
  );
}

export default LoginLogic;
```

📌 **This file controls everything:**
- ✔ state
- ✔ onChange
- ✔ onSubmit
- ✔ validation
- ✔ message

---

### 📕 App.jsx

```jsx
import LoginLogic from "./LoginLogic";

function App() {
  return (
    <div style={{ padding: "20px" }}>
      <h1>Login Mimic (Real-World Structure)</h1>
      <LoginLogic />
    </div>
  );
}

export default App;
```
