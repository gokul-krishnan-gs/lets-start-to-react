# 📘 Rendering Data from Arrays

When building interfaces, you often need to display multiple items (like comments, products, or users) that share the same structure but have different data. React makes this easy using arrays, `map()`, and `filter()`.

---

## ⚙️ Generating a List from an Array

### Steps:

1️⃣ Move your data into an array.  
2️⃣ Use the `map()` method to transform each array element into a JSX element.  
3️⃣ Return the mapped JSX inside a wrapper (like `<ul>`).

### ✅ Example:

```javascript
const people = ['Gokul', 'Arun', 'Rahul'];

export function PeopleList() {
  const listItems = people.map(person => <li key={person}>{person}</li>);
  return <ul>{listItems}</ul>;
}
```

🧠 **Note:** Each list item must have a unique `key` prop to help React identify and update individual items efficiently.

---

## 🔹 Filtering Arrays of Items

You can also use `filter()` to display only specific items from an array.

### ✅ Example:

```javascript
const people = [
  { id: 1, name: 'Gokul', role: 'Developer' },
  { id: 2, name: 'Arun', role: 'Designer' },
  { id: 3, name: 'Rahul', role: 'Developer' }
];

export function DevelopersList() {
  const developers = people.filter(person => person.role === 'Developer');
  const listItems = developers.map(dev => <li key={dev.id}>{dev.name}</li>);
  return <ul>{listItems}</ul>;
}
```

---

## 🧩 Understanding the `key` Prop

* Keys are unique identifiers for React elements inside arrays.
* React uses keys to track items between renders — useful when items are added, removed, or reordered.

### ✅ Example with keys:

```javascript
const items = ['Pen', 'Book', 'Laptop'];

export function ItemList() {
  return (
    <ul>
      {items.map(item => (
        <li key={item}>{item}</li>
      ))}
    </ul>
  );
}
```

### 🔑 Rules for keys:

* Keys must be unique among siblings.
* Keys must not change between renders (avoid generating keys inside render).
* If you need unique keys, you can use `crypto.randomUUID()` when defining the data, not during rendering.

---

## 🧠 Why Does React Need Keys?

Imagine your desktop files had no names—only positions (first file, second file, etc.). If you deleted one file, all positions would shift, causing confusion. File names fix this problem — and keys in React do the same. They help React uniquely identify which item corresponds to which component, even when order changes.

---

## 💡 Recap

* Move data outside your JSX into arrays and objects.
* Use `map()` to create multiple JSX elements dynamically.
* Use `filter()` to show only the items that meet certain conditions.
* Add a unique `key` to each list item to help React track and update them efficiently.
* Keys must be stable, unique, and never change between renders.
