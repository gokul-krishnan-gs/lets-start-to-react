# 📘Passing Props to a Component

**Definition:** Props (short for properties) allow React components to communicate. A parent component can pass information to its child components through props.

* Props can be any JavaScript value: strings, numbers, objects, arrays, functions.
* Think of props as "knobs" you can adjust—they are like function arguments.

## ⚙️ Props in JSX

* JSX attributes like `className`, `src`, `alt`, `width`, `height` are examples of props:

```jsx
<img src="logo.png" alt="Logo" width={100} height={100} />
```

* You can pass custom props to your components:

```jsx
<Avatar myName="Gokul" />
```

## 🧩 Reading Props in Components

React component functions receive props as a single object.

✅ **Destructuring props:**

```jsx
function Avatar({ person, size }) {
  // use person and size directly
}
```

**Equivalent without destructuring:**

```jsx
function Avatar(props) {
  let person = props.person;
  let size = props.size;
}
```

✅ **Default props using destructuring:**

```jsx
function Avatar({ person, size = 100 }) {
  // size will default to 100 if not provided
}
```

## 🔹 Forwarding Props with Spread Syntax

Instead of manually passing each prop, use the spread operator:

```jsx
function Profile(props) {
  return (
    <div className="card">
      <Avatar {...props} />
    </div>
  );
}
```

## 🧩 Children Prop

* Nested JSX inside a component is automatically passed as a special prop called `children`.

✅ **Example:**

```jsx
<Card>
  <Avatar />
</Card>
```

**Internally, React treats it as:**

```jsx
<Card children={<Avatar />} />
```

* Components can be flexible containers or wrappers:

```jsx
<Card>
  <p>Hello World</p>
</Card>
// children = <p>Hello World</p>
```

## 💡 Key Learnings

* Anything between `<Component> ... </Component>` goes into the children prop.
* Components with children act as wrappers or containers, making them reusable.
* To pass props: Add attributes in JSX like HTML attributes.
* To read props: Use destructuring in the function parameters.
* Default values: `size = 100` for missing or undefined props.
* Forward all props: `<Avatar {...props} />` (use sparingly).
* Nested JSX becomes the component's children prop, allowing flexibility.
