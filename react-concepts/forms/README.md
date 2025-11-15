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
