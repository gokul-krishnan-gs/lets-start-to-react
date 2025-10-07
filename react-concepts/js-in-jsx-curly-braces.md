# 📘JavaScript in JSX with Curly Braces

JSX allows you to write HTML-like markup inside JavaScript files. To include JavaScript logic or dynamic values in JSX, you use curly braces `{}`.

## 🧩 Using JavaScript Inside JSX

* **Passing strings:** Use quotes for plain strings:

```jsx
<h1>Hello World</h1>
<input type="text" placeholder="Enter name" />
```

* **Using dynamic JavaScript values:** Replace quotes with `{}` to reference JavaScript variables or expressions:

```jsx
const name = "Gokul";

export function App() {
  return <h1>Hello {name}!</h1>;
}
```

🧠 **Key Point:** Curly braces `{}` open a window into JavaScript right inside your JSX.

## ⚙️ Rules for Using Curly Braces

1. **As text inside a JSX tag:**

```jsx
<p>{2 + 3}</p>  // renders 5
```

2. **As attribute values immediately after `=`:**

```jsx
const color = "blue";
<h1 style={{ color: color }}>Hello</h1>
```

## 🔹 Double Curly Braces `{{ }}`: Passing Objects

* First `{}` → Tells React "this is JavaScript"
* Second `{}` → The actual JavaScript object

✅ **Example: Inline styles**

```jsx
<ul style={{ backgroundColor: 'black', color: 'white' }}>
  <li>Item 1</li>
  <li>Item 2</li>
</ul>
```

🧠 **Note:** Inline style properties in JSX are written in camelCase (`backgroundColor` instead of `background-color`).

## 💡 Key Learnings

* JSX attributes inside quotes → Passed as strings
* Curly braces `{}` → Bring JavaScript logic or variables into JSX
* Curly braces work inside tag content or as attribute values
* `{{ }}` is not special syntax—it's simply a JavaScript object inside JSX curly braces
