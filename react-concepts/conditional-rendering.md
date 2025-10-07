# 📘Conditional Rendering

In React, components often need to display different content depending on certain conditions. JSX allows you to use JavaScript conditional logic like `if` statements, ternary operators, and logical AND (`&&`) to control rendering.

## ⚙️ Conditional Rendering Techniques

### 1️⃣ Using `if` statements

You can use plain `if` statements to decide what to render.

✅ **Example:**

```javascript
function Item({ name, isPacked }) {
  if (isPacked) {
    return <li>{name} ✅</li>;
  } else {
    return <li>{name}</li>;
  }
}
```

### 2️⃣ Returning `null`

If you don't want to render anything, return `null`.

✅ **Example:**

```javascript
function Item({ name, isPacked }) {
  if (isPacked) {
    return null; // nothing rendered
  }
  return <li>{name}</li>;
}
```

### 3️⃣ Ternary Operator (`? :`)

The ternary operator is a concise way to render different JSX based on a condition.

✅ **Example:**

```javascript
<li>
  {isPacked ? `${name} ✅` : name}
</li>
```

### 4️⃣ Logical AND Operator (`&&`)

Use `&&` to render JSX only if a condition is true, otherwise render nothing.

✅ **Example:**

```javascript
<li>
  {name} {isPacked && '✅'}
</li>
```

### 5️⃣ Conditional Variable Assignment

You can assign JSX to a variable and conditionally update it with `if`. This is verbose but flexible.

✅ **Example:**

```javascript
let itemContent = name;
if (isPacked) {
  itemContent = name + " ✅";
}

<li>{itemContent}</li>
```

## 💡 Key Learnings

* React uses JavaScript for branching logic.
* Conditional JSX can be returned directly with `if`.
* You can save JSX to a variable and insert it using `{}`.
* `{cond ? <A /> : <B />}` → renders `<A />` if `cond` is true, otherwise `<B />`.
* `{cond && <A />}` → renders `<A />` if `cond` is true, otherwise renders nothing.
* Use shortcuts (`?` and `&&`) for brevity, or `if` statements for clarity and flexibility.
